# rp-auth

## Objetivo

A porta de entrada única para provar “quem você é”: sessões, credenciais e
emissão de tokens para todo o ecossistema. Nenhum domínio executa seu próprio login.

## Modelo mental

O usuário apresenta credenciais → auth valida e emite uma sessão/token →
cada chamada subsequente o transporta e a camada de acesso decide o que ele pode fazer.
O login prova a identidade; as permissões são uma camada separada.

## Valor para o ecossistema

Um backend de login para todas as superfícies:

- Magic links, sessões de atualização e registros de clientes OAuth em um só lugar.
- Qualquer frontend autentica os usuários da mesma forma em vez de usar suas próprias tabelas de sessão.

## Não objetivos

- Não políticas de permissão.
- Não registros de perfil de usuário.

## Limite de responsabilidade

Possui os fluxos de autenticação e a lógica de emissão de tokens/sessão; não possui
adaptadores de provedores OAuth de terceiros nem avaliação de políticas de autorização.

## Dependências diretas de módulos

- Nenhuma

## Associação à solução

- `security`

## Fonte

`modules/repositories/sequrity/rp-auth`