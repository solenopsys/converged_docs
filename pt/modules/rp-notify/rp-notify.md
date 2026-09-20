# rp-notify

## Objetivo

A distribuição única de notificações do ecossistema: qualquer domínio diz «informar o usuário» uma vez, e este módulo escolhe canais, política e tentativas. Os domínios nunca acessam diretamente as APIs SMTP/SMS/push.

## Modelo mental

O domínio emite uma intenção de notificação (quem, o quê, modelo, urgência) → o notify resolve canais e política de entrega → adaptadores de provedores externos fazem o envio real. Tentativas e fallback de canal vivem aqui, o significado da mensagem vive no domínio.

## Valor para o ecossistema

Um único repositório de «informar o usuário»:

- Modelos, canais, perfil e registros de envio por trás de uma única API.
- Qualquer domínio mantém seus textos de notificação e registros de entrega em um só lugar.

## Não objetivos

- Não a entrega de mensagens em si — apenas modelos, canais e registros de envio.
- Não tópicos de diálogo.

## Limite de responsabilidade

Possui a orquestração de notificações e a política de entrega; não possui adaptadores de envio específicos de provedor de baixo nível nem lógica de acionamento de domínio.

## Dependências diretas de módulos

- Nenhuma

## Pertinência à solução

- Não incluído em uma solução predefinida

## Fonte

`modules/repositories/communications/rp-notify`