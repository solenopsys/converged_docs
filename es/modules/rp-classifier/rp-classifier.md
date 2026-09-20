# rp-classifier

## Propósito

El servicio compartido de etiquetado: cualquier ingesta dirige aquí el contenido sin procesar y obtiene
a cambio categorías, etiquetas o intenciones. Una sola lógica de clasificación en lugar de
cadenas de if por dominio.

## Modelo mental

El productor envía elementos sin procesar (archivos, textos, solicitudes) → el clasificador asigna
etiquetas → el llamador enruta por etiqueta (modelo de producción frente a dibujo, urgente
frente a ruido). Las etiquetas son recomendaciones; la decisión de negocio permanece en el llamador.

## Valor del ecosistema

Un único estante de taxonomía:

- Nodos de árbol y asignaciones de claves tras una sola API.
- Cualquier ingesta resuelve etiquetas desde el mismo árbol en lugar de sus propios diccionarios.

## No objetivos

- Sin bytes de archivo ni conversión.
- Sin almacenamiento de documentos JSON.
## Límite de responsabilidad

Posee la lógica de clasificación y la asignación de etiquetas; no posee las canalizaciones de ingesta de contenido de origen ni el enrutamiento de negocio posterior.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/repositories/content/rp-classifier`