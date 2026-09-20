# lm-smtp

## Propósito

Rama SMTP de la distribución compartida de notificaciones: transporte de proveedor simple detrás del contrato rp-notify.

## Valor del ecosistema

El dominio emite una intención de notificación una vez a través de rp-notify → este adaptador la entrega por SMTP. Cambiar o añadir proveedores de correo electrónico nunca afecta a los dominios.

## No objetivos

Sin política de canal, reintentos ni plantillas — esto corresponde a rp-notify y al dominio invocador.


## Límite de responsabilidad

Posee el transporte SMTP y la gestión de entrega a nivel de protocolo; no posee la orquestación de notificaciones de alto nivel.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/providers/lm-smtp`