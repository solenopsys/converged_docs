# Product

- [Plataforma Converged AI](#plataforma-converged-ai)
- [O que o Converged faz](#o-que-o-converged-faz)
- [Sistema de soluções](#sistema-de-soluções)
- [Equipamentos e chão de fábrica](#equipamentos-e-chão-de-fábrica)
- [Processos](#processos)
- [Camada de IA](#camada-de-ia)
- [Arquitetura](#arquitetura)
- [Implantação](#implantação)
- [Tecnologias](#tecnologias)
- [Desempenho](#desempenho)
- [Segurança](#segurança)
- [Licenciamento](#licenciamento)
- [Comunidade](#comunidade)
- [Código-fonte](#código-fonte)

## Plataforma Converged AI

**Converged AI** é uma plataforma open-source para empresas de manufatura: bureaus de impressão 3D, oficinas CNC, laboratórios de P&D e redes de pequenas oficinas.

Sua função é assumir tudo o que acontece ao redor da produção: solicitações, arquivos, estimativas, filas, status de pedidos, comunicação com clientes, equipamentos, pagamentos, entrega e vendas recorrentes. As máquinas continuam fabricando peças, a equipe continua tomando decisões de engenharia, e o Converged conecta tudo em um sistema gerenciável.

A plataforma inclui **17 soluções** agrupadas em quatro áreas: pedidos e clientes, produção e estoque, dinheiro e lucro, equipe e responsabilidade. Não são “módulos por módulos”, mas cenários prontos para problemas concretos da oficina.

![Painel do Converged AI](/dashboard_ru.png)

## O que o Converged faz

### O que o Converged faz

Uma empresa de manufatura tem duas camadas de trabalho. A primeira é fabricar a peça, montar o produto e concluir o pedido. A segunda é tudo o que precisa acontecer antes, durante e depois da produção: aceitar uma solicitação, não perder o arquivo, combinar o preço, colocar o trabalho na fila, avisar o cliente, entender a carga das máquinas, detectar atrasos e receber o pagamento.

O Converged cobre essa segunda camada. É um circuito digital de controle que conecta o site, solicitações de clientes, tarefas internas, equipamentos, estoque, pagamentos, notificações e análises. O proprietário vê não um conjunto de ferramentas desconectadas, mas uma imagem viva do negócio: o que entrou, o que foi aceito, o que está na fila, o que está pronto, onde há risco de atraso e onde a margem está sendo perdida.

A plataforma é especialmente útil quando a produção já funciona, mas a gestão depende de chats, planilhas, memória dos funcionários e controle manual. O Converged não força a adoção imediata de um ERP ou MES pesado. Ele começa por processos concretos e gradualmente constrói um sistema unificado ao redor deles.

Em um cenário típico, o cliente envia uma solicitação pelo site, formulário, mensageiro ou operador. O Converged salva a solicitação, anexa arquivos, cria um pedido, ajuda a estimar o preço, coloca o trabalho na fila, acompanha a execução e mantém o cliente informado. Um operador pode perguntar o status na interface ou pelo chat de IA, e o sistema responde com dados reais, não com suposições.

Como resultado, a oficina depende menos de coordenação manual. As pessoas se concentram na produção e nas decisões que realmente exigem experiência, enquanto a plataforma cuida do roteamento, controle de prazos, mensagens repetitivas, coleta de status e preparação de ações.

## Sistema de soluções

### Sistema de soluções

O Converged não é vendido como uma plataforma vazia em que o cliente primeiro precisa inventar a arquitetura e montar módulos. A unidade básica de valor é uma **solução**: um cenário de trabalho pronto que resolve um problema claro do negócio.

A plataforma inclui **17 soluções** agrupadas em quatro áreas:

- **Pedidos e clientes** — solicitações recebidas, vitrine de serviços, histórico do cliente, status, comunicação e vendas recorrentes.
- **Produção e estoque** — carga de equipamentos, filas, materiais, controle de qualidade, falhas e envios.
- **Dinheiro e lucro** — custo, margem, pagamentos, recebíveis, precificação e cenários de crescimento.
- **Equipe e responsabilidade** — zonas de responsabilidade, turnos, padrões, base de conhecimento e onboarding.

Uma solução dentro do Converged não é apenas uma tela na interface. Normalmente inclui modelo de dados, workflow, funções, notificações, ações de agente de IA e integrações com equipamentos ou serviços externos. O proprietário não escolhe uma “funcionalidade”, mas um problema: acelerar o atendimento de solicitações, ver a fila de máquinas, entender a lucratividade dos pedidos ou organizar os turnos.

A descrição detalhada de todas as soluções deve ficar em uma seção separada. Na documentação do produto, o ponto importante é o princípio: Converged AI é a plataforma, e as soluções são cenários aplicados que funcionam dentro dela e fecham gradualmente diferentes áreas do negócio de manufatura.

## Equipamentos e chão de fábrica

### Equipamentos e chão de fábrica

O Converged não substitui o firmware da máquina e não tenta controlar a produção às cegas. Ele se conecta acima dos equipamentos, lê telemetria, vincula o estado das máquinas aos pedidos e mostra o que realmente está acontecendo no chão de fábrica.

A plataforma foi pensada para diferentes tipos de equipamento: impressoras 3D Bambu Lab, Marlin e Klipper, máquinas CNC, células robóticas e adaptadores especializados. Quando possível, o Converged recebe status, erros, progresso de execução, temperatura, filas de tarefas e outros dados técnicos. Quando o controle direto é arriscado ou indisponível, o sistema permanece como uma camada de observação e coordenação.

Para o proprietário, isso significa algo simples: os equipamentos deixam de ser um conjunto de janelas separadas. É possível ver quais máquinas estão ocupadas, onde há ociosidade, o que está atrasado, qual pedido está ligado a uma operação específica e onde um operador precisa intervir. Conforme o parque cresce, essa visibilidade se torna mais importante do que alternar manualmente entre interfaces separadas de impressoras ou máquinas.

O Converged também conecta os equipamentos ao processo de negócio. Uma tarefa não está apenas “imprimindo” ou “usinando”: ela está no contexto de um pedido, prazo, cliente, material, pagamento e próximo passo. O chão de fábrica se torna parte do sistema comum, não uma ilha separada.

## Processos

### Processos

O principal problema de uma oficina em crescimento raramente é a falta de mais um botão. Com mais frequência, os processos vivem na cabeça das pessoas: quem deve responder ao cliente, quando calcular o preço, quem verifica o arquivo, quando iniciar a produção, quem avisar em caso de atraso e o que fazer depois do envio.

No Converged, essas cadeias são descritas como workflows. Um processo típico pode ir da solicitação à estimativa, aprovação, fila, produção, controle de qualidade, pagamento, entrega e notificações. O usuário normalmente não constrói um grafo do zero: os cenários prontos vêm com as soluções, e a configuração se resume a regras, papéis, prazos, integrações e notificações.

Tecnicamente, a execução é movida para a camada Runtime. Ela executa workflows, tarefas cron, passos de integração e lógica de negócio permanecendo stateless: os dados persistentes ficam nos microserviços, e o Runtime responde pela execução das cadeias. Assim a lógica de negócio não se espalha por dezenas de serviços e existe um lugar claro onde vivem as regras do processo.

Para implantações complexas, os workflows podem ser estendidos. Um desenvolvedor descreve cenários como classes TypeScript tipadas, e agentes de IA podem lançar ações permitidas dentro desses cenários. Mas para um usuário comum, o objetivo é outro: não construir um editor, mas ativar um processo pronto e obter um resultado gerenciado.

## Camada de IA

### Camada de IA

A IA no Converged não é um chat separado adicionado por aparência. É uma camada de controle sobre dados, interface e processos. O usuário pode perguntar o que está acontecendo com um pedido, pedir uma resposta para o cliente, encontrar um atraso, lançar um workflow permitido ou reunir um resumo da carga das máquinas.

O modelo recebe contexto da plataforma: solicitações, status, arquivos, telemetria, histórico do cliente, direitos de acesso e tarefas atuais. Por isso a resposta se baseia em dados da empresa, não em raciocínio genérico. Se uma ação for necessária, a IA não contorna o sistema diretamente: ela chama funções, microserviços ou workflows permitidos por meio de uma camada controlada.

Os provedores de modelos se conectam por adaptadores. Uma mesma instalação pode usar GPT, Claude, DeepSeek, Mistral, Gemini ou outros motores se eles se ajustarem à tarefa e à política do cliente. Um modelo pode conversar com clientes, outro analisar requisitos técnicos, e um terceiro examinar documentos ou status de produção.

O princípio-chave é controle. A IA tem seu próprio perfil de acesso, todas as ações são registradas e operações críticas são executadas sob os mesmos direitos e políticas das ações humanas. Isso permite confiar rotina aos agentes sem dar a eles poder descontrolado sobre a produção.

## Arquitetura

### Arquitetura

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

## Implantação

### Implantação

O Converged atende a vários cenários de instalação: de uma pequena oficina a uma implantação de produção na infraestrutura da empresa. A plataforma base roda sobre **k3s**, uma distribuição leve de Kubernetes adequada para dispositivos edge, servidores locais e ambientes cloud.

Há dois perfis principais:

- **Mono** — UI, Runtime, microserviços, storage e cache são empacotados de forma compacta. Esse modo serve para desenvolvimento, protótipos, demonstrações e instalações pequenas em que a simplicidade de partida é mais importante.
- **Multi** — UI, grupos de Runtime, grupos de microserviços por domínio, storage e cache são separados. Esse é o perfil padrão de produção quando são necessários isolamento, escala e controle mais preciso de carga.

Os dois perfis usam o mesmo código. O que muda é a topologia dos contêineres e a configuração. Uma empresa pode começar com uma instalação compacta e depois mover o mesmo sistema para uma infraestrutura mais séria sem reescrever o produto.

Em cenários self-hosted, o cliente controla instalação, rede, backups, atualizações e localização física dos dados. Isso atende empresas com requisitos internos de segurança ou desejo de manter a produção totalmente do seu lado. A entrega cloud remove o trabalho operacional: a plataforma é implantada e atualizada pela equipe do serviço, enquanto o cliente recebe um ambiente pronto.

Também é possível uma opção híbrida: dados sensíveis e equipamentos ficam localmente, enquanto a nuvem é usada para atualizações, acesso externo, coordenação de equipes distribuídas ou funções específicas de IA. O princípio importante é não prender o cliente a um único modelo de entrega.

## Tecnologias

### Tecnologias

A parte servidor do Converged é construída sobre **Bun** e **Elysia**. Bun inicia JavaScript e TypeScript rapidamente, usa memória de forma eficiente e combina com implantações edge compactas. Elysia é usado como camada HTTP para plugins backend e microserviços.

Os contratos entre serviços são descritos com tipos. NRPC conecta interfaces TypeScript a implementações e gera pacotes cliente, para que frontend, Runtime e backend trabalhem com os mesmos contratos em vez de APIs textuais desconectadas.

O armazenamento de dados usa um conjunto de stores leves para diferentes tarefas: SQL, key-value, arquivos, dados colunares, índices vetoriais e relações de grafo. A camada nativa Behemoth e os adaptadores Zig cobrem tarefas em que baixo overhead, acesso a equipamentos, Unix sockets ou FFI importam.

O frontend é uma plataforma React com micro-frontends. A shell comum carrega módulos de UI separados, e os cenários de produto podem evoluir de forma independente. Isso é importante para uma plataforma com muitas soluções: a interface não deve se transformar em um monólito pesado.

Orquestração e entrega são construídas em torno de k3s, Helm e perfis de configuração. O mesmo conjunto de componentes pode ser montado em um perfil mono compacto ou separado em grupos para produção.

## Desempenho

### Desempenho

O Converged é projetado para locais de produção que nem sempre têm um grande parque de servidores. Por isso o sistema evita peso desnecessário: Bun reduz o overhead dos processos backend, Runtime permanece stateless, e microserviços podem ser agrupados por tipo de carga em vez de executar centenas de contêineres separados.

O desempenho vem da arquitetura, não de um único truque. Os dados não passam por camadas desnecessárias, os serviços possuem seus stores, Runtime paraleliza workflows e tarefas cron, e adaptadores nativos são usados onde HTTP ou uma camada JS comum adicionariam overhead demais.

Uma instalação compacta pode rodar em um servidor pequeno ou single-board computer se a carga combinar com a escala da oficina. Com o crescimento, Runtime, microserviços e grupos de storage podem ser separados para usar mais núcleos de CPU, isolar tarefas pesadas e evitar que um gargalo pare todo o sistema.

A plataforma não promete desempenho infinito “out of the box”. Gargalos dependem de equipamentos, volume de arquivos, número de pedidos, provedores de IA e integrações. A arquitetura do Converged permite começar de forma compacta e escalar apenas as partes que realmente ficam quentes.

## Segurança

### Segurança

O Converged parte do princípio de que dados de produção não devem ser jogados em um monte compartilhado. Pedidos, arquivos de clientes, parâmetros tecnológicos, pagamentos, mensagens e telemetria de equipamentos precisam ser separados por workspaces e zonas de responsabilidade.

Arquiteturalmente, isso é sustentado por isolamento de dados. Microserviços possuem seus stores, e workspaces podem ter diretórios, chaves, arquivos e limites de acesso separados. Isso simplifica exportação, migração self-hosted, backups e auditoria.

Direitos de acesso se aplicam não apenas a pessoas, mas também a agentes de IA. Se um modelo lança uma ação, lê dados ou chama um workflow, isso deve acontecer dentro do seu perfil de permissões. As ações são registradas, então é possível reconstruir quem ou qual agente iniciou um passo, quais dados foram afetados e como o cenário terminou.

Implantações self-hosted e private dão ao cliente controle total sobre a infraestrutura: rede, segredos, API keys, backups e localização física dos dados. O modo cloud é operacionalmente mais simples, mas não deve virar vendor lock-in: dados devem permanecer portáveis, e cenários devem continuar reproduzíveis em outra instalação.

## Licenciamento

### Licenciamento

O Converged é distribuído sob **AGPL-3.0**. É uma licença copyleft para software de rede: se você modificar a plataforma e fornecer acesso a ela pela rede, as mudanças devem ser divulgadas conforme os termos da licença.

Para usuários, isso significa que a versão self-hosted pode ser implantada sem comprar uma licença pelo código em si. Esse caminho serve para empresas que precisam de controle, instalação local, auditoria ou experimentos em hardware próprio. A responsabilidade operacional fica com o dono da instalação: atualizações, backups, monitoramento, segurança e disponibilidade.

A entrega cloud não é venda de código fechado, mas um serviço ao redor de uma plataforma open-source. O cliente paga por início rápido, suporte, atualizações, backups, monitoramento, infraestrutura e operação previsível. Para muitas oficinas, isso é mais barato do que construir competência DevOps internamente.

Esse equilíbrio é importante para a confiança: o núcleo permanece aberto, a comunidade pode revisar e desenvolver a plataforma, e o modelo comercial se constrói em torno de implantação, suporte e entrega controlada de valor.

## Comunidade

### Comunidade

O Converged foi pensado como uma plataforma aberta de manufatura, não como uma caixa SaaS fechada. O núcleo base está disponível sob uma licença open-source, e integrações, microserviços, micro-frontends, workflows e soluções aplicadas podem crescer ao redor dele.

Isso importa no mercado de manufatura: oficinas diferentes usam equipamentos, materiais, padrões de qualidade e cadeias de suprimento diferentes. Um sistema fechado rapidamente encontra os limites de um fornecedor específico. Uma arquitetura aberta permite adicionar adaptadores e cenários para condições reais de operação.

Uma extensão pode ser simples: um novo adaptador de equipamento, integração com serviço de pagamento, importação de um site antigo, um módulo UI separado ou um workflow para uma indústria específica. Se a extensão for útil para outros participantes, pode entrar no catálogo de soluções ou permanecer como implantação privada.

Aberto não significa sem controle. Extensões devem passar por revisão técnica, respeitar limites arquiteturais e não receber acesso a dados mais amplo do que o necessário. A confiança no ecossistema é construída sobre código-fonte, reprodutibilidade e um modelo claro de permissões.

## Código-fonte

### Código-fonte

O projeto é desenvolvido abertamente. O código-fonte, a arquitetura atual e os materiais de trabalho estão disponíveis no repositório:

[https://github.com/solenopsys/converged](https://github.com/solenopsys/converged)

O repositório é útil não apenas para desenvolvedores. Ele permite entender como microserviços, Runtime, micro-frontends, geração de contratos, perfis de implantação e adaptadores de hardware estão organizados. Para empresas que avaliam self-hosted ou implantação privada, isso é parte importante da verificação: a plataforma não é uma caixa fechada.
