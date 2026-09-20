# lm-ses

## Finalidade

Perna SES da distribuição compartilhada de notificações: transporte de e-mail AWS por trás do contrato rp-notify.

## Valor para o ecossistema

E-mails em massa e transacionais (convites para avaliação, atualizações de pedidos, convites de equipe) fluem por meio de uma integração SES. As credenciais são resolvidas via lm-secrets.

## Não objetivos

Sem política de canal ou modelos — isso é do rp-notify e do domínio chamador.


## Limite de responsabilidade

Detém a integração de envio e o mapeamento específicos do SES; não detém o domínio de criação de modelos de e-mail.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/lambdas/providers/lm-ses`