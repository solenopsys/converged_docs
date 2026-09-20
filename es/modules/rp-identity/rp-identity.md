# rp-identity

## Propósito

El registro de perfiles compartido: un registro de identidad por persona o cuenta de servicio,
vinculado desde cada dominio. Pedidos, chats, tarjetas de personal — todos apuntan
al mismo perfil en lugar de copiar nombres y atributos.

## Modelo mental

Identidad = registro estable (id, atributos principales, estado del ciclo de vida). Los dominios
almacenan el id de identidad y leen los atributos bajo demanda; nunca bifurcan el
perfil. La autenticación demuestra la identidad, el acceso la verifica, los dominios la referencian.

## Valor para el ecosistema

Un «quién» para la plataforma:

- Registros de usuarios, enlaces de métodos de autenticación e invitaciones en un solo lugar.
- Cualquier dominio almacena un id de usuario opaco y lee los atributos bajo demanda en lugar de bifurcar perfiles.

## No objetivos

- No es inicio de sesión ni sesiones.
- No son permisos.
- No es estructura organizativa ni semántica de personal.
## Límite de responsabilidad

Posee los registros de identidad y el estado del ciclo de vida de la identidad; no posee
políticas de permisos detalladas ni flujos de autenticación.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `security`

## Fuente

`modules/repositories/sequrity/rp-identity`