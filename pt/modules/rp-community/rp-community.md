# rp-community

## Objetivo

Estrutura e propriedade do fórum: seções, tópicos, quem os escreveu e quem pode vê-los. A discussão sob um tópico não fica aqui — um tópico carrega um `threadId` e as mensagens ficam em `rp-threads`.

## Limite de responsabilidade

É responsável por seções e tópicos. Não chama `rp-threads` nem qualquer outro repositório: `createTopic` gera um `threadId` e o devolve, e o chamador registra a thread e escreve a própria publicação inicial.

## Identidade e autoria

`createdBy` nunca é aceito de um chamador. Ele é lido do token verificado por meio de `getCurrentWorkspaceContext()`, que `messaging-backend` prefere a qualquer informação declarada pelo envelope. Os IDs de tópicos e threads são gerados aqui pelo mesmo motivo — um ID que um cliente pode escolher é um ID que ele pode roubar, e a tabela de tags de acesso não registra nenhum tipo de objeto para detectar a colisão.

## Visibilidade

Seções e tópicos carregam uma coluna `visibility` (`public` | `authenticated` | `private` | `tagged`), e um novo tópico herda o valor de sua seção, a menos que solicite algo mais restritivo. As tags por trás de `tagged` pertencem à relação compartilhada `access_tags` descrita em `access-control.md`; essa parte ainda não foi implementada, portanto, atualmente `visibility` é registrada, mas não é aplicada.

## Bloqueio

`touchTopicActivity` é o único lugar onde um bloqueio pode ser aplicado: `rp-threads` aceita uma mensagem sem saber que os tópicos existem, então uma tela chama isso após a publicação e trata uma recusa como uma publicação malsucedida.

## Dependências diretas do módulo

- `back-core`, `nrpc`, `g-community`

## Participação na solução

- `communications`

## Fonte

`modules/repositories/communications/rp-community`
