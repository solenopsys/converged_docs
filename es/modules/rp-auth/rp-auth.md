# rp-auth

## Propósito

La única puerta de entrada para demostrar «quién eres»: sesiones, credenciales y
emisión de tokens para todo el ecosistema. Ningún dominio gestiona su propio inicio de sesión.

## Modelo mental

El usuario presenta credenciales → auth las valida y emite una sesión/token →
cada llamada posterior lo transporta y la capa de acceso decide lo que puede hacer.
El inicio de sesión demuestra la identidad; los permisos son una capa separada.

## Valor para el ecosistema

Un backend de inicio de sesión para todas las superficies:

- Enlaces mágicos, sesiones de actualización y registros de clientes OAuth en un solo lugar.
- Cualquier frontend autentica a los usuarios de la misma manera en lugar de usar sus propias tablas de sesiones.

## No objetivos

- No políticas de permisos.
- No registros de perfil de usuario.

## Límite de responsabilidad

Posee los flujos de autenticación y la lógica de emisión de tokens/sesiones; no posee
adaptadores de proveedores OAuth de terceros ni evaluación de políticas de autorización.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `security`

## Fuente

`modules/repositories/sequrity/rp-auth`