# CASE

CASE interpreta la richiesta di un utente come un comando della piattaforma. Riceve l'insieme dei
comandi che la piattaforma può eseguire e gli esempi delle frasi che esprimono ciascuno di essi.
Da "show equipment" seleziona il comando che apre l'elenco delle attrezzature. Da "show order 4815"
seleziona il comando che apre un ordine.

Il servizio confronta la richiesta con gli esempi dei comandi e restituisce il comando selezionato
con un punteggio. `EXECUTE` significa che un comando è stato riconosciuto con sufficiente chiarezza
per essere eseguito. `AMBIGUOUS` significa che diversi comandi sono troppo simili per poter scegliere
tra loro. `UNKNOWN` significa che la richiesta non corrisponde all'insieme dei comandi.

CASE sceglie quale azione l'utente sta chiedendo di eseguire. Non estrae i dettagli di tale richiesta.
Quando un comando ne ha bisogno, PARAMS legge lo stesso testo e restituisce i valori necessari per
aprire o filtrare il risultato: in "show order 4815", CASE sceglie il comando dell'ordine e PARAMS
estrae `4815`.
