# lm-smtp

## Objetivo

Ramo SMTP da distribuição compartilhada de notificações: transporte de provedor simples por trás do contrato rp-notify.

## Valor do ecossistema

O domínio emite uma intenção de notificação uma vez via rp-notify → este adaptador entrega via SMTP. Trocar ou adicionar provedores de e-mail nunca afeta os domínios.

## Não objetivos

Sem política de canal, novas tentativas ou modelos — isso cabe ao rp-notify e ao domínio chamador.


## Limite de responsabilidade

Possui o transporte SMTP e o tratamento de entrega em nível de protocolo; não possui a orquestração de notificações de alto nível.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/lambdas/providers/lm-smtp`