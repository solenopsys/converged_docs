# rp-sheduller

## Propósito

El disparador de tiempo compartido: programaciones cron y su historial de ejecución para
todo el ecosistema. Cualquier trabajo recurrente se registra aquí en lugar de ejecutar
su propio bucle de temporizador.

## Modelo mental

El operador define una entrada cron (qué flujo de trabajo, cuándo, con qué args) → el
runtime se activa según la programación → el historial registra qué se ejecutó y cómo terminó.
Este módulo almacena y lista entradas; nunca ejecuta nada por sí mismo.

## Valor para el ecosistema

Un único reloj para el trabajo recurrente:

- Filas cron, historial de ejecuciones y estadísticas tras una API.
- Cualquier trabajo recurrente solo necesita una fila cron — sin nueva infraestructura de temporizadores.

## No objetivos

- No es definición ni ejecución de flujos de trabajo.
- No son disparadores únicos — solo programaciones recurrentes.
## Límite de responsabilidad

Gestiona CRUD/lista/estadísticas de entradas cron y registros de historial; no ejecuta
flujos de trabajo, temporizadores, reintentos ni distribución en segundo plano.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a soluciones

- No incluido en una solución predefinida

## Fuente

`modules/repositories/automation/rp-sheduller`