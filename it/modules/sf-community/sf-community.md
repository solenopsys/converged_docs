# sf-community

## Scopo

Il forum, come tre schede separate: sezioni, gli argomenti di una sezione e la
discussione di un argomento. L'apertura di una riga apre una scheda accanto a
quella corrente: non esiste una schermata che mostri contemporaneamente un
albero delle sezioni, una tabella degli argomenti e una discussione.

## Confine di responsabilità

Gestisce la navigazione del forum e la schermata dell'argomento. I messaggi in sé
appartengono a `rp-threads`, che il browser legge direttamente; gli allegati
appartengono a `rp-files` tramite un messaggio `link`. Iscrizioni, ruoli e ticket
non rientrano in questo ambito.

## Come viene creato un argomento

`createTopic` su `rp-community` genera l'id dell'argomento e quello della
discussione e assegna l'autore dal token; questa superficie registra quindi la
discussione e scrive il post di apertura su `rp-threads`. La separazione è
intenzionale: gli id che un client può scegliere sono id che può sottrarre, e
un repository che chiama un altro repository è proprio ciò che l'architettura
vieta.

## Aggiornamenti in tempo reale

Le risposte arrivano attraverso il canale aziendale di Fujin (`pushrouter`) per
mezzo della libreria `threads-state`, non tramite polling. Un push trasporta solo
gli identificatori; il testo viene riletto da `rp-threads`, dove si applica il
predicato di lettura.

## Dipendenze dirette del modulo

- `front-core`, `g-community`, `g-threads`, `signal-channel`, `threads-state`

## Appartenenza alla soluzione

- `communications`

## Sorgente

`modules/surfaces/communications/sf-community`
