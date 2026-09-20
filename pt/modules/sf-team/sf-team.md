# sf-team

## Objetivo

A equipe como uma única área de trabalho: quem trabalha aqui, o que cada pessoa pode fazer e quem foi convidado, mas ainda não chegou.

## Projeções

Quatro visualizações `setOf`, que o shell transforma nos botões permanentes da aba
— **Equipe**, **Convites**, **Agenda**, **Direitos** — além de uma visualização
`objectOf`, o cartão da pessoa, que é aberta como uma subaba *dentro* da mesma área. Sem
nada selecionado, a área mostra sua própria tela (`team.statistic` resolvida por meio de
sua visualização `setOf`, o padrão usado por `sf-logs` e `sf-equipment`).

## O que molda esta superfície

**O console não pode conceder nada.** `rp-access` é `@Access("internal")` e
o runtime rejeita um JWT de usuário antes que qualquer permissão seja verificada
(`messaging-access.ts:176`). Portanto, toda operação que altera o que alguém pode
fazer executa `wf-team-invite` no centimanus, que mantém o token de serviço do cluster.
Quem pode executá-la é a concessão comum `wf/workflows/wf-team-invite.js(x)`, que
fica em um único arquivo de predefinições — essa concessão é a totalidade de "quem pode adicionar pessoas".

Três métodos de convite em `rp-identity` carregam um `@Access("user")` no nível do método,
para que a coluna de entrega possa ser lida sem um workflow a cada atualização da tabela; eles
são controlados por `rp/identity/listInvites(r)` nas predefinições do proprietário e do gerente.

A projeção **Direitos** é composta no navegador a partir da lista de membros e dos
convites, porque o serviço que conhece a resposta real não pode ser consultado a partir
daqui. Ela mostra a intenção registrada — a função atribuída a uma pessoa e as tags
que vieram com ela —, não uma leitura do token ativo dessa pessoa.

## Operações

`team.member.import` (a operação para a qual este contorno existe — uma lista colada,
com uma tabela preenchida exatamente com essas pessoas), `team.member.create`,
`team.member.save`, `team.member.setRole`, `team.member.deactivate`,
`team.invite.revoke`, `team.shift.create`.

Três delas são publicadas no catálogo de chat em `llm.json`.

## Dependências diretas do módulo

- `front-core`, `g-centimanus`, `g-identity`, `g-staff`

## Participação na solução

- `production`

## Fonte

`modules/surfaces/sequrity/sf-team`
