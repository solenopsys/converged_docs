# rp-identity

## Scopo

Il registro profili condiviso: un record di identità per persona o account di servizio,
collegato da ogni dominio. Ordini, chat, schede del personale — puntano tutti
allo stesso profilo invece di copiare nomi e attributi.

## Modello mentale

Identità = record stabile (id, attributi principali, stato del ciclo di vita). I domini
memorizzano l’id di identità e leggono gli attributi su richiesta; non duplicano mai il
profilo. L’autenticazione dimostra l’identità, l’accesso la verifica, i domini la referenziano.

## Valore per l’ecosistema

Un unico “chi” per la piattaforma:

- Record utente, collegamenti ai metodi di autenticazione e inviti in un unico luogo.
- Ogni dominio memorizza un id utente opaco e legge gli attributi su richiesta invece di duplicare i profili.

## Non obiettivi

- Non login o sessioni.
- Non permessi.
- Non struttura organizzativa o semantica del personale.
## Confine di responsabilità

Possiede i record di identità e lo stato del ciclo di vita delle identità; non possiede
criteri di autorizzazione granulari né flussi di autenticazione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `security`

## Fonte

`modules/repositories/sequrity/rp-identity`