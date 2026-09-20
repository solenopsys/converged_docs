# lm-compressors

## Scopo

Il cavallo da lavoro condiviso a livello di byte della pipeline di file: assemblaggio, decompressione,
analisi ZIP, suddivisione dell'output e staging. Stateless — nessun client `files` o
`store` al suo interno; restituisce byte e riferimenti alla cache, la persistenza
è compito del workflow.

## Modello mentale

Il workflow passa i ref dei chunk + l'operazione (spacchettare, assemblare, suddividere) → lambda
esegue puro lavoro sui byte → restituisce byte in staging/ref di cache. Non decide mai
cosa significa un file e non memorizza mai nulla.

## Valore per l'ecosistema

Un unico punto in cui vengono toccati i byte degli archivi:

- Chunk compressi in ingresso, voci in staging in uscita — un'unica forma di unpack per qualsiasi chiamante.
- Qualsiasi futuro formato di archivio o compressione approda qui una volta e aggiorna ogni intake in una sola volta.

## Non-obiettivi

- Non archiviazione o classificazione dei file.
- Non conversione di modelli o rendering di anteprime.
## Confine di responsabilità

Possiede assemblaggio dei byte, decompressione, analisi degli archivi, suddivisione dell'output e
staging; non possiede record di file né persistenza.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `requests`

## Origine

`modules/lambdas/data/lm-compressors`