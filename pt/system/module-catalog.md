# Catálogo de módulos

Este índice é gerado a partir do registro de módulos Converged. Cada entrada aponta para a documentação mantida por esse módulo; as dependências são obtidas do manifesto do pacote do workspace, e a participação nas soluções vem de `modules/solutions`.

## Acesso e segurança

### [lm-secrets](/en/docs/modules/lm-secrets)

Fornece o contrato de serviço para armazenar, recuperar e excluir valores de segredos nomeados.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-access](/en/docs/modules/rp-access)

rp-access é um repositório no domínio de segurança. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth é um repositório no domínio de segurança. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-environment](/en/docs/modules/rp-environment)

Armazena e recupera a configuração de ambiente associada aos usuários da plataforma.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity é um repositório no domínio de segurança. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth é um repositório no domínio de segurança. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth é uma superfície no domínio de segurança. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Fornece a interface de administração para criar, visualizar, atualizar e excluir registros de segredos nomeados.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-team](/en/docs/modules/sf-team)

sf-team é uma superfície no domínio de segurança. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

## IA e agentes

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant é um repositório no domínio de IA. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Fornece armazenamento e recuperação de contextos de IA nomeados, incluindo suas variantes de idioma.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants é uma superfície no domínio de IA. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: `sf-requests`
- Soluções: `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Fornece o espaço de trabalho de IA para listar, editar e salvar contextos nomeados em vários idiomas.

- Dependências diretas: nenhuma
- Soluções: `ai`

## Análises e telemetria

### [rp-counters](/en/docs/modules/rp-counters)

Armazena configurações de contadores de análise externa por tenant (ids de rastreamento, snippets de head) para injeção SSR.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Armazena fixações de indicadores do painel pessoal: quais widgets um usuário fixou, sua ordem e metadados de exibição.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs é um repositório no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry é um repositório no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage é um repositório no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards é uma superfície no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs é uma superfície no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry é uma superfície no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage é uma superfície no domínio de análises. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `analitycs`

## Automação e orquestração

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Integra a automação da plataforma com recursos Kubernetes por meio de um cliente dedicado e contrato de serviço.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag é um repositório no domínio de automação. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `automation`, `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller é um repositório no domínio de automação. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `automation`

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks é um repositório no domínio de automação. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `automation`

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation é uma superfície no domínio de automação. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `automation`

## Domínio de negócios

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `billing`

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [rp-events](/en/docs/modules/rp-events)

Fornece criação, armazenamento e recuperação de eventos de negócios.

- Dependências diretas: nenhuma
- Soluções: `production`

### [rp-finance](/en/docs/modules/rp-finance)

Fornece operações financeiras para transações, resumos de período, fluxo de caixa, contas a receber e contas a pagar.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-invoices](/en/docs/modules/rp-invoices)

rp-invoices é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `billing`

### [rp-metering](/en/docs/modules/rp-metering)

rp-metering é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `billing`

### [rp-orders](/en/docs/modules/rp-orders)

Fornece o contrato de serviço para criar, atualizar, listar e acompanhar pedidos comerciais.

- Dependências diretas: nenhuma
- Soluções: `production`

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff é um repositório no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [sf-equipment](/en/docs/modules/sf-equipment)

sf-equipment é uma superfície no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [sf-orders](/en/docs/modules/sf-orders)

Fornece a interface de vendas para listas de pedidos e solicitações, detalhes de pedidos, filtragem por status e painéis operacionais.

- Dependências diretas: nenhuma
- Soluções: `production`

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests é uma superfície no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [sf-reviews](/en/docs/modules/sf-reviews)

sf-reviews é uma superfície no domínio de negócios. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

## Comunicações

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls é um repositório no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats é um repositório no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`

### [rp-community](/en/docs/modules/rp-community)

rp-community é um repositório no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify é um repositório no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [rp-resonus](/en/docs/modules/rp-resonus)

Fornece configuração de comunicação para números de telefone gerenciados e definições de gateway LLM.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-support](/en/docs/modules/rp-support)

rp-support é um repositório no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads é um repositório no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`, `communications`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls é uma superfície no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats é uma superfície no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`

### [sf-community](/en/docs/modules/sf-community)

sf-community é uma superfície no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`

### [sf-support](/en/docs/modules/sf-support)

sf-support é uma superfície no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads é uma superfície no domínio de comunicações. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `ai`, `communications`

## Conteúdo e documentos

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier é um repositório no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery é um repositório no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown é um repositório no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Fornece operações de armazenamento para arquivos de script, incluindo leitura, salvamento, hash e exclusão.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-static](/en/docs/modules/rp-static)

Fornece o contrato de serviço para conteúdo estático e metadados de cache SSR.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct é um repositório no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Fornece a interface do classificador para navegar por entidades, mapeamentos e estruturas de árvore.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs é uma superfície no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery é uma superfície no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing é uma superfície no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown é uma superfície no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-static](/en/docs/modules/sf-static)

Fornece a interface de operações para inspecionar e limpar entradas estáticas de cache SSR.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct é uma superfície no domínio de conteúdo. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

## Arquivos e armazenamento

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors é um lambda no domínio de dados. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps é um repositório no domínio de dados. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [rp-files](/en/docs/modules/rp-files)

rp-files é um repositório no domínio de dados. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `communications`, `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store é um repositório no domínio de dados. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps é uma superfície no domínio de dados. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [sf-files](/en/docs/modules/sf-files)

sf-files é uma superfície no domínio de dados. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

## Provedores de entrega de mensagens

### [lm-lemonsqueezy](/en/docs/modules/lm-lemonsqueezy)

lm-lemonsqueezy é um lambda no domínio de provedores. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `billing`

### [lm-push](/en/docs/modules/lm-push)

lm-push é um lambda no domínio de provedores. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses é um lambda no domínio de provedores. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms é um lambda no domínio de provedores. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp é um lambda no domínio de provedores. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

## Conversão de modelos

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor é um lambda no domínio de conversores. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

## Fluxos de trabalho

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Resume diálogos de chat e chamadas não processados com um LLM e, em seguida, armazena títulos, descrições e classificação de ruído.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [wf-equipment-incident](/en/docs/modules/wf-equipment-incident)

wf-equipment-incident é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analisa um arquivo armazenado não compactado, produzindo visualizações de modelo e estimativas CNC ou de impressão 3D quando suportado.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Expande um arquivo compactado enviado em uma coleção de arquivos armazenados para análise posterior.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Processa arquivos enviados em lotes: expande arquivos compactados, identifica arquivos de modelo e cria uma solicitação de fabricação a partir deles.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-order-review-followup](/en/docs/modules/wf-order-review-followup)

wf-order-review-followup é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [wf-order-review-request](/en/docs/modules/wf-order-review-request)

wf-order-review-request é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [wf-payment-settle](/en/docs/modules/wf-payment-settle)

wf-payment-settle é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `billing`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `requests`

### [wf-request-to-order](/en/docs/modules/wf-request-to-order)

wf-request-to-order é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: nenhuma

### [wf-team-invite](/en/docs/modules/wf-team-invite)

wf-team-invite é um fluxo de trabalho no domínio da plataforma. Seu propósito detalhado é mantido junto ao código-fonte do módulo.

- Dependências diretas: nenhuma
- Soluções: `production`

## Dependências de solução

- `ai`: `security`
- `analitycs`: `security`
- `automation`: `security`
- `billing`: `security`
- `communications`: `security`
- `content`: `security`
- `production`: `security`, `analitycs`, `requests`
- `requests`: sem dependências de solução
- `security`: sem dependências de solução
