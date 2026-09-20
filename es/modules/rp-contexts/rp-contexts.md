# rp-contexts

## Propósito

El almacén compartido de contextos nombrados para IA: prompts, variantes de idioma y
conocimiento de dominio se encuentran aquí en lugar de estar codificados en cada flujo de trabajo.
Versionado por nombre, resuelto por idioma.

## Modelo mental

El flujo de trabajo o el asistente solicita un contexto por nombre (+ idioma) → obtiene el
texto actual. Los editores actualizan los contextos sin volver a implementar los consumidores.
El almacenamiento y la recuperación están aquí; la ingeniería de prompts corresponde a los editores.

## Valor para el ecosistema

Un estante de conocimiento para las rutas de IA:

- Contextos nombrados con variantes de idioma tras una API.
- Cualquier ruta de IA resuelve el mismo contexto nombrado en lugar de sus propias copias de prompts.

## No objetivos

- No es historial de chat ni hilos de diálogo.
- No es ejecución de prompts — solo textos de contexto almacenados.
## Límite de responsabilidad

Posee el almacenamiento y la recuperación de contextos de IA nombrados y variantes de idioma;
no posee la infraestructura del proveedor de modelos ni el comportamiento de diálogo.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `ai`

## Fuente

`modules/repositories/ai/rp-contexts`