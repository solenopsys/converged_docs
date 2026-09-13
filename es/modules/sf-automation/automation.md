# Automatización

## Propósito

Es propietaria del espacio de trabajo de automatización: los flujos de trabajo y sus ejecuciones, los disparadores del bus que los inician, las programaciones recurrentes y los endpoints de webhook entrantes.

## Límite de responsabilidad

Controla la experiencia del espacio de trabajo. No ejecuta flujos de trabajo, conserva programaciones ni entrega webhooks; inicia una ejecución a través del runtime y lee el registro de vuelta desde rp-dag.

## La sección DAG

- **Flujos de trabajo** — el catálogo que publica la Solución activa, de solo lectura.
  Abrir uno equivale a solicitar su ejecución: los parámetros se escriben como JSON y se pasan a
  `centimanus.runWorkflow`.
- **Ejecuciones** — cada ejecución, con su estado.
- **Detalles de la ejecución** — el árbol de lo que hizo la ejecución. Una línea por nodo: a qué profundidad se encuentra, si finalizó y cuánto tardó. Al desplegar un nodo se muestran las llamadas de servicio que realizó y lo que devolvieron. A un nodo que delegó mediante
  `rt.sub` le siguen los nodos de la ejecución a la que delegó, un nivel hacia dentro.
  Una ejecución que aún está en curso se actualiza automáticamente.
- **Disparadores** — «cuando aparezca este tema del bus, ejecuta ese flujo de trabajo». Tema,
  flujo de trabajo, parámetros JSON, activado/desactivado.
- **Variables** — estado del flujo de trabajo escrito por `rt.set`.

Los parámetros se escriben como JSON en todas partes en lugar de generarse en un formulario: los parámetros de un flujo de trabajo son propios de este y cambian con él, por lo que un campo de texto sigue siendo correcto cuando cambian y lo que se escribe es lo que recibe el flujo de trabajo.

## Dependencias directas del módulo

- Ninguna

## Pertenencia a soluciones

- No incluido en una solución predefinida

## Código fuente

`modules/surfaces/automation/sf-automation`
