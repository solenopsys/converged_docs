# Automação

## Objetivo

É responsável pelo espaço de trabalho de automação: fluxos de trabalho e suas
execuções, os gatilhos do barramento que os iniciam, agendamentos recorrentes
e endpoints de webhook de entrada.

## Limite de responsabilidade

Controla a experiência do espaço de trabalho. Não executa fluxos de trabalho,
não mantém agendamentos nem entrega webhooks — inicia uma execução por meio do
runtime e lê o log de volta do rp-dag.

## A seção DAG

- **Fluxos de trabalho** — o catálogo publicado pela Solution ativa, somente para leitura.
  Abrir um fluxo significa pedir para executá-lo: os parâmetros são tipados como JSON e
  enviados para `centimanus.runWorkflow`.
- **Execuções** — cada execução, com seu status.
- **Detalhes da execução** — a árvore do que a execução fez. Uma linha por nó: quão
  profundo ele está, se foi concluído e quanto tempo levou. Expandir um nó mostra as
  chamadas de serviço que ele fez e o que retornou. Um nó que delegou por meio de
  `rt.sub` é seguido pelos nós da execução para a qual ele delegou, um nível abaixo.
  Uma execução que ainda está em andamento é atualizada automaticamente.
- **Gatilhos** — "quando este tópico do barramento aparecer, execute aquele fluxo de
  trabalho". Tópico, fluxo de trabalho, parâmetros JSON, ativado/desativado.
- **Variáveis** — estado do fluxo de trabalho escrito por `rt.set`.

Os parâmetros são tipados como JSON em todos os lugares, em vez de serem gerados em
um formulário: os parâmetros de um fluxo de trabalho pertencem a ele e mudam com ele,
portanto um campo de texto continua correto quando eles mudam, e o que é digitado é o
que o fluxo de trabalho recebe.

## Dependências diretas do módulo

- Nenhuma

## Participação em soluções

- Não incluído em uma solução predefinida

## Origem

`modules/surfaces/automation/sf-automation`
