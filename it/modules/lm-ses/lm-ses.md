# lm-ses

## Scopo

Ramo SES del fan-out di notifiche condiviso: trasporto e-mail AWS dietro il contratto rp-notify.

## Valore per l'ecosistema

Le e-mail bulk e transazionali (inviti a recensioni, aggiornamenti ordini, inviti al team) passano attraverso un'unica integrazione SES. Le credenziali vengono risolte tramite lm-secrets.

## Non obiettivi

Nessuna policy di canale o modelli — competenza di rp-notify e del dominio chiamante.


## Confine di responsabilità

Possiede l'integrazione di invio e la mappatura specifiche di SES; non possiede il dominio di creazione dei modelli e-mail.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Fonte

`modules/lambdas/providers/lm-ses`