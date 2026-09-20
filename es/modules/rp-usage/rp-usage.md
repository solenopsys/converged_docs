# rp-usage

## Propósito

El medidor de consumo compartido: cualquier funcionalidad informa aquí "cuánto se utilizó"
en lugar de rastrear cuotas localmente. Agregado por consumidor y período —
la fuente de la que leen la facturación y los límites.

## Modelo mental

La funcionalidad registra el consumo (quién, qué, cuánto, período) → uso
lo agrega por cuenta/período. La facturación posterior convierte los agregados en dinero;
las comprobaciones de límites leen los totales actuales. La medición vive aquí, el precio vive
aguas abajo.

## Valor del ecosistema

Un registro de eventos de uso:

- Cualquier funcionalidad registra filas (función, usuario, fecha) de la misma manera.
- Los enlaces solución-función permiten que cualquier informe agrupe llamadas por solución sin tablas de cuotas por módulo.

## No objetivos

- Sin facturación ni ejecución de pagos.
- Sin autenticación ni comprobaciones de permisos.
- Sin contadores sin procesar para paneles.
## Límite de responsabilidad

Posee la medición y agregación de uso; no posee la facturación, la ejecución de pagos
ni la política de precios.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `analitycs`

## Fuente

`modules/repositories/analytics/rp-usage`