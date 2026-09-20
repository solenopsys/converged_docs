# rp-webhooks

## Propósito

La única puerta de entrada para el mundo exterior: los sistemas externos acceden a un
endpoint de webhook, y este módulo valida, normaliza y distribuye los eventos
hacia dentro. Ningún dominio expone su propio esquema de URL de callback.

## Modelo mental

El sistema externo envía POST → el webhook valida la firma y la estructura → normalizado
el evento se registra como una entrega y se dirige al tema configurado.
Los intentos de entrega y la validación residen aquí; la reacción de negocio ocurre
aguas abajo.

## Valor para el ecosistema

Un único ingreso para callbacks externos:

- Configuraciones de endpoints y registros de entrega tras una única API.
- Cualquier sistema externo obtiene la misma forma de endpoint en lugar de una infraestructura por integración.

## No objetivos

- No es ejecución de flujos de trabajo.
- No es publicación de eventos ni envío de notificaciones.
## Límite de responsabilidad

Responsable del transporte de webhooks, la validación y los intentos de entrega; no es responsable
del procesamiento de negocio del sistema de destino.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a soluciones

- No incluido en una solución predefinida

## Fuente

`modules/repositories/automation/rp-webhooks`