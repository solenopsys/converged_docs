# rp-chats

## Objetivo

Salas de chat, sua associação e seus contextos por sala. A conversa em si
não está aqui: uma sala contém um `threadId` e as mensagens ficam em
`rp-threads`.

## Limite de responsabilidade

É responsável por salas, funções e contextos. Não chama nenhum outro repositório — `createRoom` gera o
`threadId` e o retorna, e o chamador registra a thread.

## Identidade e acesso

O chamador vem do token verificado, nunca de um parâmetro. Duas
consequências que vale mencionar:

- `listRooms` é restrito ao chamador dentro da consulta, portanto substituir o id de outro
  usuário não lê mais as salas dele, e `totalCount` não pode revelar o número
  de salas que ocultou;
- qualquer operação que enderece uma sala por id verifica primeiro a associação.

`chart_room_users` permanece mesmo após a chegada de `access_tags`: uma tag expressa
associação, mas não diferencia `owner` de `admin` ou `member`.

## Observação sobre os nomes das tabelas

As tabelas são grafadas como `chart_rooms` / `chart_room_users`. O erro de digitação é
consistente entre migrações, entidades e consultas, portanto o código funciona; renomear
é uma migração, não uma edição.

## Dependências diretas do módulo

- `back-core`, `nrpc`, `g-chats`

## Associação à solução

- `communications`

## Origem

`modules/repositories/communications/rp-chats`
