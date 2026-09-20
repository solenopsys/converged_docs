# rp-identity

## Propósito

O registro de perfis compartilhado: um registro de identidade por pessoa ou conta de serviço,
vinculado a partir de cada domínio. Pedidos, chats, cartões de funcionários — todos apontam
para o mesmo perfil em vez de copiar nomes e atributos.

## Modelo mental

Identidade = registro estável (id, atributos principais, estado do ciclo de vida). Os domínios
armazenam o id de identidade e leem os atributos sob demanda; nunca bifurcam o
perfil. A autenticação comprova a identidade, o acesso a verifica, os domínios a referenciam.

## Valor para o ecossistema

Um “quem” para a plataforma:

- Registros de usuários, vínculos de métodos de autenticação e convites em um só lugar.
- Qualquer domínio armazena um id de usuário opaco e lê os atributos sob demanda em vez de bifurcar perfis.

## Não objetivos

- Não é login nem sessões.
- Não são permissões.
- Não é estrutura organizacional nem semântica de pessoal.
## Limite de responsabilidade

Possui os registros de identidade e o estado do ciclo de vida da identidade; não possui
políticas de permissão detalhadas nem fluxos de autenticação.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `security`

## Fonte

`modules/repositories/sequrity/rp-identity`