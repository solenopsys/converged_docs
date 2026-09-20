# rp-counters

## Objetivo

Configuração por tenant de contadores externos de análise: armazena ID de rastreamento (GA4, GTM, Yandex Metrika, Meta Pixel) ou um snippet personalizado do head, para que o SSR possa injetar os scripts corretos por tenant.

## Modelo mental

O operador salva um contador (tipo, ID de rastreamento ou snippet, sinalizador de ativação) → o store mantém a configuração. O SSR lê os contadores ativados para o tenant atual e renderiza as tags correspondentes. Nenhum número é coletado aqui, apenas as configurações dos contadores.

## Valor para o ecossistema

Um único lugar para a integração de análises:

- Contadores externos (GA4, GTM, Metrika, Pixel) e snippets personalizados são configurados por tenant em vez de serem codificados por landing page.

## Não objetivos

- Não é armazenamento de eventos brutos.
- Não são diários de amostras numéricas.
- Não são registros de uso ou faturamento.
## Limite de responsabilidade

Possui as configurações de contadores (tipo, ID de rastreamento ou snippet, sinalizador de ativação); não coleta métricas, não agrega uso nem realiza cobrança.

## Dependências diretas de módulos

- Nenhuma

## Participação na solução

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-counters`