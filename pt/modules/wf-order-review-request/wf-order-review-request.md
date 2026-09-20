# wf-order-review-request

## Objetivo

Contorno 2 do sistema de avaliações: perguntar ao cliente, uma vez, depois que o trabalho estiver concluído.

Uma execução encontra um pedido que foi concluído há tempo suficiente, tem um cliente para quem escrever
e que nunca foi contatado; cria seu link pessoal de uso único para avaliação em
`rp-reviews`; e envia a solicitação por meio de `lm-ses`.

## Por que isto é um workflow

A pergunta "quais pedidos concluídos ainda não foram contatados?" abrange dois serviços
que são proibidos de conhecer um ao outro: `rp-orders` não sabe o que é uma
avaliação, e `rp-reviews` mantém `orderId` como uma string opaca. Colocar as duas
listas lado a lado é exatamente para isso que serve um fluxo — e `rt.node` é o que faz
a criação do link sobreviver a uma reinicialização sem criar um segundo link.

## Estrutura

```
read-settings → list-finished (completed, updatedAt ≤ now − delay)
              → list-invites (which of those were already asked)
              → create-invite → send-email → mark-sent | mark-failed
```

Um e-mail por execução, para que um endereço bloqueado nunca impeça a fila atrás dele e o
agendamento determine a taxa. `dryRun` renderiza o e-mail e não cria nada: um
ensaio que deixasse um link ativo para trás faria a próxima execução real ignorar esse
pedido por já ter sido contatado.

Um e-mail recusado retorna de `lm-ses` como `{ success: false }`, não como uma exceção,
portanto é um branch comum que marca o convite como `failed` — não um limite
de erro.

## Parâmetros

- `from` (obrigatório) — endereço do remetente.
- `ses` (obrigatório) — `SesCredentials`.
- `shopName` — preenchido em `{{shopName}}` nos templates.
- `delayHours` — substitui `ReviewSettings.requestDelayHours` para uma recuperação.
- `dryRun` — renderiza e encerra.

O assunto, o corpo, a base do link e o atraso vêm de `reviews.getSettings()`, para que a
loja altere seu próprio texto sem tocar neste fluxo.

## Dependências diretas do módulo

- `g-orders`
- `g-reviews`
- `g-ses`

## Código-fonte

`modules/workflows/wf-order-review-request`
