# lm-secrets

## Propósito

El adaptador compartido de bóveda de secretos: valores de secretos con nombre para toda
la plataforma tras un único contrato. Los servicios leen aquí los secretos de configuración en lugar de
la dispersión de env o clientes de bóveda por módulo.

## Modelo mental

El servicio pregunta por nombre de secreto → obtiene el valor. La rotación ocurre en un
lugar y se propaga a cada consumidor. Los detalles del backend de almacenamiento quedan tras
el contrato.

## Valor del ecosistema

Una sola puerta de bóveda para todos:

- Credenciales de proveedores, tokens de integración, secretos OAuth — misma forma get/set/delete.
- Cualquier consumidor mantiene los secretos fuera del código y la configuración; la rotación ocurre en un solo lugar.
- Las nuevas integraciones no necesitan nueva infraestructura de secretos.

## No objetivos

- No es autenticación ni comprobaciones de permisos.
- No son registros de identidad de usuarios.
## Límite de responsabilidad

Responsable de almacenar, recuperar y eliminar valores de secretos con nombre; no es responsable de
identidad, permisos ni lógica de sesión.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a soluciones

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/sequrity/lm-secrets`