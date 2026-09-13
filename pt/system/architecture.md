# Arquitetura do sistema

A Converged é uma camada operacional modular para empresas de manufatura. Suas interfaces de usuário, serviços de domínio, mecanismo de fluxos de trabalho, armazenamento, gateway de mídia e processadores industriais formam um único sistema sem se tornarem uma única aplicação.

A arquitetura separa três tipos de trabalho:

- módulos de domínio são proprietários dos dados de negócio e dos recursos voltados ao usuário;
- serviços nativos de runtime transportam mensagens, executam fluxos de trabalho, armazenam dados e lidam com mídia em tempo real;
- o plano de controle decide quais partes são executadas para cada plataforma e locatário.

## Um barramento de mensagens

Os componentes de runtime se comunicam por meio do Fujin. Cada processo abre uma conexão, registra um destino e envia mensagens para destinos lógicos. O remetente não precisa conhecer o endereço ou o local de implantação do receptor.

```text
clientes de navegador e dispositivos móveis
          |
          v
          barramento de mensagens Fujin
       /     |      |      \
      ui     ms  Centimanus Resonus
              \      |      /
               \  Behemoth /
```

Isso remove o grafo de chamadas HTTP e a malha de serviços da camada de aplicação. Roteamento, correlação de solicitações e contexto confiável do locatário viajam no envelope de mensagens comum. Um processo receptor então seleciona o serviço ou manipulador solicitado dentro de seu próprio limite.

## Runtime principal

| Componente | Responsabilidade |
| --- | --- |
| Fujin | Conecta pares de runtime e roteia mensagens para o proprietário ativo de um destino. |
| Behemoth | Fornece armazenamento isolado SQL, chave-valor, colunar, vetorial, de grafos e de arquivos. |
| Centimanus | Executa fluxos de trabalho empresariais de várias etapas como grafos reproduzíveis. |
| Resonus | Lida com mídia em tempo real, chamadas, transcrição e sessões de IA. |
| Ptah | Reconcilia a plataforma, as soluções e os locatários desejados em recursos do Kubernetes. |

Os componentes são deliberadamente restritos. O Fujin não entende serviços de negócio. O Behemoth não orquestra operações de negócio. O Centimanus não é proprietário dos dados de domínio. O Resonus não decide a identidade do locatário. O Ptah cria e configura cargas de trabalho, mas não participa das mensagens de runtime.

## Módulos e soluções

Os recursos de negócio são entregues como microsserviços, superfícies e fluxos de trabalho. Uma solução é uma seleção declarativa desses módulos para um cenário operacional específico, como processamento de pedidos, planejamento da produção ou monitoramento de equipamentos.

Os microsserviços são proprietários de seus dados e expõem contratos tipados. Eles não chamam uns aos outros para coordenar um processo. Sequências entre domínios pertencem aos fluxos de trabalho, que o Centimanus executa uma etapa durável por vez. Isso mantém os módulos de domínio pequenos e permite que uma solução os combine sem criar acoplamento oculto.

## Isolamento de dados

Cada microsserviço possui sua própria raiz física de armazenamento. O Behemoth pode atender muitas raízes a partir de um processo, mas preserva seus limites de propriedade e se recusa a criar dados fora das montagens configuradas.

O mesmo modelo se adapta a diferentes perfis de implantação:

- uma instalação de borda pode executar uma instância do Behemoth para a plataforma;
- uma instalação maior pode dividir os escopos entre fragmentos de armazenamento;
- uma instalação na nuvem pode executar uma instância de armazenamento isolada por locatário.

Alterar a topologia não altera o código da aplicação, pois os pares continuam endereçando destinos lógicos e limites de armazenamento.

## Plano de controle

O Ptah é o plano de controle e não está conectado ao Fujin. Ele observa os recursos declarados de Platform, Solution e Tenant, calcula as cargas de trabalho desejadas e as reconcilia com o Kubernetes.

```text
Platform + Solutions + Tenants
              |
              v
             Ptah
              |
              v
Implantações, serviços, volumes, configuração e rotas
```

Essa separação permite que o runtime permaneça concentrado no tráfego de negócio, enquanto o modelo de implantação lida com posicionamento, topologia de armazenamento, rotas de locatários e ciclo de vida. As mesmas imagens de aplicação podem, portanto, ser executadas em um cluster compacto de borda ou em um ambiente de nuvem multi-tenant.

## Contexto confiável

O escopo do locatário é estabelecido na borda da plataforma e transportado no envelope de mensagens. Os serviços de runtime consomem esse contexto confiável em vez de derivar um locatário dos payloads da aplicação. O posicionamento do armazenamento, as chamadas de serviço e as sessões de mídia preservam o mesmo limite de escopo.

Juntos, as mensagens lógicas, o armazenamento isolado, os fluxos de trabalho reproduzíveis e um plano de controle separado permitem que a Converged permaneça modular sem transferir a complexidade de sistemas distribuídos para cada módulo de negócio.
