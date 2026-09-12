# Bus di messaggi Fujin

Fujin è il centro di comunicazione del runtime Converged. Offre a browser,
servizi di dominio, storage, workflow, servizi multimediali e processori un modo
condiviso per scambiarsi messaggi.

## Perché esiste

Una piattaforma modulare ha bisogno che i componenti possano muoversi
indipendentemente. Collegamenti HTTP diretti costringerebbero ogni servizio a
conoscere indirizzi, repliche e topologia del deployment. Fujin sostituisce
questi collegamenti con destinazioni logiche: il mittente indica quale peer del
runtime dovrebbe ricevere un messaggio, e Fujin lo inoltra alla connessione
attiva che attualmente possiede quella destinazione.

```text
mittente -> destinazione logica -> Fujin -> connessione attiva -> servizio locale
```

Il mittente non sa dove viene eseguito il destinatario. Un processo può essere
riavviato o spostato su un altro nodo e riappropriarsi della stessa destinazione
senza modificare i suoi chiamanti.

## Modello di routing

Fujin prende una sola decisione di routing: associa una destinazione a una
connessione. La destinazione seleziona un processo come il runtime dell'interfaccia,
i servizi di dominio o Centimanus. Il nome del servizio contenuto nel messaggio
viene interpretato solo dopo che il processo ricevente lo ha ottenuto.

Mantenere separate queste decisioni è importante. Fujin rimane un piccolo
message broker invece di diventare un registro di ogni servizio aziendale,
unità di storage o workflow.

## Tre flussi

Fujin trasporta tre tipi di traffico che condividono un trasporto, ma nient'altro.
La messaggistica tra servizi trasferisce richieste tra peer. L'acquisizione dei
log riceve tutto ciò che producono i collector del deployment, lo raggruppa e lo
consegna in blocchi interi ai repository di analytics, così lo storage vede batch
anziché un flusso di singole righe. Le notifiche utente sono messaggi aziendali
indirizzati a una persona: è arrivato un ordine, un job è terminato, c'è una
lettera in attesa.

Il terzo è quello che ha bisogno di un nome proprio. `pushrouter` è un servizio
ospitato da Fujin anziché un servizio verso cui effettuare il routing, perché la
consegna è una proprietà delle sessioni attive che Fujin già possiede — nessun
altro processo sa quali browser di una persona siano attualmente connessi. Risponde
con il numero di sessioni raggiunte da un messaggio, consentendo al chiamante di
decidere se sia necessario anche un canale durevole, e mantiene una finestra
limitata di replay affinché un browser che si riconnette possa vedere ciò che ha
perso. Tutto ciò che deve sopravvivere a un riavvio appartiene a un repository,
non qui.

Le notifiche contengono chiavi di traduzione anziché frasi. Il servizio che ne
pubblica una non conosce la lingua del lettore, quindi una stringa già renderizzata
potrebbe essere corretta solo per uno di loro.

## Traffico browser e cluster

I peer nativi si connettono tramite il trasporto del cluster. Browser e client
mobili accedono tramite WebSocket e partecipano allo stesso modello di messaggistica.
Questo offre alle interfacce interattive eventi in tempo reale senza introdurre
un secondo sistema di routing applicativo.

I payload di grandi dimensioni rimangono al di fuori del canale di controllo del
browser. I client ricevono un evento di disponibilità e recuperano i dati tramite
il percorso di contenuto appropriato, mantenendo reattiva la segnalazione in
tempo reale.

## Contesto e affidabilità

L'envelope comune dei messaggi contiene dati di correlazione, scadenze, errori e
l'ambito trusted del tenant. Fujin trasporta questo contesto senza derivarlo da
un payload aziendale né modificarne il significato. I servizi riceventi possono
applicare regole di autorizzazione e storage rispetto allo stesso contesto
stabilito al margine.

## Confine delle responsabilità

Fujin gestisce la connettività e il routing delle destinazioni. Non esegue logica
aziendale, non seleziona un handler all'interno di un altro processo, non
memorizza dati di dominio e non decide il posizionamento del deployment. Queste
responsabilità restano al peer del runtime che riceve il messaggio e a Ptah in
quanto control plane.
