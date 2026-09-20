# sf-team

## Scopo

Il team come unica area di lavoro: chi lavora qui, cosa può fare ciascuno e chi
è stato invitato ma non è ancora arrivato.

## Proiezioni

Quattro viste `setOf`, che la shell trasforma nei pulsanti permanenti della scheda
— **Team**, **Inviti**, **Pianificazione**, **Diritti** — più una vista
`objectOf`, la scheda della persona, che si apre come sottoscheda *all'interno*
della stessa area. Quando non è selezionato nulla, l'area mostra la propria
schermata (`team.statistic` risolta attraverso la sua vista `setOf`, il modello
usato da `sf-logs` e `sf-equipment`).

## Cosa definisce questa superficie

**La console non può concedere nulla.** `rp-access` è `@Access("internal")` e
il runtime rifiuta un JWT utente prima che venga verificato qualsiasi permesso
(`messaging-access.ts:176`). Pertanto ogni operazione che modifica ciò che qualcuno può
fare esegue `wf-team-invite` su centimanus, che contiene il token di servizio del
cluster. Chi può eseguirla è la concessione ordinaria
`wf/workflows/wf-team-invite.js(x)`, che risiede in un unico file preset — quella
concessione costituisce l'intero concetto di "chi può aggiungere persone".

Tre metodi di invito su `rp-identity` hanno un `@Access("user")` a livello di
metodo, così la colonna di consegna può essere letta senza un workflow a ogni
aggiornamento della tabella; sono regolati da `rp/identity/listInvites(r)` nei
preset del proprietario e del manager.

La proiezione **Diritti** viene composta nel browser a partire dall'elenco dei
membri e dagli inviti, perché il servizio che conosce la risposta reale non può
essere interrogato da qui. Mostra quanto risulta dal record — il ruolo assegnato
alla persona e i tag che lo accompagnano — non una lettura del suo token attivo.

## Operazioni

`team.member.import` (quella per cui esiste questo perimetro — un elenco incollato
in ingresso e una tabella compilata contenente esattamente quelle persone),
`team.member.create`, `team.member.save`, `team.member.setRole`,
`team.member.deactivate`, `team.invite.revoke`, `team.shift.create`.

Tre di queste sono pubblicate nel catalogo della chat in `llm.json`.

## Dipendenze dirette dei moduli

- `front-core`, `g-centimanus`, `g-identity`, `g-staff`

## Appartenenza alla soluzione

- `production`

## Sorgente

`modules/surfaces/sequrity/sf-team`
