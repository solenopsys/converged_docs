# lm-push

## Propósito

Rama push del fan-out de notificaciones compartido: transporte push web/móvil detrás del contrato rp-notify.

## Valor para el ecosistema

Avisos en tiempo real para chats, pedidos, solicitudes — entregados junto con email/SMS desde una única intención de notificación.

## No objetivos

Sin segmentación ni lógica de negocio — eso corresponde a rp-notify y al dominio llamante.

## Límite de responsabilidad

Posee los detalles de integración del proveedor push; no posee la lógica empresarial de segmentación de notificaciones.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a soluciones

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/providers/lm-push`