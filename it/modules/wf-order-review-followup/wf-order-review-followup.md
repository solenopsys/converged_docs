# wf-order-review-followup

## Scopo

L'unico sollecito. Un'esecuzione prende un link per la recensione che è stato
inviato, è rimasto senza risposta per il numero di giorni configurato e non è
stato sollecitato per il numero massimo di volte consentito, e lo invia
nuovamente una volta.

## Perché questo è un workflow

La scelta non è: `reviews.findInvitesToFollowUp` è una domanda sugli inviti e
appartiene a `rp-reviews`. Ciò che questo flusso aggiunge è il nome dell'ordine
per l'email e l'invio — due servizi in un unico processo, che qui è la
definizione di un workflow.

## Cosa non fa mai deliberatamente

Non sollecita mai qualcuno che ha aperto il modulo. Ha letto la richiesta e ha
scelto di non scrivere; chiederglielo nuovamente è il modo in cui una richiesta
di recensione diventa spam. Questa condizione risiede nella query del repository
anziché in questo flusso, così un chiamante futuro non può dimenticarla.

Un sollecito rifiutato lascia l'invito `sent` anziché `failed`: la prima email
è stata effettivamente inviata e il cliente potrebbe ancora rispondere.

## Struttura

```
read-settings → find-due (sent, mai aperto, entro il limite consentito)
              → read-order (solo per il nome)
              → send-email → count-followup
```

Contare il sollecito è ciò che lo rende *unico*: la stessa query non restituirà
nuovamente quel link. `dryRun` prepara l'email e non conta nulla. `maxFollowups: 0`
disattiva completamente i solleciti e il flusso si interrompe prima di inviare
la richiesta.

## Parametri

- `from` (obbligatorio) — indirizzo del mittente.
- `ses` (obbligatorio) — `SesCredentials`.
- `shopName`, `delayDays`, `maxFollowups`, `dryRun` — override; i valori
  predefiniti provengono da `reviews.getSettings()`.

## Dipendenze dirette del modulo

- `g-orders`
- `g-reviews`
- `g-ses`

## Sorgente

`modules/workflows/wf-order-review-followup`
