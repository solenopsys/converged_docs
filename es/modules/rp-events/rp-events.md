# rp-events

## Propósito

El diario compartido del bus de eventos de negocio: cualquier dominio publica aquí «lo que sucedió» sin conocer a sus consumidores. Pedidos, solicitudes, equipos, pagos — todos hablan un mismo lenguaje de eventos.

## Modelo mental

El productor emite un evento tipado (kind, entity, time, payload) → llega al feed compartido. Los consumidores (desencadenadores de flujos de trabajo, notificadores, analítica) se suscriben por tipo y reaccionan. El publicador nunca llama directamente al consumidor.

## Valor en el ecosistema

Punto de desacoplamiento para cambios de estado:

- Eventos de negocio tipados publicados una vez y listados de nuevo tras una única API.
- Cualquier dominio registra «lo que sucedió» sin conocer a sus lectores.

## No objetivos

- No es la cinta de registro en bruto.
- No son contadores ni agregados.
- No es la ejecución del flujo de trabajo en sí.
## Límite de responsabilidad

Posee la creación, el almacenamiento y la recuperación de eventos; no posee el procesamiento de negocio del lado del consumidor ni la ejecución de flujos de trabajo.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/repositories/business/rp-events`