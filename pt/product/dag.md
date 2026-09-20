## Processos

### Arquitetura Sem uma Rede de Dependências

Converged é uma plataforma aberta na qual a comunidade pode criar, conectar e atualizar continuamente milhares de Serviços, módulos e Workflows. Esses componentes evoluem de forma independente, mas ainda precisam trabalhar juntos com precisão.

Em arquiteturas de serviços tradicionais, isso cria um problema sério à medida que o sistema cresce: cada novo componente pode introduzir novas conexões com componentes existentes. Chamadas diretas, cadeias de dependências, service mesh, roteamento e tratamento de falhas criam gradualmente uma camada separada de complexidade crescente. Quando milhares de componentes são desenvolvidos e atualizados de forma independente, manter essa rede de conexões torna-se cada vez mais difícil.

**O Converged resolve esse problema arquitetonicamente: os Serviços não sabem nada uns dos outros e nunca fazem chamadas diretas entre si.** Em vez de uma rede de dependências diretas, o sistema usa dois níveis de composição: a UI combina dados, enquanto os Workflows combinam operações em processos de negócios.

### Composição de Dados e Processos de Negócios

No nível da UI, dados de vários Serviços podem ser solicitados em paralelo e combinados em um único contexto de usuário. Funções leves e sem estado podem recuperar dados de diferentes fontes, transformá-los e produzir os dados necessários para uma Surface ou Projection. Os próprios Serviços não precisam saber onde ou junto a quais outros dados seus resultados serão usados.

As operações e os processos automatizados são tratados por meio de **Workflows**. Um Workflow é um cenário individual composto por uma sequência de scripts e operações. Ele define quais ações devem ser executadas, em que ordem, quais etapas podem ser executadas em paralelo, onde o processo deve aguardar um evento e o que acontece quando uma operação falha.

A plataforma pode conter **milhares de Workflows independentes**. Cada um pode usar Serviços e scripts existentes sem criar dependências diretas entre os próprios Serviços.

Por exemplo, um Workflow pode combinar uma solicitação, cálculo de preço, aprovação, enfileiramento, produção, controle de qualidade, pagamento e entrega. Outro Workflow pode usar os mesmos Serviços para um processo completamente diferente.

### Execução por Meio do Centimanus

**Centimanus** é o mecanismo de DAG que executa Workflows. Ele gerencia dependências entre etapas, execução paralela, espera por eventos, novas tentativas, recuperação de falhas e o estado de processos de longa duração.

Cada Workflow é um cenário independente, enquanto o Centimanus fornece um mecanismo de execução unificado para todos eles. Adicionar um novo processo, portanto, não exige alterar Serviços existentes nem criar novas conexões diretas entre eles.

Isso é especialmente importante para uma plataforma aberta. A comunidade pode adicionar novos Serviços, scripts e Workflows sem criar uma cascata de dependências por todo o sistema.

**Como resultado, o número de componentes e processos pode crescer para a casa dos milhares sem que a complexidade de seus relacionamentos cresça proporcionalmente.** Os Serviços permanecem independentes, os dados são compostos no nível da UI e as operações são combinadas por meio de Workflows individuais.

Isso dá ao Converged uma vantagem arquitetural de escalabilidade: o sistema pode expandir-se por meio de novos componentes e cenários sem transformar sua interação em uma rede crescente de dependências diretas.

### Ecossistema Aberto

Para desenvolvedores, novos recursos são adicionados por meio de Serviços, scripts sem estado e Workflows. Agentes de IA também podem iniciar ações permitidas dentro de cenários existentes, permanecendo dentro de regras e restrições definidas.

Para usuários comuns, essa complexidade permanece oculta. Eles não precisam gerenciar Serviços, construir grafos ou entender suas dependências. Workflows prontos são entregues com as soluções, enquanto os usuários podem configurá-los por meio de regras, funções, prazos, integrações e notificações.

**O usuário simplesmente habilita o processo necessário e obtém um resultado gerenciado.**
