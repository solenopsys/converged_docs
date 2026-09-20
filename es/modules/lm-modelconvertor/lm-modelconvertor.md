# lm-modelconvertor

## Propósito

El puente compartido de formatos de modelo: convierte modelos de producción entre representaciones internas y externas (p. ej., a vistas previas GLB) para que ningún flujo de trabajo enlace directamente una biblioteca conversora nativa.

## Modelo mental

El flujo de trabajo prepara los bytes del modelo → el conversor transforma el formato → devuelve bytes de vista previa/convertidos como refs de caché para `rp-files.persist`. Transformación pura: sin almacenamiento, sin estimaciones, sin decisiones de negocio.

## Valor del ecosistema

Un punto de conversión para modelos de producción:

- Un archivo preparado de entrada, salidas convertidas como refs de caché de salida — misma forma para cualquier llamador.
- Nuevos formatos y versiones del conversor llegan una vez y actualizan cada ruta de análisis.
- Mantiene dependencias nativas pesadas fuera de flujos de trabajo y repositorios.

## No objetivos

- No es almacenamiento de archivos ni orquestación de ingesta.
- No es renderizado de vistas previas ni estimaciones de segmentación.

## Límite de responsabilidad

Posee rutinas de conversión/transformación; no posee entrenamiento de modelos ascendente, servicio descendente ni persistencia.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a solución

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/convertors/lm-modelconvertor`