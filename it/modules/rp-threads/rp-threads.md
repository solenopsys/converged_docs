# rp-threads

## Scopo

Il singolo livello conversazionale dell'ecosistema: qualsiasi modulo in cui persone
o agenti si scambiano messaggi non conserva messaggi propri — detiene un
`threadId`, e il dialogo stesso vive qui.

## Modello mentale

L'entità (stanza di chat, argomento del forum, chiamata, richiesta) memorizza solo un `threadId`.
Tutti i messaggi, l'ordinamento e il contesto vivono nel thread. Creare un'entità
= generare un `threadId` e consegnarlo al chiamante, che lo registra.

## Valore per l'ecosistema

Un unico formato di dialogo ovunque:

- Thread e messaggi ordinati dietro un'unica API, identificati da thread id opaco.
- Qualsiasi entità allega una discussione senza proprie tabelle di messaggi.

## Non obiettivi

- Non stanze di chat o argomenti di forum — solo i thread di messaggi sottostanti.
- Non consegna di notifiche o riepiloghi di dialoghi.
## Confine di responsabilità

Possiede il ciclo di vita dei thread, l'ordinamento dei messaggi e i metadati a livello di thread; non
possiede stanze/argomenti, appartenenza o gateway di trasporto per
email/SMS/push.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `ai`

## Origine

`modules/repositories/communications/rp-threads`