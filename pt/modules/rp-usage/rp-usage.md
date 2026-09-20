# rp-usage

## Objetivo

O medidor de consumo compartilhado: qualquer funcionalidade informa aqui "quanto foi usado"
em vez de rastrear cotas localmente. Agregado por consumidor e período —
a fonte da qual faturamento e limites leem.

## Modelo mental

A funcionalidade registra o consumo (quem, o quê, quanto, período) → o uso
o agrega por conta/período. O faturamento a jusante transforma agregados em dinheiro;
as verificações de limite leem os totais atuais. A medição vive aqui, a precificação vive
a jusante.

## Valor do ecossistema

Um log de eventos de uso:

- Qualquer funcionalidade registra linhas (função, usuário, data) da mesma forma.
- Links solução-função permitem que qualquer relatório agrupe chamadas por solução sem tabelas de cota por módulo.

## Não objetivos

- Sem faturamento ou execução de pagamento.
- Sem autenticação ou verificações de permissão.
- Sem contadores brutos para painéis.
## Limite de responsabilidade

Detém a medição e agregação de uso; não detém faturamento, execução de pagamento
ou política de preços.

## Dependências diretas de módulos

- Nenhuma

## Participação em soluções

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-usage`