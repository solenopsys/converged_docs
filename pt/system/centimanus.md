# Runtime de workflows do Centimanus

O Centimanus executa os processos de várias etapas que conectam módulos
Converged que, de outra forma, seriam independentes. Roteamento de pedidos,
notificações, aprovações, trabalho assistido por IA e sequências de produção
podem evoluir como workflows sem transferir a orquestração para os serviços de
domínio.

## Execução reproduzível

Um workflow é um programa cujas operações significativas são divididas em nós
nomeados. O Centimanus executa um nó inacabado, registra seu resultado e então
avalia o workflow novamente. Nós concluídos retornam seus resultados
armazenados em vez de repetir seus efeitos colaterais.

```text
primeira passagem:   localizar pedido -> armazenar resultado
segunda passagem:    reproduzir pedido -> reservar máquina -> armazenar resultado
terceira passagem:   reproduzir ambos -> notificar operador -> concluir
```

Ramificações e loops podem depender de resultados anteriores, portanto o grafo
surge do próprio processo, em vez de um diagrama estático separado. Os
resultados registrados dos nós tornam o progresso explícito e permitem que a
execução continue a partir da primeira etapa inacabada.

## Por que os workflows são separados

Os microsserviços de domínio no Converged são proprietários dos dados e de
pequenas capacidades de negócio. Eles não chamam uns aos outros para
implementar um processo de ponta a ponta. Isso evita cadeias ocultas nas quais
uma alteração ou falha em um serviço afeta inesperadamente muitos outros.

O Centimanus é o local onde a coordenação entre domínios fica visível. Um
workflow pode chamar serviços, solicitar trabalho de IA e escolher a próxima
etapa, enquanto cada serviço permanece concentrado em seu próprio limite.

## Entrega de workflows

As soluções determinam quais workflows estão ativos. O Ptah publica essa
seleção, o serviço DAG expõe os descritores selecionados e o Centimanus carrega
o conteúdo correspondente por meio do proxy endereçável por conteúdo do Ptah.
Um workflow que não faça parte da solução ativa não está disponível para
execução.

Isso separa quatro preocupações: seleção do produto, entrega de conteúdo,
execução e observabilidade. Cada uma pode mudar sem transformar o runtime de
workflows em um registro de módulos ou controlador de implantação.

## Limite de confiabilidade

O Centimanus registra os resultados dos nós concluídos, mas as operações
externas ainda devem respeitar suas próprias regras de idempotência. A
telemetria do workflow é usada para visibilidade; ela não decide o estado de
execução. Os dados de negócio permanecem nos serviços que são seus proprietários,
em vez de se tornarem estado do mecanismo de workflows.

## Papel no sistema

O Centimanus recebe trabalho e chama serviços por meio do Fujin. Ele usa o
armazenamento da plataforma para o progresso dos workflows e reporta eventos do
ciclo de vida para monitoramento. Ele não é proprietário dos registros de
domínio, não seleciona soluções ativas nem roteia mensagens entre outros pares.
