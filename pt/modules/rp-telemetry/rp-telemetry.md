# rp-telemetry

## Objetivo

O feed técnico compartilhado de saúde: os serviços relatam “como estão” (latência, erros, sinais de recursos) aqui em vez de cada ferramenta de ops coletá-los individualmente. Ingestão normalizada, uma única superfície de consulta para saúde.

## Modelo mental

O serviço envia eventos de saúde (origem, sinal, tempo, payload) → a telemetria os normaliza em uma forma uniforme. Os consumidores de ops (dashboards, fluxos de incidentes) leem a saúde por serviço ao longo do tempo. O significado de negócio é atribuído pelo leitor, não pelo armazenamento.

## Valor para o ecossistema

Um diário de amostras numéricas:

- Qualquer produtor grava linhas (dispositivo, parâmetro, valor, unidade, tempo) em armazenamentos hot/cold.
- Uma linha do tempo para números de qualquer origem — sensores de equipamentos ou qualquer outra coisa.

## Não objetivos

- Não é armazenamento de logs de texto.
- Não são registros de uso.
- Não é política de alertas nem resolução de incidentes.
## Limite de responsabilidade

Responsável pela ingestão e normalização de eventos de telemetria; não responsável por definições de analytics de produto, alertas ou remediação.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-telemetry`