# lm-modelconvertor

## Objetivo

A ponte compartilhada de formatos de modelo: converte modelos de produção entre representações internas e externas (p. ex., para prévias GLB) para que nenhum fluxo de trabalho vincule diretamente uma biblioteca conversora nativa.

## Modelo mental

O fluxo de trabalho prepara os bytes do modelo → o conversor transforma o formato → retorna bytes de prévia/convertidos como refs de cache para `rp-files.persist`. Transformação pura: sem armazenamento, sem estimativas, sem decisões de negócio.

## Valor para o ecossistema

Um ponto único de conversão para modelos de produção:

- Um arquivo preparado na entrada, saídas convertidas como refs de cache na saída — mesmo formato para qualquer chamador.
- Novos formatos e versões do conversor chegam uma vez e atualizam cada caminho de análise.
- Mantém dependências nativas pesadas fora de fluxos de trabalho e repositórios.

## Não objetivos

- Não é armazenamento de arquivos nem orquestração de ingestão.
- Não é renderização de prévias nem estimativas de fatiamento.

## Limite de responsabilidade

Possui rotinas de conversão/transformação; não possui treinamento de modelos a montante, serving a jusante ou persistência.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/lambdas/convertors/lm-modelconvertor`