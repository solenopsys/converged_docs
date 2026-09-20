# wf-order-review-followup

## Propósito

El único seguimiento. Una ejecución toma un enlace de reseña que se envió, permaneció sin respuesta durante
el número configurado de días y no ha sido objeto del número permitido de seguimientos,
y lo solicita una vez más.

## Por qué esto es un flujo de trabajo

La elección no es: `reviews.findInvitesToFollowUp` es una consulta sobre invitaciones
y pertenece a `rp-reviews`. Lo que añade este flujo es el nombre del pedido
para el correo y el envío: dos servicios en un proceso, que es la definición de un
flujo de trabajo aquí.

## Lo que deliberadamente nunca hace

Nunca hace seguimiento a alguien que abrió el formulario. Leyó la solicitud y decidió no
escribir; volver a preguntar es cómo una solicitud de reseña se convierte en spam. Esa condición vive
en la consulta del repositorio y no en este flujo, para que un futuro invocador no pueda
olvidarla.

Un seguimiento rechazado deja la invitación en `sent` en lugar de `failed`: el primer correo
sí se envió, y el cliente todavía puede responderlo.

## Estructura

```
read-settings → find-due (sent, nunca abierto, dentro del límite permitido)
              → read-order (solo para el nombre)
              → send-email → count-followup
```

Contar el seguimiento es lo que lo hace *único*: la misma consulta no devolverá
de nuevo ese enlace. `dryRun` renderiza el correo y no cuenta nada. `maxFollowups: 0`
desactiva por completo los seguimientos, y el flujo se detiene antes de solicitarlos.

## Parámetros

- `from` (obligatorio) — dirección del remitente.
- `ses` (obligatorio) — `SesCredentials`.
- `shopName`, `delayDays`, `maxFollowups`, `dryRun` — anulaciones; los valores predeterminados
  provienen de `reviews.getSettings()`.

## Dependencias directas del módulo

- `g-orders`
- `g-reviews`
- `g-ses`

## Código fuente

`modules/workflows/wf-order-review-followup`
