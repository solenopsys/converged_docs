# lm-ses

## Propósito

Segmento SES de la distribución compartida de notificaciones: transporte de correo electrónico de AWS tras el contrato rp-notify.

## Valor del ecosistema

El correo masivo y transaccional (invitaciones de revisión, actualizaciones de pedidos, invitaciones de equipo) fluye a través de una integración SES. Las credenciales se resuelven mediante lm-secrets.

## Objetivos excluidos

Sin política de canal ni plantillas — eso corresponde a rp-notify y al dominio llamante.


## Límite de responsabilidad

Posee la integración de envío y el mapeo específicos de SES; no posee el dominio de creación de plantillas de correo electrónico.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/providers/lm-ses`