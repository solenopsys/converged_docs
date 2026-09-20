# rp-logs

## Propósito

El único diario de solo adición del ecosistema: cualquier servicio, equipo
o flujo de trabajo escribe aquí «lo que sucedió» en lugar de crear su propio almacén
de registros. Escrituras económicas, lecturas por tiempo/fuente.

## Modelo mental

El productor envía un evento (tiempo, fuente, nivel, texto/payload) → llega al
flujo compartido. El consumidor lee un fragmento por fuente o intervalo. Sin
agregación ni alertas internas — solo el registro del hecho.

## Valor para el ecosistema

Un flujo reutilizado por todos:

- Servicios: registros operativos sin almacenamiento propio por `rp-*`.
- Equipos: registros de máquinas/dispositivos — misma API, distinta fuente, desde impresoras 3D
  hasta cualquier módulo o sistema externo.
- Cualquier productor escribe «lo que sucedió» en un solo lugar en lugar de crear
  su propio almacén de registros; la auditoría y la revisión leen una única línea de tiempo.

## No objetivos

- Sin contadores ni agregados.
- Sin muestras numéricas ni registros de uso.
- Sin trazado de llamadas distribuidas ni alertas.
## Límite de responsabilidad

Posee las API de ingestión y recuperación de registros; no posee métricas de negocio,
agregación, alertas ni estrategia de trazado.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `analitycs`

## Fuente

`modules/repositories/analytics/rp-logs`