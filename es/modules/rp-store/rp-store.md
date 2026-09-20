# rp-store

## Propósito

Almacén de bloques direccionado por contenido — la capa inferior de almacenamiento binario de
todo el ecosistema. Almacena fragmentos por hash de contenido; no sabe nada de archivos,
pedidos, usuarios o entidades de negocio.

## Modelo mental

El productor divide los bytes en fragmentos → los guarda en el almacén → recibe
referencias. El consumidor reensambla los bytes a partir de las referencias. El almacén
en sí es un simple mapa key(blob_hash) → bytes con desduplicación: un
fragmento idéntico subido dos veces se almacena una vez.

## Valor en el ecosistema

Base de bytes direccionada por contenido:

- Blobs de bytes opacos identificados por hash, almacenados una vez, referenciados en cualquier lugar.
- Cualquier productor persiste bytes sin su propio almacenamiento binario.

## No objetivos

- Ni metadatos de archivos ni colecciones.
- Ni entradas de caché intermedias.
## Límite de responsabilidad

Posee put/get de bloques por referencia de contenido y ciclo de vida de fragmentos; no posee
nomenclatura/colecciones a nivel de archivo ni semántica de negocio de los servicios llamantes.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- `requests`

## Fuente

`modules/repositories/data/rp-store`