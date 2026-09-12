# Acceso a objetos

## Dos capas, no una

El acceso a métodos y el acceso a objetos responden preguntas diferentes, y ninguno sustituye
al otro.

**Acceso a métodos** — ¿puede este actor llamar a `rp/community/listTopics`? Se encuentra
en el árbol de permisos, lo emite `rp-access` y lo aplica el guard de nrpc antes de que se
ejecute el controlador. Sin él, cualquiera puede llamar a `deleteTopic`.

**Acceso a objetos** — ¿qué temas devuelve `listTopics`? Ese es el tema de este
documento. Sin él, un actor autorizado para llamar a `listTopics` recibe todos los temas
del almacén.

El acceso a objetos reutiliza el transporte de acceso a métodos en lugar de añadir un segundo
sistema: una etiqueta es una concesión ordinaria bajo el tipo `tg`, transportada por el mismo
JWT y emitida por las mismas llamadas.

## El mecanismo

Dos cosas, ambas locales al servicio que posee los datos.

Una tabla por almacén, que sirve para todos los tipos de objetos que contiene:

```sql
CREATE TABLE access_tags (
  objectId TEXT NOT NULL,
  tag      TEXT NOT NULL,
  PRIMARY KEY (tag, objectId)
);
CREATE INDEX access_tags_object ON access_tags (objectId);
```

Y las etiquetas por las que se compara un actor. No hay una columna para el tipo de objeto:
la unión con la tabla propietaria realiza ese filtrado, ya que un id perteneciente a otro tipo
no se encuentra allí.

## Etiquetas

**Etiquetas de grupo** — `team-support`, `moderator`. Se almacenan por usuario en el almacén
KV `access` de `rp-access`, dentro del árbol de permisos existente como
`tg/<tag>/*(mode)`, y se incluyen en el JWT. Se conceden con `addTagToUser`.

**La etiqueta personal** — `u-<userId>`. Nunca se almacena ni se emite: se deriva del sujeto
del token, que todo token verificado ya contiene. Un objeto abierto a una persona se etiqueta
con la etiqueta de esa persona, por lo que una concesión individual cuesta una fila y nada en
el token.

**Etiquetas conocidas** — `public` (cualquiera, incluidos los llamadores anónimos) y
`authenticated` (cualquier actor verificado). La visibilidad consiste en con cuál de estas se
escribe un objeto, no en una columna, lo que mantiene cada selección como una búsqueda por
etiqueta.

Así, la propiedad, el uso compartido individual, el acceso de grupo y la visibilidad pública
son un solo mecanismo con cuatro tipos de etiqueta, no cuatro mecanismos.

## Selección

Una selección debe comenzar desde la tabla de etiquetas y unirla con los objetos. `visibleFrom`
en `back-core/access` hace esto:

```ts
import { listVisible, visibleFrom } from "back-core";

const page = await listVisible<Topic>(this.store.db, "topics", { limit: 50 });

const custom = await visibleFrom(this.store.db, "topics")
  .selectAll("obj")
  .where("obj.status", "=", "open")
  .orderBy("obj.id")
  .limit(50)
  .execute();
```

La dirección no es una elección de estilo. Escrita de forma plana —
`access_tags JOIN topics ... WHERE tag IN (...) ORDER BY topics.id` — SQLite
prefiere recorrer la tabla de objetos en orden de clave primaria para satisfacer la ordenación.
En una tabla de un millón de filas con diez visibles, eso midió **363 ms** para una página de
cincuenta. A través de la subconsulta que construye `visibleFrom`, la misma página midió
**0.28 ms**. Ambas devuelven resultados idénticos, por lo que la forma tiene una prueba que
comprueba el plan de consulta en lugar de la salida.

Nunca filtres después de la consulta, fuera de la base de datos, ni pongas etiquetas en una
columna de lista que se compruebe por fila: ambas opciones leen la tabla completa.

`listVisible` devuelve `totalCount` calculado con el mismo estrechamiento que la página.
Contar sin él revela cuántos objetos se están ocultando.

## Concesión

