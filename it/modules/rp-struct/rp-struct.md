# rp-struct

## Scopo

Il generatore di strutture condiviso: trasforma i contenuti liberi in rappresentazioni tipizzate, modellate sullo schema,
su cui ogni consumatore può fare affidamento. Un unico punto di modellazione tra il contenuto grezzo
e il rendering del canale.

## Modello mentale

Contenuto grezzo in ingresso → la modellazione della struttura applica schemi e forme → blocchi tipizzati
in uscita. I canali (`sf-*`, markdown, modelli di notifica) eseguono il rendering dei blocchi
senza rieseguire il parsing della sorgente.

## Valore per l'ecosistema

Uno scaffale JSON senza tipi:

- Documenti JSON dietro un'unica API di file.
- Qualsiasi produttore archivia blob strutturati senza una propria gestione dei file.

## Non obiettivi

- Nessuna tassonomia o etichettatura.
- Nessun rendering markdown.
## Confine di responsabilità

Responsabile della modellazione della struttura e della modellazione a livello di schema; non responsabile del rendering finale
specifico del canale.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `content`

## Origine

`modules/repositories/content/rp-struct`