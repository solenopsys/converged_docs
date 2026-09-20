# lm-modelconvertor

## Scopo

Il bridge condiviso per i formati dei modelli: converte i modelli di produzione tra rappresentazioni interne ed esterne (ad es. in anteprime GLB) in modo che nessun flusso di lavoro colleghi direttamente una libreria di conversione nativa.

## Modello mentale

Il flusso di lavoro prepara i byte del modello → il convertitore trasforma il formato → restituisce i byte di anteprima/convertiti come ref di cache per `rp-files.persist`. Trasformazione pura: nessuno storage, nessuna stima, nessuna decisione di business.

## Valore per l'ecosistema

Un unico punto di conversione per i modelli di produzione:

- Un file staged in ingresso, output convertiti come ref di cache in uscita — stessa forma per qualsiasi chiamante.
- Nuovi formati e versioni del convertitore arrivano una volta e aggiornano ogni percorso di analisi.
- Mantiene le dipendenze native pesanti fuori da flussi di lavoro e repository.

## Non obiettivi

- Non archiviazione file né orchestrazione di intake.
- Non rendering di anteprime né stime di slicing.

## Limite di responsabilità

Possiede le routine di conversione/trasformazione; non possiede il training dei modelli a monte, il serving a valle o la persistenza.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Fonte

`modules/lambdas/convertors/lm-modelconvertor`