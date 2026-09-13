# rp-community

## Propósito

Estructura y propiedad del foro: secciones, temas, quién los escribió y quién puede
verlos. La discusión de un tema no está aquí: un tema contiene un `threadId`
y los mensajes viven en `rp-threads`.

## Límite de responsabilidad

Es responsable de las secciones y los temas. No llama a `rp-threads` ni a ningún otro repositorio:
`createTopic` genera un `threadId` y lo devuelve, y el llamador registra el
hilo y escribe la publicación inicial por sí mismo.

## Identidad y autoría

`createdBy` nunca se acepta de un llamador. Se obtiene del token verificado
a través de `getCurrentWorkspaceContext()`, que `messaging-backend` prefiere sobre
cualquier dato que afirme el sobre. Los identificadores de temas e hilos se generan aquí por la misma
razón: un identificador que puede elegir un cliente es un identificador que puede robar, y la tabla de
tags de acceso no registra ningún tipo de objeto para detectar la colisión.

## Visibilidad

Las secciones y los temas contienen una columna `visibility` (`public` | `authenticated` |
`private` | `tagged`), y un tema nuevo hereda el valor de su sección a menos que
solicite algo más restrictivo. Las etiquetas detrás de `tagged` pertenecen a la relación
compartida `access_tags` descrita en `access-control.md`; esa parte aún no está
implementada, por lo que actualmente `visibility` se registra, pero no se aplica.

## Bloqueo

`touchTopicActivity` es el único lugar donde se puede aplicar un bloqueo: `rp-threads`
acepta un mensaje sin saber que existen temas, por lo que una pantalla llama a esto después
de publicar y trata un rechazo como una publicación fallida.

## Dependencias directas del módulo

- `back-core`, `nrpc`, `g-community`

## Pertenencia a la solución

- `communications`

## Fuente

`modules/repositories/communications/rp-community`
