# rp-calls

## Scopo

Sessioni di chiamata e metadati: configurazione, partecipanti e collegamento a registrazioni (flussi di blocchi in rp-store) e trascrizioni/thread (rp-threads). Riepiloghi tramite wf-dialogue-summary.

## Confine di responsabilità

Possiede la logica di dominio della sessione di chiamata e i metadati di chiamata; non possiede l'infrastruttura del provider di telecomunicazioni, i byte audio né i thread di messaggi.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `ai`

## Origine

`modules/repositories/communications/rp-calls`