# rp-auth

## Scopo

L'unico punto di accesso per dimostrare “chi sei”: sessioni, credenziali ed
emissione di token per l'intero ecosistema. Nessun dominio gestisce un proprio login.

## Modello mentale

L'utente presenta le credenziali → auth le convalida ed emette una sessione/token →
ogni chiamata a valle lo trasporta e il livello di accesso decide cosa può fare.
Il login dimostra l'identità; le autorizzazioni sono un livello separato.

## Valore per l'ecosistema

Un unico backend di login per tutte le superfici:

- Magic link, sessioni di refresh e record client OAuth in un unico posto.
- Qualsiasi frontend autentica gli utenti allo stesso modo invece di usare proprie tabelle di sessione.

## Non obiettivi

- Non politiche di autorizzazione.
- Non record di profilo utente.

## Ambito di responsabilità

Possiede i flussi di autenticazione e la logica di emissione di token/sessione; non possiede
adattatori di provider OAuth di terze parti né valutazione delle policy di autorizzazione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `security`

## Origine

`modules/repositories/sequrity/rp-auth`