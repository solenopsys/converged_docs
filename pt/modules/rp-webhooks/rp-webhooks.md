# rp-webhooks

## Objetivo

A única porta de entrada para o mundo exterior: os sistemas externos chamam um
endpoint de webhook, e este módulo valida, normaliza e distribui os eventos
para dentro. Nenhum domínio expõe seu próprio esquema de URL de callback.

## Modelo mental

POST do sistema externo → o webhook valida a assinatura e a estrutura → normalizado
o evento é registrado como uma entrega e roteado para o tópico configurado.
As tentativas de entrega e a validação ficam aqui; a reação de negócio ocorre
a jusante.

## Valor para o ecossistema

Uma única entrada para callbacks externos:

- Configurações de endpoints e registros de entrega por trás de uma única API.
- Qualquer sistema externo obtém o mesmo formato de endpoint em vez de uma infraestrutura por integração.

## Não objetivos

- Não é execução de fluxo de trabalho.
- Não é publicação de eventos nem envio de notificações.
## Limite de responsabilidade

Responsável pelo transporte de webhooks, validação e tentativas de entrega; não é responsável
pelo processamento de negócio do sistema de destino.

## Dependências diretas de módulos

- Nenhuma

## Participação em soluções

- Não incluído em uma solução predefinida

## Origem

`modules/repositories/automation/rp-webhooks`