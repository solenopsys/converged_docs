# rp-counters

## Propósito

Configuración por inquilino de contadores de analítica externos: almacena ID de seguimiento (GA4, GTM, Yandex Metrika, Meta Pixel) o un fragmento personalizado del head, para que SSR pueda inyectar los scripts correctos por inquilino.

## Modelo mental

El operador guarda un contador (tipo, ID de seguimiento o fragmento, indicador de habilitación) → el almacén conserva la configuración. SSR lee los contadores habilitados para el inquilino actual y representa las etiquetas correspondientes. Aquí no se recopilan cifras, solo la configuración de los contadores.

## Valor para el ecosistema

Un único lugar para la integración de analítica:

- Los contadores externos (GA4, GTM, Metrika, Pixel) y los fragmentos personalizados se configuran por inquilino en lugar de estar codificados por página de destino.

## No objetivos

- No es almacenamiento de eventos sin procesar.
- No son diarios de muestras numéricas.
- No son registros de uso ni facturación.
## Límite de responsabilidad

Gestiona las configuraciones de contadores (tipo, ID de seguimiento o fragmento, indicador de habilitación); no recopila métricas, no agrega uso ni realiza facturación.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `analitycs`

## Fuente

`modules/repositories/analytics/rp-counters`