# rp-dumps

## Scopo

Il dock di esportazione condiviso: qualsiasi dominio acquisisce qui snapshot dei propri dati per migrazione,
backup o passaggio di consegne invece di inventare un proprio formato di dump. Snapshot
confezionati con metadati di recupero.

## Modello mentale

Il dominio richiede un dump (ambito, tempo) → il dump viene generato e confezionato →
i metadati di recupero puntano all'artefatto archiviato.
Generazione e contabilità vivono qui; l'archiviazione a lungo termine vive altrove.

## Valore per l'ecosistema

Un'unica storia di esportazione per la piattaforma:

- Elenco dello storage, statistiche, compattazione e segmenti di dump dietro un'unica API.
- Qualsiasi dominio diventa esportabile senza una propria macchina per snapshot.

## Non obiettivi

- Non serving di file live.
- Non storage di byte parallelo.
## Confine di responsabilità

Possiede generazione, confezionamento e metadati di recupero dei dump; non possiede
la piattaforma di archiviazione a lungo termine.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Origine

`modules/repositories/data/rp-dumps`