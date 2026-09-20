# rp-access

## Propósito

A camada de autorização compartilhada: cada `rp-*` pergunta aqui «este ator pode fazer isto?» em vez de inventar suas próprias verificações de permissão. Uma árvore de permissões, uma regra de avaliação, aplicada antes da execução de qualquer manipulador.

## Modelo mental

Duas perguntas, duas camadas: o acesso a métodos («pode chamar X?») é mantido na árvore de permissões e aplicado pelo guard; o acesso a objetos («quais linhas a chamada retorna?») é avaliado por entidade. Sem o primeiro, qualquer pessoa poderia chamar `deleteTopic`.

## Valor para o ecossistema

Raiz de confiança única para decisões:

- Árvore de permissões, predefinições, etiquetas e tokens emitidos ficam em um só lugar.
- Qualquer serviço verifica a mesma árvore em vez de criar suas próprias tabelas de políticas.

## Não objetivos

- Nem login nem emissão de sessão.
- Nem armazenamento de segredos.
## Limite de responsabilidade

Possui a avaliação de políticas de autorização e escopos de acesso; não possui verificação de identidade / login de autenticação.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `security`

## Fonte

`modules/repositories/sequrity/rp-access`