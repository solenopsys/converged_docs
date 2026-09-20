# wf-team-invite

## Scopo

Trasforma un elenco incollato di persone — "nome + indirizzo", in qualunque forma
sia stato scritto da una persona — in account utente, ruoli, schede del personale
e inviti, e invia a ogni persona il link che le consente di accedere.

Esiste perché quattro servizi devono muoversi insieme per una riga di quell'elenco
(`rp-identity`, `rp-access`, `rp-staff`, `rp-auth` più una lambda per le email) e
i microservizi non si chiamano tra loro.

## Perché è anche il confine dei privilegi

`rp-access` rifiuta senza mezzi termini un JWT utente (`@Access("internal")`), quindi nessuna superficie
può assegnare un ruolo. centimanus esegue questo script con `SERVICE_TOKEN`, e chi
può eseguirlo ha un normale permesso — `wf/workflows/wf-team-invite.js(x)` — verificato
all'edge (`signal_provider.zig:146`) e scritto in un unico file preset. Ecco perché
il prodotto non ha il concetto di "amministratore".

Lo script non può sapere chi lo ha chiamato, quindi la protezione contro l'escalation è un elenco fisso:
`manager`, `operator`, `viewer`. `owner` e `root` non possono essere assegnati qui.

## Struttura

1. fonti testuali — `files.materialize` + `files.extractText`, più `rawText`;
2. persone — prima `rt.llm`, un'espressione regolare riga per riga come fallback;
3. un `rt.attempt` per persona — utente, preset di base + ruolo, tag del gruppo, scheda,
   invito;
4. la lettera — un tentativo separato, così un relay rifiutato costituisce un ramo e non un
   account perso;
5. il report, i cui `staffIds` la superficie trasforma in una tabella aperta contenente esattamente
   queste persone.

Rieseguire lo stesso elenco non crea problemi: un indirizzo noto viene `updated`, mai
un secondo account.

## Dipendenze dirette dei moduli

- `g-access`, `g-auth`, `g-files`, `g-identity`, `g-notify`, `g-ses`, `g-smtp`,
  `g-staff`

## Appartenenza alla soluzione

- `production`

## Origine

`modules/workflows/wf-team-invite`
