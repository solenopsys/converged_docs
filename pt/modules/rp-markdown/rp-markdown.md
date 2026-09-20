# rp-markdown

## Objetivo

O pipeline Markdown compartilhado: análise, transformação e renderização para
cada módulo que lida com conteúdo de texto. Um único comportamento de analisador em vez
de variantes por superfície.

## Modelo mental

Fonte Markdown de entrada → analisar/transformar → saída renderizada (HTML, blocos).
Os autores de conteúdo escrevem uma vez; docs, chats, landings e notificações renderizam
a mesma fonte de forma consistente.

## Valor para o ecossistema

Espinha dorsal de texto única:

- Arquivos Markdown mais conversão JSON por trás de uma única API.
- Qualquer produtor armazena texto humano da mesma forma em vez de seu próprio manuseio de arquivos.

## Não objetivos

- Não é armazenamento de blocos tipados.
- Não é renderização HTML.
## Limite de responsabilidade

Detém o comportamento de conversão/análise Markdown; não detém transcodificação
de mídia rica nem composição de páginas.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `content`

## Fonte

`modules/repositories/content/rp-markdown`