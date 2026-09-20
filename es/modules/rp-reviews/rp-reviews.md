# rp-reviews

## Propósito

El sistema de reseñas de la tienda, en tres tablas que responden a tres preguntas diferentes.

- `reviews` — qué dijo un cliente, qué respondió la tienda y si aparece
  en el sitio. La moderación vive aquí: una reseña que llegó desde fuera nace como
  `pending` y solo es visible dentro de la consola hasta que alguien la publica.
- `review_invites` — un enlace personal de un solo uso por pedido y qué ocurrió
  con él: enviado, abierto, respondido, caducado. Este es el embudo que consulta la tienda.
- `review_settings` — una fila de JSON: las plataformas externas, el umbral,
  las plantillas de correo, los retrasos y el margen de seguimiento.

## Límite de responsabilidad

Es responsable de las reseñas, las invitaciones y la configuración del embudo. No sabe nada sobre los pedidos:
`Review.orderId` y `ReviewInvite.orderId` son cadenas opacas, y vincularlas
con pedidos reales es tarea de `wf-order-review-request` (que pregunta) y
`sf-reviews` (que muestra). No es responsable de los hilos de la comunidad.

## Dos puertas

El acceso se realiza mediante etiquetas, como en todas partes: una reseña publicada lleva `public`, cualquier otra lleva
`authenticated` más `moderator`, lo que permite a la tienda actuar
sobre una reseña que nadie de la tienda escribió.

La puerta del cliente es diferente. `getInviteByToken`, `markInviteOpened` y
`submitByToken` se autorizan mediante el propio token —una capacidad, no una
sesión—, por lo que el formulario público funciona sin ningún inicio de sesión. Devuelven una vista reducida que no incluye ni el contacto ni el id de la invitación, y
`submitByToken` consume el enlace de forma condicional, de modo que dos envíos desde el mismo correo producen
una reseña y un rechazo, en lugar de dos reseñas.

## Control de reseñas

`positiveThreshold` cambia el *énfasis* del formulario público y nada más:
cuando se alcanza o supera, al autor se le ofrecen primero las plataformas externas; por debajo, se le muestra primero una palabra para la tienda. Los enlaces a las plataformas permanecen visibles en ambos casos, porque mostrar el camino hacia una reseña pública solo a clientes satisfechos es algo que Google y varias otras plataformas prohíben. El comportamiento seguro es el predeterminado.

## Dependencias directas del módulo

- Ninguna

## Pertenencia a la solución

- `production`

## Fuente

`modules/repositories/business/rp-reviews`
