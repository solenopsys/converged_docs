# rp-events

## Objetivo

O diário compartilhado do barramento de eventos de negócio: qualquer domínio publica aqui “o que aconteceu” sem conhecer seus consumidores. Pedidos, solicitações, equipamentos, pagamentos — todos falam uma única linguagem de eventos.

## Modelo mental

O produtor emite um evento tipado (kind, entity, time, payload) → ele chega ao feed compartilhado. Os consumidores (gatilhos de workflow, notificadores, análises) assinam por tipo e reagem. O publicador nunca chama o consumidor diretamente.

## Valor no ecossistema

Ponto de desacoplamento para mudanças de estado:

- Eventos de negócio tipados publicados uma vez e listados novamente por meio de uma única API.
- Qualquer domínio registra “o que aconteceu” sem conhecer seus leitores.

## Não objetivos

- Não é a fita de log bruta.
- Não são contadores ou agregados.
- Não é a execução do workflow em si.
## Limite de responsabilidade

Detém a criação, o armazenamento e a recuperação de eventos; não detém o processamento de negócio do lado do consumidor nem a execução de workflows.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/repositories/business/rp-events`