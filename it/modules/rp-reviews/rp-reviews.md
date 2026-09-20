# rp-reviews

## Scopo

Il sistema di recensioni del negozio, in tre tabelle che rispondono a tre domande diverse.

- `reviews` — ciò che ha detto un cliente, ciò che il negozio ha risposto e se è
  presente sul sito. La moderazione vive qui: una recensione proveniente
  dall'esterno nasce `pending` ed è visibile solo nella console finché qualcuno
  non la pubblica.
- `review_invites` — un link personale e utilizzabile una sola volta per ordine,
  e ciò che ne è stato: inviato, aperto, compilato, scaduto. Questo è il funnel
  che il negozio consulta.
- `review_settings` — una riga di JSON: le piattaforme esterne, la soglia,
  i modelli delle email, i ritardi e il limite dei solleciti.

## Confine di responsabilità

Gestisce recensioni, inviti e impostazioni del funnel. Non sa nulla degli ordini:
`Review.orderId` e `ReviewInvite.orderId` sono stringhe opache e associarle
agli ordini effettivi è compito di `wf-order-review-request` (che invia la richiesta) e di
`sf-reviews` (che le mostra). Non gestisce le discussioni della community.

## Due porte

L'accesso avviene tramite tag, come ovunque: una recensione pubblicata porta
`public`, tutto il resto porta `authenticated` più `moderator`, consentendo al
negozio di agire su una recensione che nessuno del negozio ha scritto.

La porta del cliente è diversa. `getInviteByToken`, `markInviteOpened` e
`submitByToken` sono autorizzati dal token stesso — una capability, non una
sessione — quindi il modulo pubblico funziona senza alcun login. Restituiscono
una vista ristretta che non contiene né il contatto né l'id dell'invito, e
`submitByToken` consuma il link in modo condizionale, così due invii dalla stessa
email producono una recensione e un rifiuto, anziché due recensioni.

## Controllo delle recensioni

`positiveThreshold` sposta l'*enfasi* del modulo pubblico e nient'altro:
a quel valore o al di sopra, all'autore vengono proposte prima le piattaforme
esterne; al di sotto, viene proposta prima una parola con il negozio. I link
alle piattaforme restano visibili in ogni caso, perché mostrare il percorso verso
una recensione pubblica solo ai clienti soddisfatti è vietato da Google e da
diverse altre piattaforme. Il comportamento sicuro è quello predefinito.

## Dipendenze dirette del modulo

- Nessuna

## Appartenenza alla soluzione

- `production`

## Sorgente

`modules/repositories/business/rp-reviews`
