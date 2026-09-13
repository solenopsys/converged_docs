# Catálogo de módulos

Este índice é gerado a partir do registro de módulos da Converged. Cada entrada aponta para a documentação mantida por esse módulo; as dependências são obtidas do manifesto de pacotes do workspace, e a participação em soluções vem de `modules/solutions`.

## Acesso e segurança

### [lm-secrets](/en/docs/modules/lm-secrets)

Fornece o contrato de serviço para armazenar, recuperar e excluir valores de segredos nomeados.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-access](/en/docs/modules/rp-access)

rp-access é um repositório no domínio sequrity. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth é um repositório no domínio sequrity. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-environment](/en/docs/modules/rp-environment)

Armazena e recupera a configuração do ambiente associada aos usuários da plataforma.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity é um repositório no domínio sequrity. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth é um repositório no domínio sequrity. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth é uma superfície no domínio sequrity. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Fornece a interface de administração para criar, visualizar, atualizar e excluir registros de segredos nomeados.

- Dependências diretas: nenhuma
- Soluções: nenhuma

## IA e agentes

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant é um repositório no domínio ai. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Fornece o armazenamento e a recuperação de contextos de IA nomeados, incluindo suas variantes linguísticas.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants é uma superfície no domínio ai. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: `sf-requests`
- Soluções: `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Fornece o espaço de trabalho de IA para listar, editar e salvar contextos nomeados em vários idiomas.

- Dependências diretas: nenhuma
- Soluções: `ai`

## Análises e telemetria

### [rp-counters](/en/docs/modules/rp-counters)

Fornece o contrato de serviço para coletar e consultar contadores analíticos.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Fornece dados de painéis e visualizações analíticas para métricas da plataforma.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs é um repositório no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry é um repositório no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage é um repositório no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards é uma superfície no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs é uma superfície no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry é uma superfície no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage é uma superfície no domínio analytics. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

## Automação e orquestração

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Integra a automação da plataforma aos recursos do Kubernetes por meio de um cliente dedicado e de um contrato de serviço.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag é um repositório no domínio de automação. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller é um repositório no domínio de automação. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks é um repositório no domínio de automação. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation é a superfície no domínio de automação para fluxos de trabalho, agendamentos, endpoints de webhooks e seu histórico de execução.

- Dependências diretas: nenhuma
- Soluções: `automation`

## Domínio empresarial

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing é um repositório no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment é um repositório no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-events](/en/docs/modules/rp-events)

Fornece criação, armazenamento e recuperação de eventos empresariais.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-finance](/en/docs/modules/rp-finance)

Fornece operações financeiras para transações, resumos de períodos, fluxo de caixa, contas a receber e contas a pagar.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-orders](/en/docs/modules/rp-orders)

Fornece o contrato de serviço para criar, atualizar, listar e acompanhar pedidos empresariais.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests é um repositório no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews é um repositório no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales é um repositório no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff é um repositório no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-orders](/en/docs/modules/sf-orders)

Fornece a interface de vendas para listas de pedidos e solicitações, detalhes de pedidos, filtragem por status e painéis operacionais.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests é uma superfície no domínio empresarial. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

## Comunicações

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls é um repositório no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats é um repositório no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-community](/en/docs/modules/rp-community)

rp-community é um repositório no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify é um repositório no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-resonus](/en/docs/modules/rp-resonus)

Fornece configuração de comunicação para números de telefone gerenciados e configurações de gateway de LLM.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads é um repositório no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls é uma superfície no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats é uma superfície no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-community](/en/docs/modules/sf-community)

sf-community é uma superfície no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads é uma superfície no domínio de comunicações. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

## Conteúdo e documentos

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier é um repositório no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery é um repositório no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown é um repositório no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Fornece operações de armazenamento para arquivos de script, incluindo leitura, salvamento, geração de hash e exclusão.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-static](/en/docs/modules/rp-static)

Fornece o contrato de serviço para conteúdo estático e metadados de cache SSR.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct é um repositório no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Fornece a interface de classificação para navegar por entidades, mapeamentos e estruturas em árvore.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs é uma superfície no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery é uma superfície no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing é uma superfície no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown é uma superfície no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-static](/en/docs/modules/sf-static)

Fornece a interface de operações para inspecionar e limpar entradas do cache SSR estático.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct é uma superfície no domínio de conteúdo. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

## Arquivos e armazenamento

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors é uma lambda no domínio de dados. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps é um repositório no domínio de dados. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-files](/en/docs/modules/rp-files)

rp-files é um repositório no domínio de dados. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store é um repositório no domínio de dados. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps é uma superfície no domínio de dados. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-files](/en/docs/modules/sf-files)

sf-files é uma superfície no domínio de dados. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

## Provedores de entrega de mensagens

### [lm-push](/en/docs/modules/lm-push)

lm-push é uma lambda no domínio de provedores. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses é uma lambda no domínio de provedores. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms é uma lambda no domínio de provedores. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp é uma lambda no domínio de provedores. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

## Conversão de modelos

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor é uma lambda no domínio convertors. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

## Fluxos de trabalho

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Resume diálogos não processados de chats e chamadas com um LLM e, em seguida, armazena títulos, descrições e a classificação de ruído.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analisa um arquivo armazenado que não seja um arquivo compactado, produzindo prévias do modelo e estimativas de CNC ou impressão 3D quando compatível.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Expande um arquivo compactado enviado em uma coleção de arquivos armazenados para análise posterior.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze é um fluxo de trabalho no domínio da plataforma. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Processa arquivos enviados em lotes: expande arquivos compactados, identifica arquivos de modelo e cria uma solicitação de manufatura a partir deles.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze é um fluxo de trabalho no domínio da plataforma. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import é um fluxo de trabalho no domínio da plataforma. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach é um fluxo de trabalho no domínio da plataforma. Sua finalidade detalhada é mantida junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

## Dependências das soluções

- `ai`: `security`
- `analitycs`: `security`
- `content`: `security`
- `requests`: nenhuma dependência de solução
- `security`: nenhuma dependência de solução
