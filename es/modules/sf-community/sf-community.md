# sf-community

## Propósito

El foro, como tres pestañas separadas: secciones, los temas de una sección y la
discusión de un tema. Al abrir una fila, se abre una pestaña junto a la actual;
no hay ninguna pantalla que muestre a la vez un árbol de secciones, una tabla de
temas y un hilo.

## Límite de responsabilidad

Se encarga de la navegación del foro y de la pantalla del tema. Los mensajes
pertenecen a `rp-threads`, que el navegador lee directamente; los adjuntos
pertenecen a `rp-files` mediante un mensaje `link`. La pertenencia, los roles y
los tickets no forman parte de esto.

## Cómo se crea un tema

`createTopic` en `rp-community` genera el id del tema y el id del hilo, y sella
el autor a partir del token; esta superficie registra entonces el hilo y escribe
la publicación inicial en `rp-threads`. La separación es deliberada: los ids que
un cliente puede elegir son ids que puede robar, y que un repositorio llame a
otro repositorio es precisamente lo que la arquitectura prohíbe.

## Actualizaciones en tiempo real

Las respuestas llegan a través del canal de negocio de Fujin (`pushrouter`) por
medio de la biblioteca `threads-state`, no mediante consultas periódicas. Un
push solo transporta identificadores; el texto se vuelve a leer desde
`rp-threads`, donde se aplica el predicado de lectura.

## Dependencias directas del módulo

- `front-core`, `g-community`, `g-threads`, `signal-channel`, `threads-state`

## Pertenencia a la solución

- `communications`

## Origen

`modules/surfaces/communications/sf-community`
