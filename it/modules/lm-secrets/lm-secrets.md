# lm-secrets

## Scopo

L'adattatore condiviso del vault dei segreti: valori di segreti denominati per l'intera
piattaforma dietro un unico contratto. I servizi leggono qui i segreti di configurazione invece di
env-sprawl o client vault per modulo.

## Modello mentale

Il servizio chiede per nome del segreto → ottiene il valore. La rotazione avviene in un
luogo e si propaga a ogni consumer. I dettagli del backend di storage restano dietro
il contratto.

## Valore dell'ecosistema

Un'unica porta del vault per tutti:

- Credenziali dei provider, token di integrazione, segreti OAuth — stessa forma get/set/delete.
- Qualsiasi consumer mantiene i segreti fuori da codice e configurazione; la rotazione avviene in un unico luogo.
- Le nuove integrazioni non richiedono nuova infrastruttura per i segreti.

## Non obiettivi

- Non autenticazione o controlli di autorizzazione.
- Non record di identità utente.
## Confine di responsabilità

Responsabile dell'archiviazione, del recupero e dell'eliminazione dei valori di segreti denominati; non responsabile di
identità, autorizzazioni o logica di sessione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alle soluzioni

- Non incluso in una soluzione predefinita

## Fonte

`modules/lambdas/sequrity/lm-secrets`