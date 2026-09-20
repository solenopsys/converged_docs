# rp-classifier

## Scopo

Il servizio condiviso di etichettatura: qualsiasi intake indirizza qui i contenuti grezzi e riceve
in cambio categorie, etichette o intenti. Un'unica logica di classificazione invece di
catene di if per dominio.

## Modello mentale

Il produttore invia elementi grezzi (file, testi, richieste) → il classificatore assegna
etichette → il chiamante instrada per etichetta (modello di produzione vs disegno, urgente
vs rumore). Le etichette sono consigli; la decisione di business resta al chiamante.

## Valore dell'ecosistema

Un unico scaffale tassonomico:

- Nodi dell'albero e mappature di chiavi dietro un'unica API.
- Qualsiasi intake risolve le etichette dallo stesso albero invece che dai propri dizionari.

## Non obiettivi

- Niente byte di file o conversione.
- Niente archiviazione di documenti JSON.
## Confine di responsabilità

Possiede la logica di classificazione e l'assegnazione delle etichette; non possiede le pipeline di ingestione dei contenuti di origine né il routing di business a valle.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Origine

`modules/repositories/content/rp-classifier`