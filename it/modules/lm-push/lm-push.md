# lm-push

## Scopo

Ramo push del fan-out di notifiche condiviso: trasporto push web/mobile dietro il contratto rp-notify.

## Valore per l'ecosistema

Promemoria in tempo reale per chat, ordini, richieste — recapitati insieme a email/SMS da un unico intento di notifica.

## Non obiettivi

Nessuna targetizzazione o logica di business — spetta a rp-notify e al dominio chiamante.

## Confine di responsabilità

Possiede i dettagli di integrazione del provider push; non possiede la logica di targetizzazione business delle notifiche.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alle soluzioni

- Non incluso in una soluzione predefinita

## Origine

`modules/lambdas/providers/lm-push`