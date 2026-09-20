# rp-requests

## Scopo

Acquisizione e ciclo di vita delle richieste di servizio: invio, transizioni di stato, allegati di file (tramite fileId) e promozione a ordini tramite wf-request-to-order. L'analisi viene eseguita tramite wf-request-analyze.

## Limite di responsabilità

Possiede il ciclo di vita delle richieste e le transizioni di stato; non possiede il trasporto di messaggistica, i byte dei file o l'esecuzione dell'analisi.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `requests`

## Origine

`modules/repositories/business/rp-requests`