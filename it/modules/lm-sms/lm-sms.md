# lm-sms

## Scopo

Ramo SMS del fan-out di notifiche condiviso: trasporto provider dietro il contratto rp-notify.

## Valore dell'ecosistema

Ping urgenti (incidenti, codici di invito, cambi di stato) raggiungono i telefoni mentre altri canali portano la forma estesa. Stessa API di intenti di email/push.

## Non obiettivi

Nessuna regola di campagna o segmentazione — decide il dominio chiamante.

## Confine di responsabilità

Possiede la connettività del provider SMS e la formattazione del payload; non possiede regole di segmentazione campagna/business.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Fonte

`modules/lambdas/providers/lm-sms`