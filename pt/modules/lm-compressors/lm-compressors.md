# lm-compressors

## Propósito

O cavalo de batalha de bytes compartilhado do pipeline de arquivos: montagem, descompressão,
análise de ZIP, fragmentação de saída e staging. Sem estado — sem clientes `files` ou
`store` internos; retorna bytes e referências de cache, a persistência
é tarefa do workflow.

## Modelo mental

O workflow entrega refs de chunks + operação (desempacotar, montar, fragmentar) → lambda
faz trabalho puro de bytes → devolve bytes em staging/refs de cache. Nunca decide
o que um arquivo significa e nunca armazena nada.

## Valor para o ecossistema

Um único lugar onde os bytes de arquivo são tocados:

- Chunks comprimidos entram, entradas em staging saem — um único formato de desempacotamento para qualquer chamador.
- Qualquer futuro formato de arquivo ou compressão chega aqui uma vez e atualiza todas as ingestões de uma só vez.

## Não objetivos

- Não é armazenamento nem classificação de arquivos.
- Não é conversão de modelos nem renderização de visualizações.
## Limite de responsabilidade

Possui montagem de bytes, descompressão, análise de arquivos, fragmentação de saída e
staging; não possui registros de arquivos nem persistência.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `requests`

## Fonte

`modules/lambdas/data/lm-compressors`