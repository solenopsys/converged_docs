# rp-markdown

## Propósito

La pipeline Markdown compartida: análisis, transformación y renderizado para
cada módulo que gestiona contenido de texto. Un solo comportamiento del analizador en lugar
de variantes por superficie.

## Modelo mental

Fuente Markdown de entrada → analizar/transformar → salida renderizada (HTML, bloques).
Los autores de contenido escriben una vez; docs, chats, landings y notificaciones renderizan
la misma fuente de forma coherente.

## Valor para el ecosistema

Columna vertebral única de texto:

- Archivos Markdown más conversión JSON tras una sola API.
- Cualquier productor almacena el texto humano de la misma manera en lugar de su propio manejo de archivos.

## No objetivos

- No es almacenamiento de bloques tipados.
- No es renderizado HTML.
## Límite de responsabilidad

Posee el comportamiento de conversión/análisis de Markdown; no posee transcodificación
de medios enriquecidos ni composición de páginas.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `content`

## Fuente

`modules/repositories/content/rp-markdown`