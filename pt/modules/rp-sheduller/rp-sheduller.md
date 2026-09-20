# rp-sheduller

## Finalidade

O gatilho de tempo compartilhado: agendamentos cron e seu histórico de execução para
todo o ecossistema. Qualquer trabalho recorrente registra-se aqui em vez de executar
seu próprio loop de temporizador.

## Modelo mental

O operador define uma entrada cron (qual workflow, quando, com quais args) → o
runtime dispara conforme agendado → o histórico registra o que foi executado e como terminou.
Este módulo armazena e lista entradas; nunca executa nada por si só.

## Valor para o ecossistema

Um único relógio para trabalhos recorrentes:

- Linhas cron, histórico de execuções e estatísticas por trás de uma API.
- Qualquer trabalho recorrente precisa apenas de uma linha cron — sem nova infraestrutura de temporizadores.

## Não objetivos

- Não é definição nem execução de workflows.
- Não são gatilhos únicos — apenas agendamentos recorrentes.
## Limite de responsabilidade

Possui CRUD/lista/estatísticas para entradas cron e registros de histórico; não executa
workflows, temporizadores, tentativas nem distribuição em segundo plano.

## Dependências diretas de módulos

- Nenhuma

## Participação em soluções

- Não incluído em uma solução predefinida

## Fonte

`modules/repositories/automation/rp-sheduller`