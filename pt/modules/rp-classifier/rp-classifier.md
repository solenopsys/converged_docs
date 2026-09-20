# rp-classifier

## Objetivo

O serviço compartilhado de rotulagem: qualquer ingestão direciona conteúdo bruto para cá e recebe
de volta categorias, rótulos ou intenções. Uma única lógica de classificação em vez de
cadeias de if por domínio.

## Modelo mental

O produtor envia itens brutos (arquivos, textos, solicitações) → o classificador atribui
rótulos → o chamador roteia por rótulo (modelo de produção vs desenho, urgente
vs ruído). Os rótulos são recomendações; a decisão de negócio permanece com o chamador.

## Valor do ecossistema

Uma única prateleira de taxonomia:

- Nós de árvore e mapeamentos de chaves por trás de uma única API.
- Qualquer ingestão resolve rótulos a partir da mesma árvore em vez de seus próprios dicionários.

## Não objetivos

- Sem bytes de arquivo ou conversão.
- Sem armazenamento de documentos JSON.
## Limite de responsabilidade

Detém a lógica de classificação e a atribuição de rótulos; não detém pipelines de ingestão de conteúdo de origem nem roteamento de negócio posterior.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/repositories/content/rp-classifier`