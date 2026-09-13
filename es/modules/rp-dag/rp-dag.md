# rp-dag

## Propósito

Posee los activadores del flujo de trabajo y el registro de ejecución. No ejecuta nada.

## Límite de responsabilidad

Aquí pertenecen dos cosas y nada más:

- **Activadores** — «cuando aparezca este tema del bus, ejecuta ese flujo de trabajo». Configuración del sistema: decenas de filas que mantiene un operador, conservadas en su totalidad en la memoria del tiempo de ejecución en lugar de consultarse.
- **El registro de ejecución** — un árbol de lo que hizo una ejecución. El tiempo de ejecución lo escribe mientras se ejecuta el script: un nodo se abre antes de que se ejecute su cuerpo y se cierra cuando termina, de modo que una ejecución en curso muestra el nodo en el que se encuentra.

El catálogo de flujos de trabajo no es propiedad de este servicio. Ptah coloca los descriptores de la Solution activa en el entorno de este servicio (`WORKFLOWS`, `WORKFLOW_DIGESTS`, `MODULE_PROXY`) y `listAvailableWorkflows` los vuelve a publicar para el tiempo de ejecución y la interfaz de usuario. Los bytes de origen permanecen detrás de Ptah-proxy.

## El registro lo escribe el tiempo de ejecución, no este servicio

Nada de aquí escribe una entrada de registro. El tiempo de ejecución le da formato, lo coloca en Valkey bajo una clave que compone por sí mismo y, posteriormente, entrega las claves —nunca las entradas—. `commitLog` convierte cada clave en una ubicación de almacenamiento e indica al almacenamiento que recoja la entrada; el almacenamiento lee directamente de la caché, por lo que una entrada cruza el transporte una sola vez, como bytes que nadie vuelve a codificar.

```text
workflow thread ─► queue ─► log writer ─► valkey
                                 │
                                 └─ commitLog([keys]) ─► rp-dag ─► storage reads valkey
                                                                        │
                                 ◄──── committed ────────────────────────┘
                                 └─ delete the committed keys
```

Eso es lo que mantiene el registro fuera de la ruta crítica del flujo de trabajo: un nodo le cuesta al tiempo de ejecución un añadido a la cola y nada más. También significa que el registro es, por construcción, de mejor esfuerzo —una entrada puede descartarse bajo presión y un lote puede confirmarse dos veces después de un fallo. Las claves se derivan de la ejecución y de la secuencia del nodo, por lo que la segunda confirmación es una reescritura y no un duplicado.

Las claves proceden del tiempo de ejecución por esa razón: un número asignado por este servicio costaría un viaje de ida y vuelta por nodo y no sería reproducible después de un reinicio.

- `dag:log:<executionId>:exec` — la ejecución
- `dag:log:<executionId>:n:<seq>` — uno de sus nodos, con relleno de ceros hasta seis dígitos

`commitLog` deriva la ubicación de almacenamiento a partir de la clave y rechaza cualquier cosa fuera del prefijo `dag:log:`, por lo que una clave constituye toda la autoridad que transporta la llamada.

## El registro es un árbol

```text
exec:<id>              la ejecución
node:<id>:<seq>        sus nodos, en el orden en que se abrieron
```

Un nodo que delegó mediante `rt.sub` contiene el id de la ejecución secundaria, y la secundaria es una ejecución ordinaria con sus propios nodos. `executionTree` recorre ese vínculo en profundidad y devuelve el resultado plano, con cada fila etiquetada con su `depth` —de modo que un cliente representa el árbol aplicando sangría y nada más—. No se necesita un índice de padres: el vínculo es el nodo que lo creó.

Las secuencias llevan relleno de ceros en la clave, porque el almacén KV devuelve un rango de prefijo en orden lexicográfico y ese orden debe ser el orden en que se ejecutaron los nodos. El tiempo de ejecución aplica el mismo ancho cuando compone la clave de caché; ambos anchos forman un único contrato.

La retención es un límite de ejecuciones (`5000` de forma predeterminada), aplicado en cada centésima apertura. El registro sirve para diagnósticos, no es un archivo histórico.

## Los cambios de activadores llegan al tiempo de ejecución mediante el bus

Crear, cambiar o eliminar un activador publica `dag.triggers.changed`. El tiempo de ejecución se suscribe a ese tema junto con el propio de los activadores, por lo que una edición está activa para el siguiente evento en lugar de tener que esperar a que transcurra un intervalo de sondeo. La publicación es de mejor esfuerzo —un bus caído no debe hacer fallar la edición de un operador— y la actualización periódica del tiempo de ejecución sigue siendo el mecanismo de respaldo.

## Dependencias directas del módulo

- g-bus — para anunciar un cambio de activador

## Pertenencia a una Solution

- No incluido en una solución predefinida

## Origen

`modules/repositories/automation/rp-dag`
