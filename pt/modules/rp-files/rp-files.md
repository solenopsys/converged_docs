# rp-files

## Objetivo

Fornece APIs de metadados de arquivos e fluxos de trabalho de gerenciamento de arquivos.

## Limite de responsabilidade

É responsável pelos registros de arquivos e pelas operações no nível de arquivo; não é responsável pelos detalhes de implementação do armazenamento de objetos.

## Dependências diretas do módulo

- `rp-store` — o armazenamento de blocos endereçado por conteúdo onde os bytes de cada arquivo residem.
  rp-files mantém os nomes, as coleções e a lista de partes; não armazena dados.

## Participação na solução

- `requests`

## Origem

`modules/repositories/data/rp-files`
