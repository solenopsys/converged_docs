# rp-store

## Objetivo

Repositório de blocos endereçado por conteúdo — a camada binária mais baixa de armazenamento de
todo o ecossistema. Armazena fragmentos por hash de conteúdo; não sabe nada sobre arquivos,
pedidos, usuários ou entidades de negócio.

## Modelo mental

O produtor divide bytes em fragmentos → coloca-os no repositório → recebe
referências. O consumidor remonta os bytes a partir das referências. O repositório
em si é um mapa simples key(blob_hash) → bytes com desduplicação: um
fragmento idêntico enviado duas vezes é armazenado uma vez.

## Valor para o ecossistema

Base de bytes endereçada por conteúdo:

- Blobs de bytes opacos identificados por hash, armazenados uma vez, referenciados em qualquer lugar.
- Qualquer produtor persiste bytes sem armazenamento binário próprio.

## Não objetivos

- Nem metadados de arquivo nem coleções.
- Nem entradas de cache intermediárias.
## Limite de responsabilidade

Detém put/get de blocos por referência de conteúdo e ciclo de vida de fragmentos; não detém
nomeação/coleções em nível de arquivo nem semântica de negócio dos serviços chamadores.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `requests`

## Fonte

`modules/repositories/data/rp-store`