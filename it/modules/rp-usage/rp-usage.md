# rp-usage

## Scopo

Il contatore di consumo condiviso: qualsiasi funzionalità segnala qui "quanto è stato utilizzato"
invece di tracciare le quote localmente. Aggregato per consumatore e periodo —
l'origine da cui fatturazione e limiti leggono.

## Modello mentale

La funzionalità registra il consumo (chi, cosa, quanto, periodo) → l'utilizzo
lo aggrega per account/periodo. La fatturazione a valle trasforma gli aggregati in denaro;
i controlli dei limiti leggono i totali correnti. La misurazione vive qui, la determinazione dei prezzi vive
a valle.

## Valore dell'ecosistema

Un unico registro eventi di utilizzo:

- Qualsiasi funzionalità registra righe (funzione, utente, data) allo stesso modo.
- I collegamenti soluzione-funzione consentono a qualsiasi report di raggruppare le chiamate per soluzione senza tabelle quote per modulo.

## Non obiettivi

- Nessuna fatturazione o esecuzione di pagamenti.
- Nessuna autenticazione o verifica dei permessi.
- Nessun contatore grezzo per dashboard.
## Confine di responsabilità

Possiede la misurazione e l'aggregazione dell'utilizzo; non possiede la fatturazione, l'esecuzione dei pagamenti
o la politica dei prezzi.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alle soluzioni

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-usage`