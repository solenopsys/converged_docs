# sf-chats

## Propósito

Salas de chat, como tres pestañas separadas: la lista de salas, la conversación de una sala y
los miembros de una sala. Gestionar quién está en una sala y leer lo que dijeron son
dos tareas y, por lo tanto, dos pestañas.

## Límite de responsabilidad

Se encarga de la navegación de salas, la pantalla de conversación y la edición de miembros. Los mensajes
pertenecen a `rp-threads`, leídos directamente desde el navegador; los archivos pertenecen a
`rp-files` mediante un mensaje de tipo `link`.

## Cómo se crea una sala

`createRoom` en `rp-chats` genera el id de la sala y el id del hilo, y registra al
creador del token como `owner`; esta superficie registra entonces el hilo con
`rp-threads`. `rp-chats` nunca llama a otro repositorio.

## Actualizaciones en tiempo real

Un mensaje nuevo se publica para cada miembro por nombre a través de `pushrouter` de Fujin,
nunca para todo el tenant: la existencia de una sala privada no es pública, incluso cuando su
contenido permanece protegido por el predicado de lectura. El push solo transporta identificadores.

## Dependencias directas del módulo

- `effector`, `front-core`, `g-chats`, `g-threads`, `signal-channel`, `threads-state`

## Pertenencia a la solución

- `communications`

## Fuente

`modules/surfaces/communications/sf-chats`
