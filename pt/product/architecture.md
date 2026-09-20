## Arquitetura

Converged é construído como um ambiente de execução modular no qual a interface, a lógica de negócios e a infraestrutura são separadas, embora operem como um único sistema.

No nível do usuário, o sistema consiste em **Superfícies**, que organizam o contexto de trabalho, e **Projeções** — telas individuais projetadas para resolver tarefas específicas do usuário.

A lógica de negócios é implementada em **TypeScript** por meio de vários tipos de **Serviços**: Repositórios, Lambdas e Runtimes. Processos mais complexos são montados em **Workflows**, que são executados pelo mecanismo de processamento de DAG Centimanus.

Na base do sistema estão os **Apps**. Eles são ambientes de execução de infraestrutura com um núcleo compacto em Zig, no qual scripts TypeScript são executados. Os Apps fornecem os recursos fundamentais sobre os quais operam os Serviços, Workflows e a UI.

```text
Usuário
  ↓
Superfícies
  └── Projeções
        ↓
Serviços — TypeScript
  ├── Repositórios
  ├── Lambdas
  └── Runtimes
        ↓
Workflows
        ↓
Apps — Zig + TypeScript
  ├── Fujin
  ├── Centimanus
  ├── Resonus
  ├── Behemoth
  ├── Ptah
  └── Cruller
        ↓
Kubernetes
  ↓
Edge / Servidor / Cluster
```

### Superfícies e Projeções

Uma **Superfície** é um espaço de trabalho do usuário organizado em torno de um contexto de trabalho específico. Ela reúne os dados, as ações e as visualizações necessários para trabalhar em uma determinada área.

Uma Superfície não precisa corresponder a um único Serviço. Ela pode combinar dados e ações de vários Repositórios, Lambdas, Runtimes e Workflows.

Uma **Projeção** é uma tela individual dentro de uma Superfície, projetada para executar uma função específica. Ela apresenta os dados de uma forma conveniente para o usuário e fornece as ações necessárias.

A interface é, portanto, organizada em torno de **com o que o usuário está trabalhando**, e não em torno da estrutura interna dos Serviços.

### Serviços

A lógica de negócios do Converged é escrita em TypeScript e dividida em vários tipos de Serviços.

**Repositórios** encapsulam o acesso aos dados. Eles fornecem uma interface para ler, modificar e consultar dados, ocultando o mecanismo de armazenamento subjacente.

**Lambdas** são funções sem estado projetadas para operações individuais, como processamento e transformação de dados, computação, validação ou atuação como gateways para APIs externas.

**Runtimes** fornecem ambientes de execução especializados para lógicas que exigem seu próprio contexto de execução.

Os Serviços são os blocos de construção do sistema. Eles não precisam conhecer os processos de negócios nos quais serão usados e podem ser reutilizados por diferentes Superfícies e Workflows.

### Workflows

Um **Workflow** combina Serviços em um processo de negócios completo.

Em vez de conectar Serviços por meio de chamadas diretas, um Workflow define quais operações devem ser executadas, em que ordem, quais etapas podem ser executadas em paralelo, onde o sistema deve aguardar um evento e o que deve acontecer quando uma operação falha.

Por exemplo:

```text
Pedido
  ↓
Pagamento
  ↓
Fatiamento
  ↓
Produção
  ↓
Entrega
```

Um Workflow pode usar Repositórios para operações de dados, Lambdas para operações individuais e Runtimes ou Apps para tarefas especializadas.

### Centimanus

**Centimanus é o mecanismo de DAG que executa Workflows.**

Um Workflow é representado como um grafo de operações, enquanto o Centimanus gerencia sua execução: dependências entre etapas, novas tentativas, espera por eventos, operações paralelas e compensação em caso de falha.

Cada execução produz uma trilha de auditoria mostrando o que foi iniciado, o que foi concluído, quais operações foram repetidas e por que ocorreu uma falha.

Isso possibilita criar processos resilientes e de longa duração que preservam o estado da execução e podem continuar após uma reinicialização.

Os Serviços permanecem independentes porque não precisam ser conectados por cadeias de chamadas diretas para implementar um processo de negócios específico.

### Apps

**Os Apps são a base da infraestrutura do Converged.**

Um App é um ambiente virtual de execução leve. Seu núcleo do sistema é escrito em **Zig**, enquanto a lógica mutável é executada como **scripts TypeScript**.

Essa separação mantém a infraestrutura crítica em um núcleo compacto e de alto desempenho, preservando a flexibilidade do TypeScript para a lógica e a configuração da aplicação.

Os Apps fornecem os recursos de infraestrutura usados pelo restante do sistema:

* **Fujin** — tecido de comunicação para comandos, eventos, WebSockets e telemetria de máquinas.
* **Centimanus** — processamento de DAG e execução de Workflows.
* **Resonus** — gateway em tempo real para voz, mídia, transcrição e provedores de IA.
* **Behemoth** — armazenamento múltiplo isolado para diferentes tipos de dados.
* **Ptah** — gerenciamento de implantação e topologia do Kubernetes.
* **Cruller** — runtime no qual módulos de UI e TypeScript são executados.

Os Apps não são outra camada de lógica de negócios. Eles fornecem a **infraestrutura e os ambientes de execução** nos quais a camada TypeScript opera.

