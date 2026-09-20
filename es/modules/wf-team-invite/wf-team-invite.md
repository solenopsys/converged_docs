# wf-team-invite

## Propósito

Convierte una lista pegada de personas — «nombre + dirección», con cualquier formato
que le haya dado una persona — en cuentas de usuario, roles, tarjetas de personal e
invitaciones, y envía a cada persona el enlace que inicia su sesión.

Existe porque cuatro servicios tienen que avanzar juntos para una fila de esa lista
(`rp-identity`, `rp-access`, `rp-staff`, `rp-auth` más una lambda de correo) y los
microservicios no se llaman entre sí.

## Por qué también es el límite de privilegios

`rp-access` rechaza directamente un JWT de usuario (`@Access("internal")`), por lo que ninguna
superficie puede asignar un rol. centimanus ejecuta este script con `SERVICE_TOKEN`, y quién
puede ejecutarlo es una concesión ordinaria — `wf/workflows/wf-team-invite.js(x)` — comprobada
en el extremo (`signal_provider.zig:146`) y escrita en un único archivo de preajustes. Por eso
el producto no tiene el concepto de «administrador».

El script no puede ver quién lo llamó, así que la protección contra la escalada es una lista fija:
`manager`, `operator`, `viewer`. `owner` y `root` no se pueden conceder aquí.

## Estructura

1. fuentes de texto — `files.materialize` + `files.extractText`, además de `rawText`;
2. personas — primero `rt.llm`, y una expresión regular línea por línea como alternativa;
3. un `rt.attempt` por persona — usuario, preajuste base + rol, etiquetas de grupo, tarjeta,
   invitación;
4. la carta — su propio intento, de modo que un relay rechazado sea una rama y no una cuenta
   perdida;
5. el informe, cuyos `staffIds` la superficie convierte en una tabla abierta compuesta exactamente
   por estas personas.

Volver a ejecutar la misma lista no causa problemas: una dirección conocida se `updated`, nunca
se crea una segunda cuenta.

## Dependencias directas del módulo

- `g-access`, `g-auth`, `g-files`, `g-identity`, `g-notify`, `g-ses`, `g-smtp`,
  `g-staff`

## Pertenencia a la solución

- `production`

## Fuente

`modules/workflows/wf-team-invite`
