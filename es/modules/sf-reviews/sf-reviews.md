# sf-reviews

## Propósito

El sistema de reseñas como un área de trabajo unificada: lo que los clientes dijeron sobre el trabajo,
cuáles de esas reseñas están en el sitio, qué respondió la tienda y hasta dónde está llegando la solicitud:
cuántos enlaces se enviaron, cuántos se abrieron y cuántas respuestas llegaron.

## Estructura

La superficie declara dos vistas `setOf` — las reseñas y las invitaciones que las solicitaron — que el espacio de trabajo convierte en los botones permanentes de esta pestaña, y una vista `objectOf` para una reseña. La cola de moderación, el muro de reseñas publicadas y el conjunto de rechazadas son preajustes de la tabla de reseñas, no tres tipos: es una sola lista leída de tres maneras. Por lo tanto, abrir una reseña abre una subpestaña *dentro* de las reseñas en lugar de navegar fuera de ellas. Cuando no se pulsa nada, la superficie muestra su propia pantalla, `ReviewsDashboardView`.

## Límite de responsabilidad

Lee y escribe en `rp-reviews`. Lee `rp-orders` para consultar el trabajo al que se refiere una reseña — directamente desde el navegador, que es donde corresponde una composición de dos llamadas; ninguno de los dos repositorios conoce al otro.

El envío no se realiza desde aquí. `wf-order-review-request` genera y envía el enlace personal, y `wf-order-review-followup` hace el seguimiento, porque llegar a un pedido y a una reseña dentro de un mismo proceso es precisamente para lo que sirve un flujo de trabajo. «Solicitar una reseña» en esta superficie genera el enlace y deja el envío a ese flujo, de modo que siga habiendo un único remitente y un único registro.

## Reglas de las reseñas

El formulario público muestra las plataformas externas a todo el mundo. El umbral de la tienda modifica el *énfasis* — primero se ofrecen las plataformas a un cliente satisfecho y, a uno insatisfecho, la posibilidad de hablar primero con la tienda —, pero nunca la disponibilidad de los enlaces, porque mostrar el camino hacia una reseña pública solo a clientes satisfechos es algo que Google y varias otras plataformas prohíben. La tarjeta indica hacia qué opción se inclinó el formulario para una reseña determinada; no bloquea nada.

## Dependencias directas del módulo

- `g-reviews`
- `g-orders`

## Pertenencia a la solución

- `production`

## Fuente

`modules/surfaces/business/sf-reviews`
