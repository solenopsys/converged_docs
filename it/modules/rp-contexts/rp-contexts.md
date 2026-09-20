# rp-contexts

## Scopo

L'archivio condiviso di contesti denominati per l'IA: prompt, varianti linguistiche e
conoscenza di dominio si trovano qui invece di essere codificati in ogni flusso di lavoro.
Versionato per nome, risolto per lingua.

## Modello mentale

Il flusso di lavoro o l'assistente richiede un contesto per nome (+ lingua) → ottiene il
testo corrente. Gli editor aggiornano i contesti senza ridistribuire i consumatori.
Archiviazione e recupero sono qui; il prompt engineering spetta agli editor.

## Valore per l'ecosistema

Un unico scaffale di conoscenza per i percorsi IA:

- Contesti denominati con varianti linguistiche dietro un'unica API.
- Qualsiasi percorso IA risolve lo stesso contesto denominato invece delle proprie copie di prompt.

## Non obiettivi

- Non cronologia chat né thread di dialogo.
- Non esecuzione di prompt — solo testi di contesto archiviati.
## Confine di responsabilità

Possiede archiviazione e recupero di contesti IA denominati e varianti linguistiche;
non possiede l'infrastruttura del provider di modelli né il comportamento dialogico.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `ai`

## Origine

`modules/repositories/ai/rp-contexts`