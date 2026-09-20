# rp-requests

## Propósito

Admisión y ciclo de vida de solicitudes de servicio: envío, transiciones de estado, archivos adjuntos (por fileId) y promoción a pedidos mediante wf-request-to-order. El análisis se ejecuta a través de wf-request-analyze.

## Límite de responsabilidad

Posee el ciclo de vida de la solicitud y las transiciones de estado; no posee el transporte de mensajería, los bytes de archivo ni la ejecución del análisis.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `requests`

## Fuente

`modules/repositories/business/rp-requests`