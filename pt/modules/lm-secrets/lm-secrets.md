# lm-secrets

## Propósito

O adaptador compartilhado de cofre de segredos: valores de segredos nomeados para toda a
plataforma por trás de um único contrato. Os serviços leem aqui os segredos de configuração em vez de
env-sprawl ou clientes de cofre por módulo.

## Modelo mental

O serviço pergunta pelo nome do segredo → obtém o valor. A rotação acontece em um
lugar e se propaga para cada consumidor. Os detalhes do backend de armazenamento ficam atrás do
contrato.

## Valor do ecossistema

Uma única porta de cofre para todos:

- Credenciais de provedores, tokens de integração, segredos OAuth — mesma forma get/set/delete.
- Qualquer consumidor mantém os segredos fora do código e da configuração; a rotação acontece em um só lugar.
- Novas integrações não precisam de nova infraestrutura de segredos.

## Não objetivos

- Não é autenticação nem verificações de permissão.
- Não são registros de identidade de usuário.
## Limite de responsabilidade

Responsável por armazenar, recuperar e excluir valores de segredos nomeados; não responsável por
identidade, permissões ou lógica de sessão.

## Dependências diretas de módulos

- Nenhuma

## Participação em soluções

- Não incluído em uma solução predefinida

## Fonte

`modules/lambdas/sequrity/lm-secrets`