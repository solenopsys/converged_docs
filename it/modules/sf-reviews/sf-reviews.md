# sf-reviews

## Scopo

Il sistema delle recensioni come un'unica area di lavoro: ciò che i clienti hanno detto sul lavoro,
quale parte è sul sito, cosa ha risposto il negozio e quanto sta procedendo la richiesta —
quanti link sono stati inviati, quanti sono stati aperti, quanti sono tornati indietro.

## Struttura

La superficie dichiara due viste `setOf` — le recensioni e gli inviti che le hanno richieste — che l'area di lavoro trasforma nei pulsanti permanenti di questa scheda, e una vista `objectOf` per una recensione. La coda di moderazione, la bacheca delle recensioni pubblicate e l'insieme di quelle rifiutate sono preimpostazioni sulla tabella delle recensioni, non tre tipi: sono un'unica lista letta in tre modi. Aprire una recensione apre quindi una sottoscheda *all'interno* delle recensioni invece di portare altrove. Senza alcuna selezione, la superficie mostra la propria schermata, `ReviewsDashboardView`.

## Confine di responsabilità

Legge e scrive in `rp-reviews`. Legge `rp-orders` per il lavoro a cui si riferisce una recensione —
direttamente dal browser, che è il luogo in cui appartiene una composizione a due chiamate; nessuno dei due
repository conosce l'altro.

L'invio non viene effettuato da qui. `wf-order-review-request` crea e invia il link personale e `wf-order-review-followup` lo sollecita, perché raggiungere un ordine e una recensione in un unico processo è esattamente ciò a cui serve un workflow. «Richiedi una recensione» su questa superficie crea il link e lascia l'invio a quel flusso, così rimangono un unico mittente e un'unica traccia.

## Controllo delle recensioni

Il modulo pubblico mostra a tutti le piattaforme esterne. La soglia del negozio sposta l'*enfasi* — a un cliente soddisfatto vengono proposte prima le piattaforme, a uno insoddisfatto viene proposta prima una comunicazione con il negozio — e mai la disponibilità dei link, perché mostrare il percorso verso una recensione pubblica solo ai clienti soddisfatti è vietato da Google e da diverse altre piattaforme. La scheda indica verso quale direzione il modulo si è orientato per una determinata recensione; non applica alcun filtro.

## Dipendenze dirette del modulo

- `g-reviews`
- `g-orders`

## Appartenenza alla soluzione

- `production`

## Origine

`modules/surfaces/business/sf-reviews`
