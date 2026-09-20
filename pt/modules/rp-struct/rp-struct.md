# rp-struct

## Objetivo

O construtor de estruturas compartilhado: transforma conteúdo solto em representações tipadas, moldadas por esquema,
nas quais cada consumidor pode confiar. Um ponto único de modelagem entre o conteúdo bruto
e a renderização de canal.

## Modelo mental

Conteúdo bruto de entrada → a modelagem de estrutura aplica esquemas e formas → blocos tipados
de saída. Os canais (`sf-*`, markdown, modelos de notificação) renderizam blocos
sem reanalisar a origem.

## Valor para o ecossistema

Uma prateleira JSON sem tipo:

- Documentos JSON por trás de uma única API de arquivos.
- Qualquer produtor armazena blobs estruturados sem manipulação própria de arquivos.

## Não objetivos

- Sem taxonomia ou rotulagem.
- Sem renderização de markdown.
## Limite de responsabilidade

Responsável pela modelagem de estrutura e pela modelagem em nível de esquema; não responsável pela renderização final
específica do canal.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `content`

## Fonte

`modules/repositories/content/rp-struct`