# rp-markdown

## Scopo

La pipeline Markdown condivisa: parsing, trasformazione e rendering per
ogni modulo che gestisce contenuti testuali. Un unico comportamento del parser invece
di varianti per superficie.

## Modello mentale

Sorgente Markdown in ingresso → parsing/trasformazione → output renderizzato (HTML, blocchi).
Gli autori di contenuti scrivono una volta; documenti, chat, landing page e notifiche eseguono il rendering
della stessa sorgente in modo coerente.

## Valore per l’ecosistema

Dorsale testuale unica:

- File Markdown più conversione JSON dietro un’unica API.
- Ogni producer memorizza il testo umano allo stesso modo invece della propria gestione dei file.

## Non obiettivi

- Non archiviazione di blocchi tipizzati.
- Non rendering HTML.
## Confine di responsabilità

Possiede il comportamento di conversione/parsing Markdown; non possiede la transcodifica
di rich media o la composizione delle pagine.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `content`

## Fonte

`modules/repositories/content/rp-markdown`