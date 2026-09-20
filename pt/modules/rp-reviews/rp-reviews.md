# rp-reviews

## Objetivo

O sistema de avaliações da loja, em três tabelas que respondem a três perguntas diferentes.

- `reviews` — o que um cliente disse, o que a loja respondeu e se isso está
  no site. A moderação acontece aqui: uma avaliação que veio de fora nasce como
  `pending` e fica visível apenas dentro do console até que alguém a publique.
- `review_invites` — um link pessoal e de uso único por pedido, e o que aconteceu
  com ele: enviado, aberto, respondido, expirado. Este é o funil que a loja acompanha.
- `review_settings` — uma linha de JSON: as plataformas externas, o limite, os
  modelos de e-mail, os atrasos e a permissão para enviar lembretes.

## Limite de responsabilidade

É responsável pelas avaliações, convites e configurações do funil. Não sabe nada
sobre pedidos: `Review.orderId` e `ReviewInvite.orderId` são strings opacas, e associá-las
a pedidos reais é responsabilidade de `wf-order-review-request` (que faz a solicitação) e
`sf-reviews` (que exibe). Não é responsável por conversas da comunidade.

## Duas portas

O acesso é feito por tag, como em todo lugar: uma avaliação publicada carrega `public`, qualquer outra
carrega `authenticated` mais `moderator`, o que permite que a loja aja
sobre uma avaliação que ninguém da loja escreveu.

A porta do cliente é diferente. `getInviteByToken`, `markInviteOpened` e
`submitByToken` são autorizados pelo próprio token — uma capacidade, não uma
sessão — para que o formulário público funcione sem nenhum login. Eles retornam uma
visão restrita que não contém nem o contato nem o id do convite, e
`submitByToken` consome o link condicionalmente, para que duas submissões do mesmo e-mail produzam
uma avaliação e uma recusa, em vez de duas avaliações.

## Controle das avaliações

`positiveThreshold` altera a *ênfase* do formulário público e nada mais:
no limite ou acima dele, o autor recebe primeiro as plataformas externas; abaixo dele, recebe
primeiro um contato com a loja. Os links das plataformas continuam visíveis de qualquer forma,
porque mostrar o caminho para uma avaliação pública apenas a clientes satisfeitos é algo que o Google
e várias outras plataformas proíbem. O comportamento seguro é o padrão.

## Dependências diretas do módulo

- Nenhuma

## Participação na solução

- `production`

## Origem

`modules/repositories/business/rp-reviews`
