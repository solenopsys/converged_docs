# rp-threads

## Propósito

La capa conversacional única del ecosistema: cualquier módulo donde personas
o agentes intercambian mensajes no guarda mensajes propios — conserva un
`threadId`, y el diálogo en sí vive aquí.

## Modelo mental

La entidad (sala de chat, tema de foro, llamada, solicitud) almacena solo un `threadId`.
Todos los mensajes, el orden y el contexto viven en el hilo. Crear una entidad
= generar un `threadId` y entregarlo al llamante, que lo registra.

## Valor para el ecosistema

Un formato de diálogo en todas partes:

- Hilos y mensajes ordenados tras una única API, identificados por id de hilo opaco.
- Cualquier entidad adjunta una discusión sin sus propias tablas de mensajes.

## No objetivos

- No son salas de chat ni temas de foro — solo los hilos de mensajes que hay detrás.
- No es entrega de notificaciones ni resúmenes de diálogos.
## Límite de responsabilidad

Posee el ciclo de vida de hilos, el orden de mensajes y metadatos a nivel de hilo; no
posee salas/temas, membresía ni pasarelas de transporte para
email/SMS/push.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `ai`

## Fuente

`modules/repositories/communications/rp-threads`