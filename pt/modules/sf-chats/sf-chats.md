# sf-chats

## Objetivo

Salas de bate-papo, como três abas separadas: a lista de salas, a conversa de uma sala e
os membros de uma sala. Gerenciar quem está em uma sala e ler o que disseram são
duas tarefas e, portanto, duas abas.

## Limite de responsabilidade

É responsável pela navegação das salas, pela tela de conversa e pela edição dos membros. As mensagens
pertencem a `rp-threads`, lidas diretamente pelo navegador; os arquivos pertencem a
`rp-files` por meio de uma mensagem `link`.

## Como uma sala é criada

`createRoom` em `rp-chats` gera o id da sala e o id da thread e registra o
criador do token como `owner`; esta superfície então registra a thread em
`rp-threads`. `rp-chats` nunca chama outro repositório.

## Atualizações em tempo real

Uma nova mensagem é publicada para cada membro nominalmente por meio do `pushrouter` do Fujin,
nunca para todo o tenant: a existência de uma sala privada não é pública, mesmo quando
seu conteúdo permanece protegido pelo predicado de leitura. O push transporta apenas identificadores.

## Dependências diretas do módulo

- `effector`, `front-core`, `g-chats`, `g-threads`, `signal-channel`, `threads-state`

## Associação à solução

- `communications`

## Fonte

`modules/surfaces/communications/sf-chats`
