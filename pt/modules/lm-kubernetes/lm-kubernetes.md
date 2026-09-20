# lm-kubernetes

## Objetivo

Ponte de operador Kubernetes sem estado: aplica intenções de automação da plataforma a recursos do cluster (deployments, jobs) por meio de um cliente dedicado. Sem estado persistente; segredos resolvidos via lm-secrets.

## Limite de responsabilidade

Responsável pela tradução da API do cluster e leituras de aplicação/status; não responsável pela orquestração de fluxos de trabalho, agendamento ou armazenamento de segredos.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/lambdas/automation/lm-kubernetes`