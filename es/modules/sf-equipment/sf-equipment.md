# sf-equipment

## Propósito

La planta de producción como un área de trabajo unificada: qué máquinas existen, en qué estado se encuentra cada una,
qué trabajo está ejecutando, qué indican sus datos de telemetría en este momento, qué le ha sucedido
y qué está programado en ella a continuación.

## Estructura

La superficie declara tres vistas `setOf` — máquinas, diario, programación — que
el espacio de trabajo convierte en los botones permanentes de esta pestaña, y una vista `objectOf`
para una máquina. Por lo tanto, abrir una impresora abre una subpestaña *dentro de* equipment
en lugar de navegar fuera de ella. Sin nada seleccionado, la superficie
muestra su propia pantalla, `EquipmentDashboardView`.

## Límite de responsabilidad

Lee y escribe en `rp-equipment`. Lee `rp-orders` para el trabajo que está
realizando una máquina y `rp-telemetry` para sus parámetros en tiempo real — ambos directamente desde el
navegador, que es donde corresponde una composición de dos llamadas; ninguno de los dos repositorios
conoce al otro.

El estado de la máquina se escribe desde aquí porque, hasta que un puente de telemetría lo comunique,
el operador que está junto a la máquina es su única fuente de verdad.

## Dependencias directas del módulo

- `g-equipment`
- `g-orders`
- `g-telemetry`

## Pertenencia a la solución

- `production`

## Fuente

`modules/surfaces/business/sf-equipment`
