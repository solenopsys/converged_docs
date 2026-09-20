# rp-access

## Scopo

Il livello di autorizzazione condiviso: ogni `rp-*` chiede qui «questo attore può farlo?» invece di inventare i propri controlli di autorizzazione. Un unico albero dei permessi, una unica regola di valutazione, applicata prima dell'esecuzione di qualsiasi handler.

## Modello mentale

Due domande, due livelli: l'accesso ai metodi («può chiamare X?») è contenuto nell'albero dei permessi e applicato dal guard; l'accesso agli oggetti («quali righe restituisce la chiamata?») è valutato per entità. Senza il primo, chiunque potrebbe chiamare `deleteTopic`.

## Valore per l'ecosistema

Unica radice di fiducia per le decisioni:

- Albero dei permessi, preset, tag e token emessi si trovano in un unico luogo.
- Qualsiasi servizio controlla lo stesso albero invece di creare proprie tabelle di policy.

## Non obiettivi

- Né login né emissione di sessioni.
- Né archiviazione di segreti.
## Limite di responsabilità

Possiede la valutazione delle policy di autorizzazione e gli ambiti di accesso; non possiede la verifica dell'identità / il login di autenticazione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `security`

## Origine

`modules/repositories/sequrity/rp-access`