# rp-files

## Propósito

Proporciona API de metadatos de archivos y flujos de trabajo para la gestión de archivos.

## Límite de responsabilidad

Es responsable de los registros de archivos y las operaciones a nivel de archivo; no es responsable de los detalles de implementación del almacenamiento de objetos.

## Dependencias directas del módulo

- `rp-store` — el almacén de bloques direccionado por contenido donde viven los bytes de cada archivo.
  rp-files conserva los nombres, las colecciones y la lista de fragmentos; no almacena datos.

## Pertenencia a la solución

- `requests`

## Fuente

`modules/repositories/data/rp-files`
