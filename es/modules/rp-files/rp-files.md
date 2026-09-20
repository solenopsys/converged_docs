# rp-files

## Propósito

La abstracción única de archivos del ecosistema: cualquier módulo que necesite
«archivos» viene aquí en lugar de crear su propia tabla de nombres y rutas.
Conserva metadatos, colecciones y listas de fragmentos; los bytes en sí residen en
el almacenamiento de bloques, accesible a través de un cliente de servicio de almacenamiento.

## Modelo mental

Archivo = registro (nombre, extensión, colección, propietario) + lista ordenada de referencias de fragmentos
 en el almacenamiento de bloques. La clasificación (`detectType`), la materialización
y la persistencia operan sobre metadatos — los bytes solo se cargan cuando realmente se necesitan
(preparación de modelos, servicio de descargas).

## Valor en el ecosistema

El punto de entrada de la ingesta de archivos:

- Archivos, fragmentos, colecciones y metadatos tras una sola API; los bytes de fragmentos se delegan al almacenamiento de bloques.
- Cualquier dominio vincula un id de archivo opaco a su entidad en lugar de copiar bytes.

## No objetivos

- No es almacenamiento de bloques puro — los bytes de fragmentos residen en el almacén de bloques.
- No es desempaquetado de archivos ni conversión de modelos.
## Límite de responsabilidad

Posee registros de archivos, colecciones y ciclo de vida de listas de fragmentos; no posee
detalles de implementación del almacenamiento de objetos ni transformaciones de bytes.

## Dependencias directas de módulos

- Ninguna — los bytes de fragmentos pasan por un cliente de servicio de almacenamiento, que es una llamada
  de transporte como la que realiza cualquier consumidor externo, no un enlace de módulo a módulo.
  rp-files conserva nombres, colecciones y la lista de fragmentos; no almacena datos.

## Pertenencia a la solución

- `requests`

## Fuente

`modules/repositories/data/rp-files`