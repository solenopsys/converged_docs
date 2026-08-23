## Desempenho

O Converged é projetado para locais de produção que nem sempre têm um grande parque de servidores. Por isso o sistema evita peso desnecessário: Bun reduz o overhead dos processos backend, Runtime permanece stateless, e microserviços podem ser agrupados por tipo de carga em vez de executar centenas de contêineres separados.

O desempenho vem da arquitetura, não de um único truque. Os dados não passam por camadas desnecessárias, os serviços possuem seus stores, Runtime paraleliza workflows e tarefas cron, e adaptadores nativos são usados onde HTTP ou uma camada JS comum adicionariam overhead demais.

Uma instalação compacta pode rodar em um servidor pequeno ou single-board computer se a carga combinar com a escala da oficina. Com o crescimento, Runtime, microserviços e grupos de storage podem ser separados para usar mais núcleos de CPU, isolar tarefas pesadas e evitar que um gargalo pare todo o sistema.

A plataforma não promete desempenho infinito “out of the box”. Gargalos dependem de equipamentos, volume de arquivos, número de pedidos, provedores de IA e integrações. A arquitetura do Converged permite começar de forma compacta e escalar apenas as partes que realmente ficam quentes.
