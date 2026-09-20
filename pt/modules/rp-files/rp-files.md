# rp-files

## Propósito

A abstração única de arquivos do ecossistema: qualquer módulo que precise de
"arquivos" vem aqui em vez de criar sua própria tabela de nomes e caminhos.
Mantém metadados, coleções e listas de chunks; os bytes em si residem no
armazenamento em bloco, acessado por meio de um cliente de serviço de armazenamento.

## Modelo mental

Arquivo = registro (nome, extensão, coleção, proprietário) + lista ordenada de referências de chunks
 no armazenamento em bloco. Classificação (`detectType`), materialização
e persistência operam sobre metadados — os bytes só são carregados quando realmente necessários
(preparação de modelos, atendimento de downloads).

## Valor no ecossistema

O ponto de entrada da ingestão de arquivos:

- Arquivos, chunks, coleções e metadados por trás de uma única API; bytes de chunks delegados ao armazenamento em bloco.
- Qualquer domínio vincula um id de arquivo opaco à sua entidade em vez de copiar bytes.

## Não objetivos

- Não é armazenamento bruto em bloco — os bytes de chunks residem no block store.
- Não é descompactação de arquivos nem conversão de modelos.
## Limite de responsabilidade

Detém registros de arquivos, coleções e ciclo de vida das listas de chunks; não detém
detalhes de implementação do armazenamento de objetos nem transformações de bytes.

## Dependências diretas de módulos

- Nenhuma — os bytes de chunks passam por um cliente de serviço de armazenamento, que é uma chamada
  de transporte como a que qualquer consumidor externo faz, não uma ligação de módulo para módulo.
  rp-files mantém nomes, coleções e a lista de chunks; não armazena dados.

## Participação na solução

- `requests`

## Fonte

`modules/repositories/data/rp-files`