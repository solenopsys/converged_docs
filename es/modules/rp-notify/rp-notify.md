# rp-notify

## Propósito

La única distribución de notificaciones del ecosistema: cualquier dominio dice «informar al usuario» una vez, y este módulo elige los canales, la política y los reintentos. Los dominios nunca acceden directamente a las API de SMTP/SMS/push.

## Modelo mental

El dominio emite una intención de notificación (quién, qué, plantilla, urgencia) → notify resuelve los canales y la política de entrega → los adaptadores de proveedores externos realizan el envío real. Los reintentos y la conmutación de canal viven aquí, el significado del mensaje vive en el dominio.

## Valor para el ecosistema

Un único almacén de «informar al usuario»:

- Plantillas, canales, perfil y registros de envío tras una única API.
- Cualquier dominio mantiene sus textos de notificación y registros de entrega en un solo lugar.

## No objetivos

- No la entrega de mensajes en sí — solo plantillas, canales y registros de envío.
- No hilos de diálogo.

## Límite de responsabilidad

Posee la orquestación de notificaciones y la política de entrega; no posee adaptadores de envío específicos de proveedor de bajo nivel ni lógica de activación de dominio.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/repositories/communications/rp-notify`