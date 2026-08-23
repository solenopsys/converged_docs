## Arquitetura

O Converged foi projetado como uma plataforma modular, mas não como uma coleção caótica de microserviços. A separação é simples: a interface mostra dados e lança ações, Runtime executa processos, microserviços possuem dados, e adaptadores conectam equipamentos e sistemas externos.

```text
Usuário / cliente
        ↓
UI e micro-frontends
        ↓
Runtime: workflows, cron, integrações, ações de IA
        ↓
Microserviços: APIs tipadas e dados próprios
        ↓
Storage / Behemoth / arquivos / SQL / KV / métricas
        ↓
Equipamentos, mensageiros, pagamentos e serviços externos
```

Os microserviços permanecem deliberadamente finos. Cada serviço responde por sua área de dados, validação e API tipada. Ele não deve conhecer a lógica interna de serviços vizinhos nem se transformar em um centro oculto de processos de negócio. Isso reduz acoplamento e torna o sistema mais simples de manter.

Toda a lógica transversal é movida para o Runtime. Se o sistema precisa aceitar um pedido, consultar vários serviços, criar uma tarefa, enviar uma notificação, esperar um evento e atualizar o status, isso é executado em um workflow. O Runtime não armazena estado persistente por conta própria: ele grava histórico, variáveis e resultados por meio dos serviços que possuem seus próprios stores.

O armazenamento é construído em torno de isolamento. Em vez de uma base compartilhada, cada domínio recebe seus próprios limites de dados: SQL, key-value, arquivos, dados colunares, índices vetoriais ou relações de grafo quando necessário. Esse modelo ajuda a mover workspaces, limitar acesso e evitar uma base comum onde dados de clientes diferentes se misturam.

O frontend também é modular. A shell comum carrega micro-frontends independentes por import map, então áreas individuais da interface podem evoluir sem recompilar todo o produto. Para o usuário continua sendo um único sistema; para o desenvolvimento, um conjunto de zonas claras de responsabilidade.
