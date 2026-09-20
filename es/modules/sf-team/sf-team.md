# sf-team

## Propósito

El equipo como un área de trabajo: quién trabaja aquí, qué puede hacer cada persona y a quién
se ha invitado pero aún no ha llegado.

## Proyecciones

Cuatro vistas `setOf`, que el shell convierte en los botones permanentes de la pestaña
— **Equipo**, **Invitaciones**, **Horario**, **Derechos** — más una vista
`objectOf`, la tarjeta de la persona, que se abre como una subtapa *dentro* de la misma área. Sin
pulsar nada, el área muestra su propia pantalla (`team.statistic`, resuelta a través de
su vista `setOf`, el patrón que utilizan `sf-logs` y `sf-equipment`).

## Qué define esta superficie

**La consola no puede conceder nada.** `rp-access` es `@Access("internal")` y
el runtime rechaza un JWT de usuario antes de comprobar cualquier permiso
(`messaging-access.ts:176`). Por eso, toda operación que cambie lo que alguien puede
hacer ejecuta `wf-team-invite` en centimanus, que contiene el token de servicio del clúster.
Quién puede ejecutarla es la concesión ordinaria `wf/workflows/wf-team-invite.js(x)`, que
vive en un único archivo de preajustes — esa concesión constituye todo lo relativo a «quién puede añadir personas».

Tres métodos de invitación en `rp-identity` llevan un `@Access("user")` a nivel de método,
por lo que la columna de entrega puede leerse sin un workflow por cada actualización de tabla; están
controlados por `rp/identity/listInvites(r)` en los preajustes del propietario y del gerente.

La proyección **Derechos** se compone en el navegador a partir del registro y las
invitaciones, porque no se puede consultar desde aquí al servicio que conoce la respuesta real. Muestra
la intención registrada — el rol que se asignó a una persona y las etiquetas que lo acompañaban —,
no una lectura de su token activo.

## Operaciones

`team.member.import` (para esto existe este contorno: se pega una lista y se obtiene
una tabla rellenada exactamente con esas personas), `team.member.create`,
`team.member.save`, `team.member.setRole`, `team.member.deactivate`,
`team.invite.revoke`, `team.shift.create`.

Tres de ellas se publican en el catálogo de chat en `llm.json`.

## Dependencias directas de módulos

- `front-core`, `g-centimanus`, `g-identity`, `g-staff`

## Pertenencia a la solución

- `production`

## Fuente

`modules/surfaces/sequrity/sf-team`
