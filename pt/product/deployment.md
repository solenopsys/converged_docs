## Implantação

O Converged oferece suporte a vários cenários de implantação — de dispositivos edge compactos e servidores locais a uma infraestrutura em nuvem que atende muitas empresas independentes. A plataforma base é executada no **k3s**, uma distribuição leve do Kubernetes adequada para microcomputadores, infraestrutura local e clusters em nuvem.

Há três perfis principais de implantação:

* **Mono** — UI, Serviços, armazenamento e cache são executados em uma configuração compacta em uma única máquina. É adequada para **microcomputadores como Raspberry Pi e Orange Pi**, dispositivos edge, pequenos servidores locais, desenvolvimento, protótipos e demonstrações.
* **Multi** — o sistema é distribuído entre várias máquinas em um cluster Kubernetes. A UI, grupos de Serviços, armazenamento e cache podem ser implantados e escalados de forma independente. Esse perfil é adequado para ambientes de produção que exigem capacidade adicional, tolerância a falhas e controle mais preciso dos recursos.
* **Cloud** — várias empresas operam dentro do **mesmo cluster Kubernetes**, usando uma arquitetura multi-tenant. Cada **tenant** possui um ambiente isolado com seus próprios dados, configuração e recursos, enquanto a infraestrutura subjacente do cluster é compartilhada. Isso permite atender muitas empresas de forma eficiente sem exigir um cluster separado para cada cliente.

Os três perfis usam a mesma base de código. Apenas a topologia e a configuração da implantação mudam. Assim, um sistema pode começar como uma instalação Mono compacta em um microcomputador, migrar para um cluster Multi conforme os requisitos crescem ou funcionar como um serviço Cloud compartilhado por muitas empresas independentes.

Em uma implantação **self-hosted**, a empresa controla a instalação, a rede, os backups, as atualizações e a localização física de seus dados. Isso é adequado para organizações que precisam de controle total sobre sua infraestrutura.

Na **Cloud**, a infraestrutura é operada centralmente. Várias empresas compartilham o mesmo cluster, permanecendo isoladas no nível do tenant, incluindo seus dados, configuração e recursos alocados.

Também é possível uma implantação **híbrida**: dados sensíveis e equipamentos podem permanecer locais, enquanto a nuvem é usada para atualizações, acesso externo, equipes distribuídas ou determinados recursos de IA.

O princípio fundamental é que o **Converged não prende a plataforma a um único modelo de implantação**. O mesmo sistema pode ser executado em um pequeno microcomputador, em um cluster com várias máquinas ou como um serviço Cloud multi-tenant.
