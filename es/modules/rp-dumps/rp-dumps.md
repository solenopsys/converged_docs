# rp-dumps

## Propósito

El muelle de exportación compartido: cualquier dominio toma instantáneas de sus datos aquí para migración,
copia de seguridad o transferencia en lugar de inventar su propio formato de volcado. Instantáneas
empaquetadas con metadatos de recuperación.

## Modelo mental

El dominio solicita un volcado (alcance, tiempo) → el volcado se genera y empaqueta →
los metadatos de recuperación apuntan al artefacto almacenado.
La generación y la contabilidad residen aquí; el archivo a largo plazo reside en otro lugar.

## Valor del ecosistema

Una única historia de exportación para la plataforma:

- Listado de almacenamiento, estadísticas, compactación y segmentos de volcado tras una API.
- Cualquier dominio se vuelve exportable sin su propia maquinaria de instantáneas.

## No objetivos

- No es servicio de archivos en vivo.
- No es un almacenamiento de bytes paralelo.
## Límite de responsabilidad

Posee la generación, el empaquetado y los metadatos de recuperación de volcados; no posee
la plataforma de archivo a largo plazo.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/repositories/data/rp-dumps`