# rp-logs

## Propósito

O diário único somente de acréscimo do ecossistema: qualquer serviço, equipamento
ou fluxo de trabalho escreve aqui «o que aconteceu» em vez de criar seu próprio armazenamento
de logs. Escritas baratas, leituras por tempo/fonte.

## Modelo mental

O produtor envia um evento (tempo, fonte, nível, texto/payload) → ele chega ao
fluxo compartilhado. O consumidor lê uma fatia por fonte ou intervalo. Sem
agregação ou alertas internos — apenas o registro do fato.

## Valor para o ecossistema

Um fluxo reutilizado por todos:

- Serviços: logs operacionais sem armazenamento próprio por `rp-*`.
- Equipamentos: logs de máquinas/dispositivos — mesma API, fonte diferente, de impressoras 3D
  a qualquer módulo ou sistema externo.
- Qualquer produtor escreve «o que aconteceu» em um só lugar em vez de criar
  seu próprio armazenamento de logs; auditoria e revisão leem uma única linha do tempo.

## Não objetivos

- Sem contadores ou agregados.
- Sem amostras numéricas ou registros de uso.
- Sem rastreamento de chamadas distribuídas ou alertas.
## Limite de responsabilidade

Possui as APIs de ingestão e recuperação de logs; não possui métricas de negócio,
agregação, alertas ou estratégia de rastreamento.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-logs`