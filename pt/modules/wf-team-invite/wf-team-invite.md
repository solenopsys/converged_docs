# wf-team-invite

## Objetivo

Transforma uma lista colada de pessoas — "nome + endereço", em qualquer formato que um ser
humano tenha escrito — em contas de usuário, funções, cartões de equipe e convites, e envia
a cada pessoa o link que permite fazer login.

Isso existe porque quatro serviços precisam avançar juntos para uma linha dessa lista
(`rp-identity`, `rp-access`, `rp-staff`, `rp-auth`, além de uma lambda de e-mail) e
os microsserviços não chamam uns aos outros.

## Por que também é o limite de privilégios

`rp-access` recusa diretamente um JWT de usuário (`@Access("internal")`), então nenhuma superfície
pode conceder uma função. centimanus executa este script com `SERVICE_TOKEN`, e quem
pode executá-lo recebe uma concessão comum — `wf/workflows/wf-team-invite.js(x)` — verificada
na borda (`signal_provider.zig:146`) e registrada em um único arquivo de predefinições. É por isso que
o produto não tem o conceito de "administrador".

O script não consegue ver quem o chamou, então a proteção contra escalação é uma lista fixa:
`manager`, `operator`, `viewer`. `owner` e `root` não podem ser concedidos aqui.

## Estrutura

1. fontes de texto — `files.materialize` + `files.extractText`, além de `rawText`;
2. pessoas — primeiro `rt.llm`, e uma expressão regular linha a linha como alternativa;
3. um `rt.attempt` por pessoa — usuário, predefinição base + função, tags de grupo, cartão,
   convite;
4. a mensagem — sua própria tentativa, para que um relay recusado seja um ramo e não uma conta
   perdida;
5. o relatório, cujos `staffIds` a superfície transforma em uma tabela aberta exatamente
   com essas pessoas.

Executar novamente a mesma lista é inofensivo: um endereço conhecido é `updated`, nunca uma
segunda conta.

## Dependências diretas do módulo

- `g-access`, `g-auth`, `g-files`, `g-identity`, `g-notify`, `g-ses`, `g-smtp`,
  `g-staff`

## Participação na solução

- `production`

## Fonte

`modules/workflows/wf-team-invite`
