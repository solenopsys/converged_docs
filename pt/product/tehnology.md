## Tecnologias

A parte servidor do Converged é construída sobre **Bun** e **Elysia**. Bun inicia JavaScript e TypeScript rapidamente, usa memória de forma eficiente e combina com implantações edge compactas. Elysia é usado como camada HTTP para plugins backend e microserviços.

Os contratos entre serviços são descritos com tipos. NRPC conecta interfaces TypeScript a implementações e gera pacotes cliente, para que frontend, Runtime e backend trabalhem com os mesmos contratos em vez de APIs textuais desconectadas.

O armazenamento de dados usa um conjunto de stores leves para diferentes tarefas: SQL, key-value, arquivos, dados colunares, índices vetoriais e relações de grafo. A camada nativa Behemoth e os adaptadores Zig cobrem tarefas em que baixo overhead, acesso a equipamentos, Unix sockets ou FFI importam.

O frontend é uma plataforma React com micro-frontends. A shell comum carrega módulos de UI separados, e os cenários de produto podem evoluir de forma independente. Isso é importante para uma plataforma com muitas soluções: a interface não deve se transformar em um monólito pesado.

Orquestração e entrega são construídas em torno de k3s, Helm e perfis de configuração. O mesmo conjunto de componentes pode ser montado em um perfil mono compacto ou separado em grupos para produção.
