# rp-dumps

## Objetivo

A doca de exportação compartilhada: qualquer domínio captura seus dados aqui para migração,
backup ou transferência em vez de inventar seu próprio formato de dump. Snapshots
empacotados com metadados de recuperação.

## Modelo mental

O domínio solicita um dump (escopo, tempo) → o dump é gerado e empacotado →
os metadados de recuperação apontam para o artefato armazenado.
Geração e contabilidade vivem aqui; arquivamento de longo prazo vive em outro lugar.

## Valor para o ecossistema

Uma única história de exportação para a plataforma:

- Listagem de armazenamento, estatísticas, compactação e segmentos de dump por trás de uma API.
- Qualquer domínio torna-se exportável sem sua própria maquinaria de snapshot.

## Não objetivos

- Não é serviço de arquivos em tempo real.
- Não é um armazenamento de bytes paralelo.
## Limite de responsabilidade

Possui geração, empacotamento e metadados de recuperação de dumps; não possui
a plataforma de arquivamento de longo prazo.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- Não incluído em uma solução predefinida

## Fonte

`modules/repositories/data/rp-dumps`