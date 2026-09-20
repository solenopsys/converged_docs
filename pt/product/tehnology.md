## Tecnologias

O Converged é construído sobre uma base de sistemas compacta, projetada para alto desempenho e uso eficiente de recursos em ambientes Kubernetes de qualquer escala — de um único microcomputador a um cluster distribuído.

No núcleo da infraestrutura está o **Zig** — uma linguagem de programação de sistemas moderna, extremamente rápida e simples. O Zig é usado em elementos de infraestrutura nos quais desempenho, eficiência de recursos, acesso ao hardware e controle de baixo nível são importantes.

O **Cruller** fornece o ambiente de execução para TypeScript e JavaScript. É um runtime especializado derivado do Bun e adaptado à arquitetura e aos requisitos do Converged.

O **Behemoth** fornece uma camada de dados unificada compatível com diferentes modelos de armazenamento, incluindo SQL, dados de chave-valor, arquivos, vetores e outras estruturas de dados especializadas. O armazenamento pode ser distribuído e escalado de acordo com os requisitos de cada implantação.

O **Fujin** fornece a camada de comunicação, conectando Services, interfaces, eventos e equipamentos por meio de uma malha unificada de comunicação em tempo real. O **Centimanus** executa Workflows e gerencia suas dependências, execução paralela, eventos, novas tentativas e operações de longa duração.

O Converged sempre é executado no **Kubernetes**. O ambiente-base é o **k3s**, uma distribuição leve do Kubernetes que torna o mesmo modelo de implantação prático até mesmo em pequenos dispositivos de borda, como o Raspberry Pi. Em uma única máquina, o Converged é executado como um cluster compacto de nó único; quando necessário, o mesmo cluster pode ser distribuído entre várias máquinas.

Isso fornece uma base tecnológica consistente em toda a infraestrutura — de um pequeno dispositivo de borda a um cluster de nuvem distribuído.
