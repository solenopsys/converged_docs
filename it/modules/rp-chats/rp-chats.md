# rp-chats

## Scopo

Stanze di chat, relativa appartenenza e contesti per stanza. La conversazione
in sé non si trova qui: una stanza contiene un `threadId` e i messaggi risiedono in
`rp-threads`.

## Confine di responsabilità

Gestisce stanze, ruoli e contesti. Non chiama alcun altro repository — `createRoom` genera
il `threadId` e lo restituisce, mentre il chiamante registra il thread.

## Identità e accesso

Il chiamante proviene dal token verificato, mai da un parametro. Due
conseguenze che vale la pena citare:

- `listRooms` è limitato al chiamante all'interno della query, quindi sostituire l'id di un altro
  utente non consente più di leggere le sue stanze e `totalCount` non può rivelare il numero
  di stanze che ha nascosto;
- qualsiasi operazione che indirizza una singola stanza tramite id verifica prima l'appartenenza.

`chart_room_users` rimane anche dopo l'arrivo di `access_tags`: un tag esprime
l'appartenenza, ma non distingue tra `owner`, `admin` e `member`.

## Nota sui nomi delle tabelle

Le tabelle sono denominate `chart_rooms` / `chart_room_users`. L'errore di battitura è
coerente tra migrazioni, entità e query, quindi il codice funziona; rinominare
è una migrazione, non una modifica.

## Dipendenze dirette del modulo

- `back-core`, `nrpc`, `g-chats`

## Appartenenza alla soluzione

- `communications`

## Sorgente

`modules/repositories/communications/rp-chats`
