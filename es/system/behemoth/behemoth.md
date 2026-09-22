# Almacenamiento de Behemoth

Behemoth es la base nativa de almacenamiento de Converged. Proporciona varios
modelos de datos mediante un único runtime compacto, al tiempo que conserva un
límite físico de almacenamiento separado para cada microservicio.

## Almacenamiento para servicios modulares

Cada servicio de dominio es propietario de sus datos. No comparte tablas ni
índices con servicios no relacionados, y no necesita operar una pila de base de
datos separada. Behemoth sirve las raíces aisladas desde un proceso nativo común
y enruta cada solicitud al almacén correcto.

```text
servicio de pedidos   -> volumen de pedidos   -> SQL y archivos
servicio de llamadas  -> volumen de llamadas  -> clave-valor y fragmentos de audio
servicio de búsqueda  -> volumen de búsqueda  -> índice vectorial
```

La separación es física, no una convención de nombres. Si una raíz de servicio
no está montada y declarada, Behemoth se niega a crear su almacén. Por lo tanto,
un error de despliegue se hace visible de inmediato en lugar de escribir datos
en un sistema de archivos temporal del contenedor.

## Múltiples modelos de datos

Las distintas cargas de trabajo necesitan estructuras diferentes. Behemoth
combina almacenamiento relacional, de clave-valor, columnar, vectorial, de
p grafos y de archivos detrás del mismo límite de runtime. Un servicio elige el
almacén que se adapta a sus datos sin añadir un nuevo producto de base de datos
externo a la plataforma.

Los motores siguen estando especializados internamente. La capa unificada es
responsable del ciclo de vida, el aislamiento, el transporte y los metadatos,
no de fingir que todos los modelos de datos se comportan de la misma manera.

## Ubicación y escalado

La ubicación del almacenamiento es independiente del código de la aplicación.
Una instalación de edge puede utilizar un único proceso de Behemoth. Las
implementaciones más grandes pueden dividir los ámbitos entre varias instancias,
mientras que un perfil en la nube puede proporcionar a cada tenant su propia
instancia de almacenamiento.

Cada microservicio mantiene su propio volumen en cada perfil. Mover un ámbito o
un servicio a otra instancia de Behemoth cambia la configuración del despliegue,
mientras que los clientes siguen utilizando la misma identidad lógica de
almacenamiento.

## Límites de fallo y recuperación

Los almacenes pequeños propiedad de cada servicio reducen el impacto de la
corrupción, las migraciones y las operaciones de copia de seguridad. Un problema
en un almacén no requiere restaurar una base de datos compartida para toda la
plataforma. Los volcados y la recuperación pueden gestionarse para el límite
del servicio afectado, y los servicios no relacionados pueden seguir operando.

## Lugar en el sistema

Las solicitudes de almacenamiento llegan a Behemoth a través de Fujin, como las
solicitudes a cualquier otro par de runtime. Ptah proporciona el diseño de
volúmenes y la configuración de montaje. Behemoth ejecuta las operaciones de
almacenamiento, pero no coordina los flujos de trabajo empresariales, selecciona
tenants ni define qué servicios contiene una solución.
