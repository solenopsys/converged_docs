# rp-sheduller

## Scopo

Il trigger temporale condiviso: pianificazioni cron e relativa cronologia di esecuzione per
l'intero ecosistema. Qualsiasi job ricorrente si registra qui invece di eseguire il proprio
ciclo di timer.

## Modello mentale

L'operatore definisce una voce cron (quale workflow, quando, con quali args) → il
runtime si attiva secondo pianificazione → la cronologia registra cosa è stato eseguito e come è terminato.
Questo modulo memorizza ed elenca le voci; non esegue mai nulla direttamente.

## Valore per l'ecosistema

Un unico orologio per il lavoro ricorrente:

- Righe cron, cronologia delle esecuzioni e statistiche dietro un'unica API.
- Qualsiasi job ricorrente necessita solo di una riga cron — nessuna nuova infrastruttura di timer.

## Non obiettivi

- Non definizione o esecuzione di workflow.
- Non trigger una tantum — solo pianificazioni ricorrenti.
## Confine di responsabilità

Possiede CRUD/elenco/statistiche per voci cron e record di cronologia; non esegue
workflow, timer, retry o dispatch in background.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alle soluzioni

- Non incluso in una soluzione predefinita

## Fonte

`modules/repositories/automation/rp-sheduller`