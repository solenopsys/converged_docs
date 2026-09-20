# lm-smtp

## Scopo

Ramo SMTP del fan-out di notifiche condiviso: semplice trasporto del provider dietro il contratto rp-notify.

## Valore dell'ecosistema

Il dominio emette un intento di notifica una sola volta tramite rp-notify → questo adattatore lo recapita via SMTP. Sostituire o aggiungere provider di posta elettronica non tocca mai i domini.

## Non obiettivi

Nessuna policy di canale, riprova o modello — questo spetta a rp-notify e al dominio chiamante.


## Confine di responsabilità

Possiede il trasporto SMTP e la gestione della consegna a livello di protocollo; non possiede l'orchestrazione delle notifiche di alto livello.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Fonte

`modules/lambdas/providers/lm-smtp`