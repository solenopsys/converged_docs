# lm-sms

## Propósito

Rama SMS de la distribución compartida de notificaciones: transporte de proveedor tras el contrato rp-notify.

## Valor del ecosistema

Los avisos urgentes (incidentes, códigos de invitación, cambios de estado) llegan a los teléfonos mientras otros canales llevan la versión larga. Misma API de intención que email/push.

## No objetivos

Sin reglas de campaña o segmentación — el dominio llamante decide.

## Límite de responsabilidad

Posee la conectividad del proveedor SMS y el formato de la carga; no posee reglas de segmentación comercial/de campaña.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/providers/lm-sms`