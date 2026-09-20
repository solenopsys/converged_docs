# wf-order-review-request

## Propósito

Contorno 2 del sistema de reseñas: preguntar al cliente una vez, después de terminar el trabajo.

Una ejecución encuentra un pedido que terminó hace suficiente tiempo, tiene un cliente al que escribir
y al que nunca se le ha preguntado; crea su enlace personal de reseña de un solo uso en
`rp-reviews`; y envía la solicitud mediante `lm-ses`.

## Por qué esto es un flujo de trabajo

La pregunta «¿qué pedidos terminados aún no han recibido la solicitud?» abarca dos servicios
que tienen prohibido conocerse entre sí: `rp-orders` no sabe qué es una reseña, y
`rp-reviews` almacena `orderId` como una cadena opaca. Poner ambas listas una al lado de la otra
es exactamente para lo que sirve un flujo — y `rt.node` es lo que hace que la creación del enlace
sobreviva a un reinicio sin crear un segundo enlace.

## Estructura

```
read-settings → list-finished (completed, updatedAt ≤ now − delay)
              → list-invites (which of those were already asked)
              → create-invite → send-email → mark-sent | mark-failed
```

Un correo por ejecución, para que una dirección atascada nunca bloquee la cola que está detrás y
la programación determine la velocidad. `dryRun` renderiza el correo y no crea nada: un
ensayo que dejara un enlace activo haría que la siguiente ejecución real omitiera ese pedido
por considerarlo ya solicitado.

Un correo rechazado vuelve de `lm-ses` como `{ success: false }`, no como una excepción,
por lo que es una rama normal que marca la invitación como `failed`, no un límite
de errores.

## Parámetros

- `from` (obligatorio) — dirección del remitente.
- `ses` (obligatorio) — `SesCredentials`.
- `shopName` — se inserta en `{{shopName}}` en las plantillas.
- `delayHours` — reemplaza `ReviewSettings.requestDelayHours` para una puesta al día.
- `dryRun` — renderiza y se detiene.

El asunto, el cuerpo, la base del enlace y el retraso provienen de `reviews.getSettings()`, por lo que la
tienda puede cambiar su propia redacción sin modificar este flujo.

## Dependencias directas del módulo

- `g-orders`
- `g-reviews`
- `g-ses`

## Código fuente

`modules/workflows/wf-order-review-request`
