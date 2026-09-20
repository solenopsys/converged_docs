# wf-order-review-request

## Scopo

Contorno 2 del sistema di recensioni: chiedere al cliente, una volta, dopo che il lavoro è terminato.

Un'esecuzione individua un ordine terminato da abbastanza tempo, con un cliente a cui scrivere e a cui non è mai stato chiesto nulla; genera il suo link personale monouso per la recensione in
`rp-reviews`; e invia la richiesta tramite `lm-ses`.

## Perché questo è un workflow

La domanda "quali ordini terminati non hanno ancora ricevuto una richiesta" coinvolge due servizi a cui è vietato conoscersi: `rp-orders` non sa cosa sia una recensione, mentre `rp-reviews` conserva `orderId` come stringa opaca. Affiancare i due elenchi è esattamente ciò per cui serve un flow — e `rt.node` è ciò che permette alla generazione del link di sopravvivere a un riavvio senza generarne un secondo.

## Struttura

```
read-settings → list-finished (completed, updatedAt ≤ now − delay)
              → list-invites (which of those were already asked)
              → create-invite → send-email → mark-sent | mark-failed
```

Una sola email per esecuzione, così un indirizzo bloccato non ostacola mai la coda dietro di sé e la pianificazione decide la frequenza. `dryRun` esegue il rendering dell'email e non genera nulla: una prova che lasciasse dietro di sé un link attivo farebbe sì che la successiva esecuzione reale saltasse quell'ordine considerandolo già contattato.

Un'email rifiutata ritorna da `lm-ses` come `{ success: false }`, non come un'eccezione, quindi è un normale ramo che contrassegna l'invito come `failed` — non un confine di errore.

## Parametri

- `from` (obbligatorio) — indirizzo del mittente.
- `ses` (obbligatorio) — `SesCredentials`.
- `shopName` — inserito in `{{shopName}}` nei template.
- `delayHours` — sostituisce `ReviewSettings.requestDelayHours` per un recupero degli arretrati.
- `dryRun` — esegue il rendering e si arresta.

L'oggetto, il corpo, la base del link e il ritardo provengono da `reviews.getSettings()`, così il negozio può modificare autonomamente il testo senza intervenire su questo flow.

## Dipendenze dirette del modulo

- `g-orders`
- `g-reviews`
- `g-ses`

## Sorgente

`modules/workflows/wf-order-review-request`
