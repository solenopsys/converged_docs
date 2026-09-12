# Interface de linha de comando convergente

A CLI Convergente é um mecanismo de comandos voltado para operadores. Ela fornece uma
superfície de comandos consistente para diagnósticos da plataforma, automação, armazenamento e
operações de domínio, permitindo que cada capacidade permaneça em seu próprio módulo de
comandos.

## Superfície de comandos modular

O núcleo da CLI não contém um registro fixo de comandos de negócio. Na inicialização,
ele lê um ou mais diretórios passados por `--commands` e carrega o módulo TypeScript selecionado para cada seção de comando. Um módulo exporta uma fábrica que retorna um processador; o processador declara seus comandos e encaminha cada nome de comando para um manipulador.

```text
bun cli <section> <command> [param]
          |          |
          |          +-> command handler
          v
  command module -> processor -> generated NRPC client
```

Isso torna a CLI extensível sem alterar seu tempo de execução. Uma solução ou
produto pode adicionar um diretório de comandos, e um novo módulo `<section>.ts` se torna uma
nova seção da CLI. O núcleo carrega apenas a seção solicitada para execução, portanto um módulo
opcional ou com falha não pode impedir a execução de comandos não relacionados.

`BaseCommandProcessor` fornece o mapa de comandos comum, a saída de ajuda, a propagação de
erros e o comportamento consistente de listagem. Os módulos concentram-se em seus próprios
argumentos e ações de domínio; o executor gerencia a configuração da conexão, o ciclo de vida,
o relatório, a temporização, o status de saída e o encerramento do canal.

## Um modelo de autorização

Todos os módulos de comando habilitados para NRPC usam a mesma sessão da CLI e o mesmo caminho
de autorização. Primeiro, a CLI lê o JWT do usuário no arquivo de sessão local; em seguida,
recorre a `SERVICE_TOKEN` quando não há uma sessão disponível. A sessão do usuário tem
precedência porque as ações do operador podem exigir a identidade do chamador.

O token é enviado durante o handshake compartilhado do WebSocket Fujin e também
fornecido à configuração do cliente NRPC. Se uma sessão armazenada for rejeitada, o executor a
remove da conexão ativa e tenta novamente uma vez com o token de serviço, quando um estiver
configurado. Os erros de autenticação são relatados de maneira uniforme, com orientação para
entrar novamente, em vez de deixar que módulos de comando individuais gerenciem o estado do
token por conta própria.

A autorização continua sendo aplicada pelo serviço receptor. A CLI transporta as credenciais
do chamador e o escopo do workspace; ela não interpreta permissões nem concede acesso
localmente. Um comando pode optar por não usar o canal WebSocket somente quando fala
deliberadamente com um endpoint que não seja NRPC, como uma operação de diagnóstico direta.

## Integração com NRPC

Os módulos de comando criam clientes a partir de pacotes `g-<service>` gerados e passam a eles
a configuração compartilhada `createCliNrpcClientConfig`. O NRPC serializa a chamada de método
tipado em uma solicitação WebSocket, endereçada a um destino lógico e serviço Fujin. O Fujin a
encaminha ao par de runtime ativo, e o serviço aplica sua política normal de acesso antes de
executar o método.

O mesmo canal oferece suporte a métodos comuns de solicitação-resposta e a métodos de
streaming. Os identificadores de solicitação, os prazos, a ordenação das respostas e o
tratamento de falhas de conexão são centralizados no canal da CLI, portanto cada módulo obtém o
mesmo comportamento sem reimplementar o código do protocolo.

## Limite de responsabilidades

A CLI gerencia a descoberta de comandos, o ciclo de vida da execução de comandos, a seleção da
sessão local e o canal comum de cliente NRPC/WebSocket. Ela não gerencia a lógica de negócio do
domínio, decisões de permissão, implementação de serviços nem o roteamento do Fujin. Essas
responsabilidades permanecem com os módulos de comando, os serviços de backend e a
infraestrutura de runtime que recebe a chamada.
