# lm-compressors

## Propósito

El caballo de batalla de bytes compartido del pipeline de archivos: ensamblaje, descompresión,
análisis de ZIP, fragmentación de salida y staging. Sin estado — sin clientes `files` ni
`store` en su interior; devuelve bytes y referencias de caché, la persistencia
es tarea del flujo de trabajo.

## Modelo mental

El flujo de trabajo entrega refs de chunks + operación (desempaquetar, ensamblar, fragmentar) → lambda
realiza trabajo puro de bytes → devuelve bytes en staging/refs de caché. Nunca decide
lo que significa un archivo y nunca almacena nada.

## Valor del ecosistema

Un único lugar donde se tocan los bytes de archivo:

- Chunks comprimidos dentro, entradas en staging fuera — una única forma de desempaquetado para cualquier llamador.
- Cualquier futuro formato de archivo o compresión llega aquí una vez y actualiza todas las ingestas a la vez.

## No objetivos

- No es almacenamiento ni clasificación de archivos.
- No es conversión de modelos ni renderizado de vistas previas.
## Límite de responsabilidad

Posee el ensamblaje de bytes, la descompresión, el análisis de archivos, la fragmentación de salida y
el staging; no posee registros de archivos ni persistencia.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `requests`

## Fuente

`modules/lambdas/data/lm-compressors`