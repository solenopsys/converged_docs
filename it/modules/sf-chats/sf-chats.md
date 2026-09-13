# sf-chats

## Scopo

Stanze di chat, come tre schede separate: l'elenco delle stanze, la conversazione di una stanza e
l'elenco dei membri di una stanza. Gestire chi si trova in una stanza e leggere ciò che ha detto sono
due attività e quindi due schede.

## Confine di responsabilità

Gestisce la navigazione delle stanze, la schermata della conversazione e la modifica dei membri. I messaggi
appartengono a `rp-threads`, letti direttamente dal browser; i file appartengono a
`rp-files` tramite un messaggio `link`.

## Come viene creata una stanza

`createRoom` su `rp-chats` genera l'id della stanza e l'id del thread e registra il
creatore dal token come `owner`; questa superficie registra quindi il thread con
`rp-threads`. `rp-chats` non chiama mai un altro repository.

## Aggiornamenti in tempo reale

Un nuovo messaggio viene pubblicato a ciascun membro per nome tramite il `pushrouter` di Fujin,
mai all'intero tenant: l'esistenza di una stanza privata non è pubblica anche quando i suoi
contenuti restano protetti dal predicato di lettura. Il push trasporta solo identificatori.

## Dipendenze dirette del modulo

- `effector`, `front-core`, `g-chats`, `g-threads`, `signal-channel`, `threads-state`

## Appartenenza alla soluzione

- `communications`

## Sorgente

`modules/surfaces/communications/sf-chats`
