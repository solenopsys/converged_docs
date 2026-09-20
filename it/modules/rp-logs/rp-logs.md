# rp-logs

## Scopo

Il singolo diario in sola aggiunta dell'ecosistema: qualsiasi servizio, apparecchiatura
o flusso di lavoro scrive qui «cosa è successo» invece di creare un proprio archivio
di log. Scritture economiche, letture per tempo/fonte.

## Modello mentale

Il produttore invia un evento (tempo, fonte, livello, testo/payload) → arriva sullo
stream condiviso. Il consumatore legge una porzione per fonte o intervallo. Nessuna
aggregazione o avviso all'interno — solo la registrazione del fatto.

## Valore per l'ecosistema

Un unico stream riutilizzato da tutti:

- Servizi: log operativi senza storage proprio per `rp-*`.
- Apparecchiature: log di macchine/dispositivi — stessa API, fonte diversa, dalle stampanti 3D
  a qualsiasi modulo o sistema esterno.
- Qualsiasi produttore scrive «cosa è successo» in un unico luogo invece di creare
  il proprio archivio di log; audit e revisione leggono un'unica cronologia.

## Non obiettivi

- Niente contatori o aggregati.
- Niente campioni numerici o record di utilizzo.
- Niente tracciamento di chiamate distribuite o avvisi.
## Confine di responsabilità

Possiede le API di ingestione e recupero dei log; non possiede metriche di business,
aggregazione, avvisi o strategia di tracciamento.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-logs`