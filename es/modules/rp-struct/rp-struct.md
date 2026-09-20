# rp-struct

## Propósito

El constructor de estructuras compartido: convierte el contenido suelto en representaciones tipadas, con forma de esquema,
en las que puede confiar cada consumidor. Un único punto de modelado entre el contenido sin procesar
y la representación del canal.

## Modelo mental

Contenido sin procesar de entrada → el modelado de estructuras aplica esquemas y formas → bloques tipados
de salida. Los canales (`sf-*`, markdown, plantillas de notificación) representan bloques
sin volver a analizar la fuente.

## Valor del ecosistema

Un estante JSON sin tipos:

- Documentos JSON tras una única API de archivos.
- Cualquier productor almacena blobs estructurados sin su propia gestión de archivos.

## No objetivos

- Sin taxonomía ni etiquetado.
- Sin representación de markdown.
## Límite de responsabilidad

Responsable del modelado de estructuras y la conformación a nivel de esquema; no responsable de la representación final
específica del canal.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `content`

## Fuente

`modules/repositories/content/rp-struct`