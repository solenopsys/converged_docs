# wf-order-review-followup

## Objetivo

A única cobrança. Cada execução pega um link de avaliação que foi enviado, ficou
sem resposta pelo número configurado de dias e ainda não recebeu o número máximo
de cobranças permitido, e faz mais uma tentativa.

## Por que isto é um workflow

A escolha não é: `reviews.findInvitesToFollowUp` é uma consulta sobre convites
e pertence a `rp-reviews`. O que este fluxo acrescenta é o nome do pedido para
o e-mail e o envio — dois serviços em um único processo, que é a definição de
um workflow aqui.

## O que ele deliberadamente nunca faz

Ele nunca cobra alguém que abriu o formulário. A pessoa leu o pedido e escolheu
não escrever; perguntar novamente é como uma solicitação de avaliação se torna
spam. Essa condição fica na consulta do repositório, e não neste fluxo, para que
um futuro chamador não possa esquecê-la.

Uma cobrança recusada deixa o convite como `sent`, em vez de `failed`: o primeiro
e-mail foi enviado, e o cliente ainda pode respondê-lo.

## Estrutura

```
read-settings → find-due (sent, nunca aberto, dentro do limite)
              → read-order (somente para o nome)
              → send-email → count-followup
```

Contar a cobrança é o que a torna *única*: a mesma consulta não retornará esse
link novamente. `dryRun` renderiza o e-mail e não contabiliza nada. `maxFollowups: 0`
desativa completamente as cobranças, e o fluxo para antes de fazer a solicitação.

## Parâmetros

- `from` (obrigatório) — endereço do remetente.
- `ses` (obrigatório) — `SesCredentials`.
- `shopName`, `delayDays`, `maxFollowups`, `dryRun` — substituições; os valores
  padrão vêm de `reviews.getSettings()`.

## Dependências diretas do módulo

- `g-orders`
- `g-reviews`
- `g-ses`

## Código-fonte

`modules/workflows/wf-order-review-followup`
