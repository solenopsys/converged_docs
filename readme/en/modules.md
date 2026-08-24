# Modules

- **AI and agents**
  - [mf-agents](#mf-agents)
  - [mf-assistants](#mf-assistants)
- **Access and security**
  - [mf-auth](#mf-auth)
- **Communications**
  - [mf-calls](#mf-calls)
  - [mf-chats](#mf-chats)
- **Content and documents**
  - [mf-classifier](#mf-classifier)
- **Communications**
  - [mf-community](#mf-community)
- **AI and agents**
  - [mf-contexts](#mf-contexts)
- **Automation and orchestration**
  - [mf-dag](#mf-dag)
- **Analytics and telemetry**
  - [mf-dasboards](#mf-dasboards)
- **Content and documents**
  - [mf-docs](#mf-docs)
- **Files and storage**
  - [mf-dumps](#mf-dumps)
- **AI and agents**
  - [mf-functions](#mf-functions)
- **Content and documents**
  - [mf-galery](#mf-galery)
  - [mf-landing](#mf-landing)
- **Analytics and telemetry**
  - [mf-logs](#mf-logs)
- **Content and documents**
  - [mf-markdown](#mf-markdown)
- **Business domain**
  - [mf-orders](#mf-orders)
  - [mf-requests](#mf-requests)
- **Content and documents**
  - [mf-scripts](#mf-scripts)
- **Access and security**
  - [mf-secrets](#mf-secrets)
- **Automation and orchestration**
  - [mf-sheduller](#mf-sheduller)
- **Content and documents**
  - [mf-static](#mf-static)
  - [mf-struct](#mf-struct)
- **Analytics and telemetry**
  - [mf-telemetry](#mf-telemetry)
- **Communications**
  - [mf-threads](#mf-threads)
- **Analytics and telemetry**
  - [mf-usage](#mf-usage)
- **Automation and orchestration**
  - [mf-webhooks](#mf-webhooks)
- **Access and security**
  - [ms-access](#ms-access)
- **AI and agents**
  - [ms-agent](#ms-agent)
  - [ms-assistant](#ms-assistant)
- **Access and security**
  - [ms-auth](#ms-auth)
- **Business domain**
  - [ms-billing](#ms-billing)
- **Communications**
  - [ms-calls](#ms-calls)
  - [ms-chats](#ms-chats)
- **Content and documents**
  - [ms-classifier](#ms-classifier)
- **Communications**
  - [ms-community](#ms-community)
- **AI and agents**
  - [ms-contexts](#ms-contexts)
- **Analytics and telemetry**
  - [ms-counters](#ms-counters)
- **Automation and orchestration**
  - [ms-dag](#ms-dag)
- **Analytics and telemetry**
  - [ms-dashboard](#ms-dashboard)
- **Files and storage**
  - [ms-dumps](#ms-dumps)
- **Access and security**
  - [ms-environment](#ms-environment)
- **Business domain**
  - [ms-equipment](#ms-equipment)
  - [ms-events](#ms-events)
- **Files and storage**
  - [ms-files](#ms-files)
- **Business domain**
  - [ms-finance](#ms-finance)
- **AI and agents**
  - [ms-functions](#ms-functions)
- **Content and documents**
  - [ms-galery](#ms-galery)
- **Access and security**
  - [ms-identity](#ms-identity)
- **Automation and orchestration**
  - [ms-kubernetes](#ms-kubernetes)
- **Analytics and telemetry**
  - [ms-logs](#ms-logs)
- **Content and documents**
  - [ms-markdown](#ms-markdown)
- **Model conversion**
  - [ms-modelconvertor](#ms-modelconvertor)
- **Communications**
  - [ms-notify](#ms-notify)
- **Access and security**
  - [ms-oauth](#ms-oauth)
- **Business domain**
  - [ms-orders](#ms-orders)
- **Message delivery providers**
  - [ms-push](#ms-push)
- **Business domain**
  - [ms-requests](#ms-requests)
- **Communications**
  - [ms-resonus](#ms-resonus)
- **Business domain**
  - [ms-reviews](#ms-reviews)
  - [ms-sales](#ms-sales)
- **Content and documents**
  - [ms-scripts](#ms-scripts)
- **Access and security**
  - [ms-secrets](#ms-secrets)
- **Message delivery providers**
  - [ms-ses](#ms-ses)
- **Automation and orchestration**
  - [ms-sheduller](#ms-sheduller)
- **Message delivery providers**
  - [ms-sms](#ms-sms)
  - [ms-smtp](#ms-smtp)
- **Business domain**
  - [ms-staff](#ms-staff)
- **Content and documents**
  - [ms-static](#ms-static)
- **Files and storage**
  - [ms-store](#ms-store)
- **Content and documents**
  - [ms-struct](#ms-struct)
- **Analytics and telemetry**
  - [ms-telemetry](#ms-telemetry)
- **Communications**
  - [ms-threads](#ms-threads)
- **Analytics and telemetry**
  - [ms-usage](#ms-usage)
- **Automation and orchestration**
  - [ms-webhooks](#ms-webhooks)
- ****
  - [wf-dialogue-summary](#wf-dialogue-summary)
  - [wf-file-analysis](#wf-file-analysis)
  - [wf-file-analyze](#wf-file-analyze)
  - [wf-file-unpack](#wf-file-unpack)

## AI and agents

### mf-agents

#### Purpose

Owns AI Agents UI: agent catalog/list pages, agent config forms, run/trigger controls, and execution status panels.

#### Responsibility boundary

Controls agent management and agent-run experience in UI; does not own global prompt-provider settings or platform auth screens.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microfrontends/ai/mf-agents`

### mf-assistants

#### Purpose

Owns Assistants UI: assistant chat/workspace views, assistant configuration panels, and assistant session interaction components.

#### Responsibility boundary

Controls assistant user experience and assistant-scoped state; does not own shared identity/profile UI or infrastructure telemetry pages.

#### Direct module dependencies

- `mf-requests`

#### Solution membership

- `ai`

#### Source

`modules/microfrontends/ai/mf-assistants`

## Access and security

### mf-auth

#### Purpose

Owns Auth UI: sign-in/sign-up/reset flows, session/security screens, and authentication guard/redirect UX behavior.

#### Responsibility boundary

Controls authentication-related frontend flows and auth UI state; does not own identity profile management beyond auth scope or business-domain pages.

#### Direct module dependencies

- None

#### Solution membership

- `security`

#### Source

`modules/microfrontends/sequrity/mf-auth`

## Communications

### mf-calls

#### Purpose

Owns Calls UI: call session screens, call controls, call participant/status panels, and call history presentation widgets.

#### Responsibility boundary

Controls call-related interaction surfaces and call session state in UI; does not own thread messaging UI or provider transport settings.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microfrontends/communications/mf-calls`

### mf-chats

#### Purpose

Owns Charts UI: reusable communication/report chart widgets, chart configuration controls, and chart drill-down interactions.

#### Responsibility boundary

Controls chart-rendering UX components for this module scope; does not own source event ingestion or global dashboard layout shell.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microfrontends/communications/mf-chats`

## Content and documents

### mf-classifier

#### Purpose

Provides the mf-classifier capability in the content domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/content/mf-classifier`

## Communications

### mf-community

#### Purpose

Owns Community UI: community feed/list pages, community post/detail views, and moderation/community action controls.

#### Responsibility boundary

Controls community-specific user interactions and layouts; does not own external social connector settings or direct call interfaces.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/communications/mf-community`

## AI and agents

### mf-contexts

#### Purpose

Provides the mf-contexts capability in the ai domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microfrontends/ai/mf-contexts`

## Automation and orchestration

### mf-dag

#### Purpose

Owns DAG Automation UI: workflow graph editor/viewer, node/link configuration dialogs, and run-status monitoring screens.

#### Responsibility boundary

Controls DAG visualization and workflow editing experience; does not own scheduler-wide cron management UI or webhook endpoint management.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/automation/mf-dag`

## Analytics and telemetry

### mf-dasboards

#### Purpose

Owns Analytics Dashboard UI: overview dashboards, KPI cards, trend charts, and dashboard-level filters/date ranges.

#### Responsibility boundary

Controls dashboard composition and analytics overview interactions; does not own raw log explorer UI or telemetry event-detail tooling.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/analytics/mf-dasboards`

## Content and documents

### mf-docs

#### Purpose

Owns Docs UI: document browsing, document detail views, editing/preview interfaces, and documentation navigation components.

#### Responsibility boundary

Controls document-centered frontend workflows and UI states; does not own markdown engine internals or binary media storage tooling.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microfrontends/content/mf-docs`

## Files and storage

### mf-dumps

#### Purpose

Owns Data Dumps UI: export/dump creation forms, dump history tables, download actions, and dump status/progress indicators.

#### Responsibility boundary

Controls user-facing dump/export workflows and status presentation; does not own storage/archive backend execution internals.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/data/mf-dumps`

## AI and agents

### mf-functions

#### Purpose

Provides the mf-functions capability in the ai domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/ai/mf-functions`

## Content and documents

### mf-galery

#### Purpose

Owns Gallery UI: media gallery grids, media preview/detail views, gallery organization controls, and gallery filtering/search.

#### Responsibility boundary

Controls gallery browsing and media curation interactions; does not own backend transcoding pipelines or storage-provider internals.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microfrontends/content/mf-galery`

### mf-landing

#### Purpose

Owns Landing UI: landing pages, hero/section composition, and public-facing content presentation blocks.

#### Responsibility boundary

Controls landing-page layouts and interaction behavior; does not own authenticated admin panels or analytics data collection internals.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microfrontends/content/mf-landing`

## Analytics and telemetry

### mf-logs

#### Purpose

Owns Logs UI: log stream/table views, log search/filter controls, and log detail drill-down panels for operators.

#### Responsibility boundary

Controls log exploration and troubleshooting UX; does not own product usage dashboards or agent/business domain pages.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microfrontends/analytics/mf-logs`

## Content and documents

### mf-markdown

#### Purpose

Owns Markdown UI: markdown editor surfaces, live preview panels, markdown content formatting controls, and publish-ready views.

#### Responsibility boundary

Controls markdown authoring/presentation UX; does not own document permissions/auth or media conversion infrastructure.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microfrontends/content/mf-markdown`

## Business domain

### mf-orders

#### Purpose

Provides the mf-orders capability in the business domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/business/mf-orders`

### mf-requests

#### Purpose

Owns Requests UI: request inbox/list screens, request detail/timeline views, and request status/action forms.

#### Responsibility boundary

Controls request lifecycle user interactions in the frontend; does not own chats/threads modules or billing execution pages.

#### Direct module dependencies

- None

#### Solution membership

- `requests`

#### Source

`modules/microfrontends/business/mf-requests`

## Content and documents

### mf-scripts

#### Purpose

Provides the mf-scripts capability in the content domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/content/mf-scripts`

## Access and security

### mf-secrets

#### Purpose

Provides the mf-secrets capability in the sequrity domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/sequrity/mf-secrets`

## Automation and orchestration

### mf-sheduller

#### Purpose

Owns Scheduler UI: recurring job configuration pages, schedule calendars/tables, and job run history/next-run indicators.

#### Responsibility boundary

Controls schedule creation and scheduling-state visualization; does not own DAG graph editor or domain-specific task content editors.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/automation/mf-sheduller`

## Content and documents

### mf-static

#### Purpose

Provides the mf-static capability in the content domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/content/mf-static`

### mf-struct

#### Purpose

Owns Structured Content UI: schema-driven content forms, structured block editors, and structured content preview/validation views.

#### Responsibility boundary

Controls structured content editing experiences and UI validation states; does not own final channel delivery adapters.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microfrontends/content/mf-struct`

## Analytics and telemetry

### mf-telemetry

#### Purpose

Owns Telemetry UI: technical signal views, metrics graphs, event timelines, and service-health visual components.

#### Responsibility boundary

Controls telemetry-specific visualizations and filters; does not own billing/usage reporting UX or shell-level navigation.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microfrontends/analytics/mf-telemetry`

## Communications

### mf-threads

#### Purpose

Owns Threads UI: threaded conversation lists, thread detail panels, reply composers, and thread state indicators.

#### Responsibility boundary

Controls thread-centric communication experience; does not own push/email transport configuration or external social channel adapters.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microfrontends/communications/mf-threads`

## Analytics and telemetry

### mf-usage

#### Purpose

Owns Usage UI: feature-consumption charts, usage counters, quota/limit displays, and usage period comparison screens.

#### Responsibility boundary

Controls usage analytics presentation and interaction; does not own charge/payment screens or low-level telemetry ingestion tools.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microfrontends/analytics/mf-usage`

## Automation and orchestration

### mf-webhooks

#### Purpose

Owns Webhooks UI: webhook endpoint list/forms, event subscription settings, delivery history, and retry controls.

#### Responsibility boundary

Controls webhook management flows and delivery observability UX; does not own downstream business processing screens.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microfrontends/automation/mf-webhooks`

## Access and security

### ms-access

#### Purpose

Manages access-control rules and permission checks.

#### Responsibility boundary

Owns authorization policy evaluation and access scopes; does not own identity proofing/authentication login.

#### Direct module dependencies

- None

#### Solution membership

- `security`

#### Source

`modules/microservices/sequrity/ms-access`

## AI and agents

### ms-agent

#### Purpose

Runs autonomous AI-agent workflows and orchestrates multi-step LLM tasks.

#### Responsibility boundary

Owns agent execution logic and task orchestration; does not own core auth, billing, or long-term data storage.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microservices/ai/ms-agent`

### ms-assistant

#### Purpose

Provides assistant-style AI interactions for end users and internal tools.

#### Responsibility boundary

Owns assistant dialog behavior and request handling; does not own model provider infrastructure or user identity.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microservices/ai/ms-assistant`

## Access and security

### ms-auth

#### Purpose

Handles authentication workflows and credential/session validation.

#### Responsibility boundary

Owns auth flows and token/session issuance logic; does not own third-party OAuth provider adapters outside auth scope.

#### Direct module dependencies

- None

#### Solution membership

- `security`

#### Source

`modules/microservices/sequrity/ms-auth`

## Business domain

### ms-billing

#### Purpose

Handles billing domain operations such as plans, charges, and billing state.

#### Responsibility boundary

Owns billing workflows and billing records; does not own external payment gateway internals.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-billing`

## Communications

### ms-calls

#### Purpose

Provides call-related communication workflows and call session handling.

#### Responsibility boundary

Owns call-session domain logic and call metadata; does not own external telecom provider infrastructure.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microservices/communications/ms-calls`

### ms-chats

#### Purpose

Generates and serves chart-oriented communication or reporting artifacts.

#### Responsibility boundary

Owns chart composition and chart data shaping; does not own raw analytics event collection.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microservices/communications/ms-chats`

## Content and documents

### ms-classifier

#### Purpose

Classifies incoming content/items into categories, labels, or intents.

#### Responsibility boundary

Owns classification logic and label assignment; does not own source content ingestion pipelines.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/content/ms-classifier`

## Communications

### ms-community

#### Purpose

Supports community-level interactions and social communication features.

#### Responsibility boundary

Owns community entities and interactions; does not own third-party social network connectors.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/communications/ms-community`

## AI and agents

### ms-contexts

#### Purpose

Provides the ms-contexts capability in the ai domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microservices/ai/ms-contexts`

## Analytics and telemetry

### ms-counters

#### Purpose

Provides the ms-counters capability in the analytics domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microservices/analytics/ms-counters`

## Automation and orchestration

### ms-dag

#### Purpose

Executes DAG-based automation pipelines and dependency-aware jobs.

#### Responsibility boundary

Owns workflow graph scheduling/execution; does not own domain-specific business rules inside downstream services.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/automation/ms-dag`

## Analytics and telemetry

### ms-dashboard

#### Purpose

Provides the ms-dashboard capability in the analytics domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/analytics/ms-dashboard`

## Files and storage

### ms-dumps

#### Purpose

Creates and manages data dumps/export snapshots.

#### Responsibility boundary

Owns dump generation, packaging, and retrieval metadata; does not own long-term archival platform.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/data/ms-dumps`

## Access and security

### ms-environment

#### Purpose

Provides the ms-environment capability in the sequrity domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/sequrity/ms-environment`

## Business domain

### ms-equipment

#### Purpose

Manages equipment entities, metadata, and related lifecycle operations.

#### Responsibility boundary

Owns equipment catalog and state transitions; does not own logistics carrier execution.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-equipment`

### ms-events

#### Purpose

Provides the ms-events capability in the business domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-events`

## Files and storage

### ms-files

#### Purpose

Provides file metadata APIs and file-management workflows.

#### Responsibility boundary

Owns file records and file-level operations; does not own object storage implementation details.

#### Direct module dependencies

- None

#### Solution membership

- `requests`

#### Source

`modules/microservices/data/ms-files`

## Business domain

### ms-finance

#### Purpose

Provides the ms-finance capability in the business domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-finance`

## AI and agents

### ms-functions

#### Purpose

Provides the ms-functions capability in the ai domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/ai/ms-functions`

## Content and documents

### ms-galery

#### Purpose

Manages gallery-style media collections and related metadata.

#### Responsibility boundary

Owns gallery entities and organization logic; does not own binary object storage backend.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microservices/content/ms-galery`

## Access and security

### ms-identity

#### Purpose

Maintains identity profiles and identity-linked core attributes.

#### Responsibility boundary

Owns identity records and identity lifecycle state; does not own fine-grained permission policies.

#### Direct module dependencies

- None

#### Solution membership

- `security`

#### Source

`modules/microservices/sequrity/ms-identity`

## Automation and orchestration

### ms-kubernetes

#### Purpose

Provides the ms-kubernetes capability in the automation domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/automation/ms-kubernetes`

## Analytics and telemetry

### ms-logs

#### Purpose

Collects and stores operational logs for platform services.

#### Responsibility boundary

Owns log ingestion and retrieval APIs; does not own business metrics or tracing strategy.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microservices/analytics/ms-logs`

## Content and documents

### ms-markdown

#### Purpose

Processes markdown content, rendering/transformation workflows, and related APIs.

#### Responsibility boundary

Owns markdown conversion/parsing behavior; does not own rich media transcoding.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microservices/content/ms-markdown`

## Model conversion

### ms-modelconvertor

#### Purpose

Converts models/data formats between internal and external representations.

#### Responsibility boundary

Owns conversion/transformation routines; does not own upstream model training or downstream serving.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/convertors/ms-modelconvertor`

## Communications

### ms-notify

#### Purpose

Coordinates notification workflows across channels.

#### Responsibility boundary

Owns notification orchestration and delivery policy; does not own low-level provider-specific sending adapters.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/communications/ms-notify`

## Access and security

### ms-oauth

#### Purpose

Implements OAuth-specific authorization flows and provider handshakes.

#### Responsibility boundary

Owns OAuth grant flow handling and token exchange; does not own non-OAuth authentication methods.

#### Direct module dependencies

- None

#### Solution membership

- `security`

#### Source

`modules/microservices/sequrity/ms-oauth`

## Business domain

### ms-orders

#### Purpose

Provides the ms-orders capability in the business domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-orders`

## Message delivery providers

### ms-push

#### Purpose

Provider adapter for push-notification delivery.

#### Responsibility boundary

Owns push provider integration details; does not own notification business targeting logic.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/providers/ms-push`

## Business domain

### ms-requests

#### Purpose

Processes service/business requests submitted by users or organizations.

#### Responsibility boundary

Owns request lifecycle and status transitions; does not own messaging transport or file storage internals.

#### Direct module dependencies

- None

#### Solution membership

- `requests`

#### Source

`modules/microservices/business/ms-requests`

## Communications

### ms-resonus

#### Purpose

Provides the ms-resonus capability in the communications domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/communications/ms-resonus`

## Business domain

### ms-reviews

#### Purpose

Stores and manages user or partner reviews and moderation-related metadata.

#### Responsibility boundary

Owns review entities and review state; does not own community thread infrastructure.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-reviews`

### ms-sales

#### Purpose

Handles sales-domain entities, sales flows, and related metrics preparation.

#### Responsibility boundary

Owns sales lifecycle and sales data logic; does not own payment gateway transaction processing.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-sales`

## Content and documents

### ms-scripts

#### Purpose

Provides the ms-scripts capability in the content domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/content/ms-scripts`

## Access and security

### ms-secrets

#### Purpose

Provides the ms-secrets capability in the sequrity domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/sequrity/ms-secrets`

## Message delivery providers

### ms-ses

#### Purpose

Provider adapter for AWS SES email delivery.

#### Responsibility boundary

Owns SES-specific sending integration and mapping; does not own email template authoring domain.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/providers/ms-ses`

## Automation and orchestration

### ms-sheduller

#### Purpose

Stores and serves automation schedule data and execution history.

#### Responsibility boundary

Owns CRUD/list/stats for cron entries and history records; does not execute workflows, timers, retries, or background dispatch.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/automation/ms-sheduller`

## Message delivery providers

### ms-sms

#### Purpose

Provider adapter for SMS delivery channels.

#### Responsibility boundary

Owns SMS provider connectivity and payload formatting; does not own campaign/business segmentation rules.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/providers/ms-sms`

### ms-smtp

#### Purpose

Provider adapter for SMTP-based email delivery.

#### Responsibility boundary

Owns SMTP transport and protocol-level delivery handling; does not own high-level notification orchestration.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/providers/ms-smtp`

## Business domain

### ms-staff

#### Purpose

Manages staff records, roles, and staff-centric domain operations.

#### Responsibility boundary

Owns staff domain data and workflows; does not own authentication credential issuance.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/business/ms-staff`

## Content and documents

### ms-static

#### Purpose

Provides the ms-static capability in the content domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/content/ms-static`

## Files and storage

### ms-store

#### Purpose

Implements generic storage-domain operations for service data.

#### Responsibility boundary

Owns store-facing data access APIs in this domain; does not own business semantics of calling services.

#### Direct module dependencies

- None

#### Solution membership

- `requests`

#### Source

`modules/microservices/data/ms-store`

## Content and documents

### ms-struct

#### Purpose

Builds and serves structured content representations used by other services.

#### Responsibility boundary

Owns structure modeling and schema-level shaping; does not own final channel-specific rendering.

#### Direct module dependencies

- None

#### Solution membership

- `content`

#### Source

`modules/microservices/content/ms-struct`

## Analytics and telemetry

### ms-telemetry

#### Purpose

Captures telemetry events and technical health signals from services.

#### Responsibility boundary

Owns telemetry event intake and normalization; does not own product analytics definitions.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microservices/analytics/ms-telemetry`

## Communications

### ms-threads

#### Purpose

Manages threaded conversations and related message context.

#### Responsibility boundary

Owns thread lifecycle and thread-level metadata; does not own transport gateways for email/SMS/push.

#### Direct module dependencies

- None

#### Solution membership

- `ai`

#### Source

`modules/microservices/communications/ms-threads`

## Analytics and telemetry

### ms-usage

#### Purpose

Tracks usage counters and consumption metrics for product features.

#### Responsibility boundary

Owns usage measurement and aggregation; does not own invoicing or payment execution.

#### Direct module dependencies

- None

#### Solution membership

- `analitycs`

#### Source

`modules/microservices/analytics/ms-usage`

## Automation and orchestration

### ms-webhooks

#### Purpose

Receives and dispatches webhook events for external integrations.

#### Responsibility boundary

Owns webhook transport, validation, and delivery attempts; does not own target-system business processing.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/microservices/automation/ms-webhooks`

## 

### wf-dialogue-summary

#### Purpose

Provides the wf-dialogue-summary capability in the workflow domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/workflows/wf-dialogue-summary`

### wf-file-analysis

#### Purpose

Provides the wf-file-analysis capability in the workflow domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- `requests`

#### Source

`modules/workflows/wf-file-analysis`

### wf-file-analyze

#### Purpose

Provides the wf-file-analyze capability in the workflow domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- Not included in a predefined solution

#### Source

`modules/workflows/wf-file-analyze`

### wf-file-unpack

#### Purpose

Provides the wf-file-unpack capability in the workflow domain.

#### Responsibility boundary

The module boundary is defined by its public contracts and implementation directory.

#### Direct module dependencies

- None

#### Solution membership

- `requests`

#### Source

`modules/workflows/wf-file-unpack`
