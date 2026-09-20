# rp-telemetry

## Propósito

El feed técnico compartido de salud: los servicios informan «cómo están» (latencia, errores, señales de recursos) aquí en lugar de que cada herramienta de operaciones los consulte individualmente. Ingesta normalizada, una única superficie de consulta para la salud.

## Modelo mental

El servicio envía eventos de salud (origen, señal, tiempo, carga útil) → la telemetría los normaliza en una forma uniforme. Los consumidores de operaciones (paneles, flujos de incidentes) leen la salud por servicio a lo largo del tiempo. El significado de negocio lo asigna el lector, no el almacén.

## Valor del ecosistema

Un diario de muestras numéricas:

- Cualquier productor escribe filas (dispositivo, parámetro, valor, unidad, tiempo) en almacenes hot/cold.
- Una línea de tiempo para números de cualquier origen — sensores de equipos o cualquier otra cosa.

## No objetivos

- No es almacenamiento de registros de texto.
- No son registros de uso.
- No es política de alertas ni resolución de incidentes.
## Límite de responsabilidad

Responsable de la ingesta y normalización de eventos de telemetría; no responsable de las definiciones de analítica de producto, alertas o remediación.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `analitycs`

## Fuente

`modules/repositories/analytics/rp-telemetry`