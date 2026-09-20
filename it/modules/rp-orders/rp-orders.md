# rp-orders

## Scopo

Ciclo di vita dell'ordine: creazione, aggiornamenti, elenco e tracciamento. I file si collegano tramite fileId (rp-files), la discussione fa riferimento a un threadId (rp-threads), il completamento può attivare inviti a recensioni.

## Limite di responsabilità

Possiede i record degli ordini e le transizioni di stato; non possiede l'archiviazione dei file, la messaggistica né i meccanismi di recensione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Origine

`modules/repositories/business/rp-orders`