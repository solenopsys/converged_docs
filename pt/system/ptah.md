# Plano de controle do Ptah

O Ptah transforma uma descrição de plataforma Converged em recursos Kubernetes em execução.
Ele é o plano de controle do sistema: decide o que deve existir para uma plataforma,
quais soluções estão ativas e como as cargas de trabalho e o armazenamento dos tenants são posicionados.

## Modelo de plataforma desejado

O modelo de implantação tem três camadas:

| Recurso | Significado |
| --- | --- |
| Plataforma | Runtime compartilhado, roteamento, perfil de armazenamento, aplicações e mapa de módulos. |
| Solução | Um conjunto de módulos de negócio, fluxos de trabalho e processadores adicionados a uma plataforma. |
| Tenant | Um site isolado com seu próprio escopo, rotas e, quando necessário, fragmento de armazenamento. |

O Ptah observa esses recursos e produz o conjunto completo desejado de
implantações, serviços, volumes, configurações e rotas. O Kubernetes então
converge o cluster de acordo com essa descrição.

```text
Plataforma + Solução + Tenant
              |
              v
             Ptah
              |
              v
Cargas de trabalho, armazenamento e rotas do Kubernetes
```

## Política e mecanismo

O Ptah separa os mecanismos do cluster da política do produto. O controlador nativo
observa o Kubernetes, aplica recursos, registra o status e remove objetos obsoletos. Uma camada de política pura converte os dados observados da plataforma em um resultado desejado, sem fazer chamadas de rede ou modificar o próprio cluster.

A mesma política pode, portanto, ser avaliada antes da implantação. Isso torna
as decisões de posicionamento e ciclo de vida inspecionáveis sem reproduzi-las em
um segundo gerador de configuração.

## Perfis de implantação

Os perfis alteram o posicionamento do armazenamento sem alterar as imagens das aplicações:

- `mono` executa uma instância de armazenamento para uma plataforma compacta;
- `multi` divide os escopos entre fragmentos de armazenamento;
- `cloud` fornece a cada tenant uma instância de armazenamento isolada e um limite de rota.

A regra de propriedade dos volumes permanece a mesma em todos os perfis: cada microsserviço
tem seu próprio volume de armazenamento. O Ptah decide qual instância do Behemoth monta esses
volumes e publica o mapeamento de escopo para armazenamento usado pelas cargas de trabalho sem estado.

## Módulos e rollout

As soluções nomeiam módulos em vez de incorporar seus bytes. O Ptah distribui um
mapa de módulos endereçado por conteúdo e disponibiliza conteúdo imutável dos módulos por meio de um
cache compartilhado. Os consumidores recebem o digest exato que devem carregar.

Quando o digest selecionado muda, a descrição da carga de trabalho muda com ele e
o Kubernetes executa o rollout. Assim, um pod em execução registra o conteúdo preciso
do módulo com o qual foi iniciado, e o rollback significa selecionar novamente o digest anterior.

## Reconciliação segura

O Ptah aplica um conjunto completo desejado e remove por limpeza os recursos que não pertencem mais a ele. Os recursos que contêm dados são mantidos, a menos que a exclusão seja solicitada explicitamente. Entradas incompletas ou uma falha de política suprimem a limpeza, impedindo que um problema temporário de dependência seja interpretado como uma solicitação para remover a plataforma.

## Papel no sistema

O Ptah não é um par no barramento de mensagens Fujin e não processa tráfego de negócio. Ele cria e configura os pares, o armazenamento e as rotas que compõem o runtime. Depois que estão em execução, Fujin, Behemoth, Centimanus e Resonus realizam seu trabalho independentemente do plano de controle.
