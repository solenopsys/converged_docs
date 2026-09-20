# rp-access

## Propósito

La capa de autorización compartida: cada `rp-*` pregunta aquí «¿puede este actor hacer esto?» en lugar de inventar sus propias comprobaciones de permisos. Un árbol de permisos, una regla de evaluación, aplicada antes de que se ejecute ningún manejador.

## Modelo mental

Dos preguntas, dos capas: el acceso a métodos («puede llamar a X») se mantiene en el árbol de permisos y lo aplica el guard; el acceso a objetos («qué filas devuelve la llamada») se evalúa por entidad. Sin lo primero, cualquiera podría llamar a `deleteTopic`.

## Valor en el ecosistema

Raíz de confianza única para las decisiones:

- El árbol de permisos, los ajustes preestablecidos, las etiquetas y los tokens emitidos viven en un solo lugar.
- Cualquier servicio consulta el mismo árbol en lugar de crear sus propias tablas de políticas.

## No objetivos

- Ni inicio de sesión ni emisión de sesiones.
- Ni almacenamiento de secretos.
## Límite de responsabilidad

Posee la evaluación de políticas de autorización y los ámbitos de acceso; no posee la verificación de identidad ni el inicio de sesión de autenticación.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `security`

## Fuente

`modules/repositories/sequrity/rp-access`