### Fujin

**Fujin é o tecido unificado para comandos, eventos e telemetria.**

Todos os componentes do sistema se comunicam por meio do Fujin, em vez de fazer chamadas diretas uns aos outros. Um comando da UI, um evento de Workflow, uma leitura de sensor de uma máquina ou uma atualização do progresso da produção passam pela mesma camada de comunicação.

WebSockets entregam alterações à interface em tempo real, sem polling.

Como a comunicação passa por uma única camada, ela pode ser rastreada, reproduzida e limitada centralmente.

**Resultado:** os Serviços permanecem independentes, o tempo real passa a fazer parte da infraestrutura comum e os eventos do sistema tornam-se observáveis.

### Resonus

**Resonus é uma interface unificada em tempo real para voz, mídia e IA.**

Ele combina chamadas telefônicas, fluxos de áudio, transcrição e adaptadores de provedores de IA em uma única camada.

Uma conversa pode passar de uma chamada telefônica para transcrição e depois para análise de IA sem transitar entre sistemas separados. A mídia pode ser associada diretamente a pedidos, equipamentos e eventos.

Os adaptadores de provedores isolam o sistema de fornecedores individuais de voz e IA.

**Resultado:** voz, mídia e IA tornam-se parte do ambiente comum de Workflows, enquanto os provedores podem ser substituídos sem reestruturar a lógica da aplicação.

### Behemoth

**Behemoth é o sistema unificado de armazenamento múltiplo para os dados do Converged.**

Diferentes tipos de dados recebem o armazenamento apropriado: SQL para pedidos e clientes, arquivos para modelos e documentos, vetores para busca de IA, cache para estado quente e outros tipos especializados de armazenamento quando necessário.

O isolamento é estrutural: os dados de diferentes espaços de trabalho não são misturados e podem ser escalados, copiados para backup e movidos de forma independente.

O mesmo modelo funciona em implantações Edge, Server e Cluster. Em um pequeno dispositivo Edge, todos os domínios de armazenamento podem residir em um único nó; em um Cluster, eles podem ser distribuídos entre equipamentos de armazenamento especializados.

**Resultado:** os dados são isolados por construção, enquanto a infraestrutura de armazenamento pode crescer com a instalação sem alterar a camada da aplicação.

### Ptah

**Ptah é o orquestrador de implantação do Converged sobre o Kubernetes.**

Ele gerencia a alocação de Apps, contêineres e dados de acordo com a topologia de implantação: Edge, Server ou Cluster.

O núcleo do Ptah é escrito em Zig, enquanto as regras de gerenciamento são implementadas como scripts TypeScript. Isso permite que a lógica de alocação, ordem de implantação, failover e distribuição de dados mude sem reconstruir o núcleo.

O mesmo mecanismo é usado para diferentes tipos de instalação — de um único nó Edge a um cluster distribuído.

**Resultado:** todo o sistema é gerenciado por meio de uma camada de implantação unificada, enquanto a lógica de implantação permanece dinâmica e modificável.

### Cruller

**Cruller é o runtime para a UI e os módulos TypeScript.**

Ele fornece o ambiente no qual a lógica TypeScript do Converged é executada, incluindo a UI e os módulos da aplicação.

O Cruller conecta a camada dinâmica TypeScript aos recursos de infraestrutura fornecidos pelos Apps, permitindo que a camada da aplicação evolua sem modificar o núcleo de baixo nível.

### Kubernetes e Topologia

Todos os Apps e componentes relacionados são implantados por meio do **Kubernetes**.

O Converged usa o mesmo modelo arquitetural independentemente da escala da instalação:

```text
Edge
  → nó único

Server
  → servidor único com mais recursos

Cluster
  → vários nós e armazenamento distribuído
```

A topologia física muda, mas o modelo da aplicação não. Serviços, Workflows, Superfícies e Projeções operam da mesma maneira, esteja o sistema sendo executado em um dispositivo Edge ou em um cluster completo.

### Modelo Unificado

As diferentes partes do Converged são organizadas em torno de responsabilidades distintas:

**Surface** — contexto de trabalho do usuário.
**Projection** — uma função específica e sua representação visual.
**Repository** — acesso a dados.
**Lambda** — uma operação individual sem estado.
**Runtime** — um ambiente de execução especializado.
**Workflow** — um processo de negócios que combina Serviços.
**Apps** — ambientes de execução de infraestrutura com um núcleo Zig e TypeScript internamente.
**Fujin** — comunicação e eventos.
**Centimanus** — execução de Workflows.
**Resonus** — voz, mídia e IA em tempo real.
**Behemoth** — armazenamento.
**Ptah** — implantação e gerenciamento do Kubernetes.
**Cruller** — ambiente de execução para UI e TypeScript.

O princípio central do Converged é **separar o contexto do usuário, a lógica da aplicação e a infraestrutura sem forçá-los a seguir a mesma estrutura**.

Uma Surface pode combinar vários Serviços. Um Workflow pode combinar várias operações. E vários Workflows e Serviços podem usar os mesmos Apps subjacentes.

O resultado é um sistema que permanece modular no nível da lógica de negócios, compacto no nível da infraestrutura e unificado da perspectiva do usuário.
