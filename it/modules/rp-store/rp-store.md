# rp-store

## Scopo

Block store a indirizzamento per contenuto — lo strato più basso di archiviazione binaria dell'intero
ecosistema. Memorizza i chunk in base all'hash del contenuto; non sa nulla di file,
ordini, utenti o entità di business.

## Modello mentale

Il producer suddivide i byte in chunk → li inserisce nello store → riceve
riferimenti. Il consumer riassembla i byte dai riferimenti. Lo store
stesso è una semplice mappa key(blob_hash) → byte con deduplicazione: un
chunk identico caricato due volte viene memorizzato una sola volta.

## Valore per l'ecosistema

Fondamento di byte a indirizzamento per contenuto:

- Blob di byte opachi indicizzati per hash, memorizzati una volta, referenziati ovunque.
- Qualsiasi producer persiste i byte senza un proprio storage binario.

## Non obiettivi

- Né metadati di file né collezioni.
- Né voci di cache intermedie.
## Confine di responsabilità

Possiede put/get dei blocchi per riferimento di contenuto e ciclo di vita dei chunk; non possiede
denominazione/collezioni a livello di file né semantica di business dei servizi chiamanti.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `requests`

## Origine

`modules/repositories/data/rp-store`