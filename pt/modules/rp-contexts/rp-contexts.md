# rp-contexts

## Objetivo

O repositório compartilhado de contextos nomeados para IA: prompts, variantes de idioma e
conhecimento de domínio ficam aqui em vez de serem codificados em cada fluxo de trabalho.
Versionado por nome, resolvido por idioma.

## Modelo mental

O fluxo de trabalho ou assistente solicita um contexto por nome (+ idioma) → recebe o
texto atual. Os editores atualizam os contextos sem reimplantar os consumidores.
Armazenamento e recuperação ficam aqui; a engenharia de prompts cabe aos editores.

## Valor para o ecossistema

Uma prateleira de conhecimento para caminhos de IA:

- Contextos nomeados com variantes de idioma por trás de uma API.
- Qualquer caminho de IA resolve o mesmo contexto nomeado em vez de suas próprias cópias de prompts.

## Não objetivos

- Não é histórico de chat nem threads de diálogo.
- Não é execução de prompts — apenas textos de contexto armazenados.
## Limite de responsabilidade

Possui armazenamento e recuperação de contextos de IA nomeados e variantes de idioma;
não possui infraestrutura de provedor de modelos nem comportamento de diálogo.

## Dependências diretas de módulo

- Nenhuma

## Participação na solução

- `ai`

## Fonte

`modules/repositories/ai/rp-contexts`