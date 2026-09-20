# rp-requests

## Finalidade

Recepção e ciclo de vida de solicitações de serviço: envio, transições de status, anexos de arquivo (por fileId) e promoção a pedidos via wf-request-to-order. A análise é executada por meio de wf-request-analyze.

## Limite de responsabilidade

Detém o ciclo de vida da solicitação e as transições de status; não detém o transporte de mensagens, os bytes de arquivo nem a execução da análise.

## Dependências diretas de módulo

- Nenhuma

## Participação na solução

- `requests`

## Fonte

`modules/repositories/business/rp-requests`