```ts
const access = new AccessTags(this.store);

await access.tagNew(id, { owner: actorId, visibility: "private" });
await access.grantToUser(id, otherUserId);   // effective immediately
await access.revokeFromUser(id, otherUserId);
await access.dropObject(id);                 // on delete; a leftover row would
                                             // later match a reused id
await access.requireRead(id);                // throws AccessDeniedError
```

La pertenencia a grupos pasa por `rp-access`, porque vive en el token:

```ts
await access.addTagToUser(userId, "team-support");
await access.removeTagFromUser(userId, "team-support");
await access.getTagsOfUser(userId);
```

## Requisitos

**Los ids deben ser únicos entre las tablas cubiertas por etiquetas.** Una secuencia
compartida, un UUID o un prefijo de tipo — lo que ya use el almacén. Las entidades no
cubiertas por etiquetas no se ven afectadas; esto no supone un cambio a UUID para toda la
plataforma.

**Los ids deben ser generados por el servidor.** Sin una columna para el tipo de objeto, un id
que el llamador pueda elegir es un objeto al que el llamador puede acceder. Actualmente existen
ids proporcionados por clientes en `rp-sales`, `rp-classifier` y `rp-chats`, y deben cerrarse
antes de que esos repositorios adopten etiquetas.

**Los ids monotónicos son una ventaja, no un requisito.** Una secuencia compartida o UUIDv7
proporciona el orden de creación directamente desde el índice de etiquetas. UUIDv4 no lo hace,
y esa es la única consecuencia: usa un `orderBy` explícito en su lugar.

**El orden de bytes debe coincidir con el significado.** Una secuencia numérica almacenada en
una columna de texto necesita ceros de relleno, o `"10"` se ordena antes que `"9"`.

**No debe haber `:` ni `;` en ids o etiquetas.** Son `KEY_SEPARATOR` y
`RANGE_END_SUFFIX` en `back-core`; un separador dentro de una clave la hace ambigua
en los almacenes KV. `addTagToUser` rechaza esas etiquetas.

**`NRPC_ACCESS_MODE` debe ser `required`.** Con el guard desactivado, el usuario del contexto
recae en el sobre, que escribe el llamador; la etiqueta personal se derivaría entonces de un id
proporcionado por el cliente. Es `required` en `confs/dev` y `confs/prod`; el valor
predeterminado del código es `off` para ejecuciones locales y pruebas.

## Almacenes no SQL

KV: la misma estructura que las claves del mismo almacén — `tag:<tag>:<objectId>` hacia
adelante, `obj:<objectId>:<tag>` en sentido inverso. Leer una lista es un escaneo de prefijo
por etiqueta, fusionado y sin duplicados. Una paginación fiable necesita un cursor en
`kvList`, que actualmente devuelve un rango completo; hasta entonces, las listas KV están
limitadas por lo que cabe en memoria.

Archivos y JSON (`JsonStore` extiende `FileStore`): no tienen un índice de etiquetas propio. El
nombre del archivo es el id del objeto, y el acceso a él es el acceso al registro que lo
referencia, que vive en un almacén SQL o KV del mismo servicio.

Grafo: la etiqueta es un nodo, la concesión es una arista y el recorrido comienza desde la
etiqueta.

## Límites aceptados

**Eliminar una etiqueta de grupo espera a que se vuelva a emitir el token** —
`DEFAULT_TTL_SECONDS` es de 90 días. Las concesiones y revocaciones individuales son
inmediatas, porque la tabla se lee en cada solicitud. El acceso que deba cambiar al instante
usa la etiqueta personal, no un grupo.

El **`totalCount` exacto** necesita la unión; con varias etiquetas superpuestas, el recuento se
hace sobre ids distintos, lo que cuesta más a medida que crece el conjunto visible.

**Ordenar por cualquier campo distinto del id** es barato mientras pocos objetos coincidan con
una etiqueta. Si alguna etiqueta llega a cubrir cientos de miles de objetos, ese orden debe
desnormalizarse en la tabla de etiquetas o eliminarse.
