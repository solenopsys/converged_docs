# rp-threads

## Propósito

A camada conversacional única do ecossistema: qualquer módulo onde pessoas
ou agentes trocam mensagens não guarda mensagens próprias — mantém um
`threadId`, e o diálogo em si vive aqui.

## Modelo mental

A entidade (sala de chat, tópico de fórum, chamada, solicitação) armazena apenas um `threadId`.
Todas as mensagens, ordenação e contexto vivem no thread. Criar uma entidade
= gerar um `threadId` e entregá-lo ao chamador, que o registra.

## Valor para o ecossistema

Um formato de diálogo em toda parte:

- Threads e mensagens ordenadas por trás de uma única API, identificadas por thread id opaco.
- Qualquer entidade anexa uma discussão sem suas próprias tabelas de mensagens.

## Não objetivos

- Não são salas de chat nem tópicos de fórum — apenas os threads de mensagens por trás deles.
- Não é entrega de notificações nem resumos de diálogos.
## Limite de responsabilidade

Detém o ciclo de vida de threads, a ordenação de mensagens e metadados em nível de thread; não
detém salas/tópicos, associação, nem gateways de transporte para
email/SMS/push.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `ai`

## Fonte

`modules/repositories/communications/rp-threads`