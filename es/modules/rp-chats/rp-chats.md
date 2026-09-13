# rp-chats

## Propósito

Salas de chat, sus miembros y sus contextos por sala. La conversación
en sí no está aquí: una sala contiene un `threadId` y los mensajes viven en
`rp-threads`.

## Límite de responsabilidad

Gestiona las salas, los roles y los contextos. No llama a ningún otro repositorio — `createRoom` genera el
`threadId` y lo devuelve, y el llamador registra el hilo.

## Identidad y acceso

El llamador proviene del token verificado, nunca de un parámetro. Dos
consecuencias que vale la pena mencionar:

- `listRooms` está limitado al llamador dentro de la consulta, por lo que sustituir el id de
otro usuario ya no permite leer sus salas, y `totalCount` no puede filtrar el número
de salas que ocultó;
- cualquier operación que acceda a una sala por su id comprueba primero la pertenencia.

`chart_room_users` permanece incluso después de que llegue `access_tags`: una etiqueta expresa
la pertenencia, pero no distingue entre `owner`, `admin` y `member`.

## Nota sobre los nombres de las tablas

Las tablas se escriben `chart_rooms` / `chart_room_users`. El error tipográfico es
coherente en todas las migraciones, entidades y consultas, por lo que el código funciona; cambiar el nombre
requiere una migración, no una edición.

## Dependencias directas del módulo

- `back-core`, `nrpc`, `g-chats`

## Pertenencia a la solución

- `communications`

## Fuente

`modules/repositories/communications/rp-chats`
