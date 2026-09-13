# rp-files

## Scopo

Fornisce API per i metadati dei file e flussi di lavoro per la gestione dei file.

## Confine di responsabilità

Gestisce i record dei file e le operazioni a livello di file; non gestisce i dettagli di implementazione dell'archiviazione degli oggetti.

## Dipendenze dirette del modulo

- `rp-store` — l'archivio di blocchi indirizzato al contenuto in cui risiedono i byte di ogni file.
  rp-files conserva i nomi, le raccolte e l'elenco dei chunk; non archivia dati.

## Appartenenza alla soluzione

- `requests`

## Sorgente

`modules/repositories/data/rp-files`
