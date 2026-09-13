# rp-community

## Scopo

Struttura e responsabilità del forum: sezioni, argomenti, chi li ha scritti e chi
può vederli. La discussione all'interno di un argomento non si trova qui: un
argomento contiene un `threadId` e i messaggi risiedono in `rp-threads`.

## Confine di responsabilità

Gestisce sezioni e argomenti. Non chiama `rp-threads` né alcun altro repository:
`createTopic` genera un `threadId` e lo restituisce, mentre il chiamante registra
il thread e scrive autonomamente il post di apertura.

## Identità e paternità

`createdBy` non viene mai accettato dal chiamante. Viene letto dal token verificato
tramite `getCurrentWorkspaceContext()`, che `messaging-backend` preferisce a
qualsiasi informazione dichiarata nell'envelope. Per lo stesso motivo, gli ID di
argomenti e thread vengono generati qui: un ID che il client può scegliere è un
ID che può sottrarre, e la tabella dei tag di accesso non registra alcun tipo di
oggetto per rilevare la collisione.

## Visibilità

Sezioni e argomenti contengono una colonna `visibility` (`public` | `authenticated` |
`private` | `tagged`) e un nuovo argomento eredita il valore della propria sezione,
a meno che non richieda qualcosa di più restrittivo. I tag alla base di `tagged`
appartengono alla relazione condivisa `access_tags` descritta in
`access-control.md`; questa parte non è ancora implementata, quindi oggi
`visibility` viene registrata ma non applicata.

## Blocco

`touchTopicActivity` è l'unico punto in cui è possibile applicare un blocco:
`rp-threads` accetta un messaggio senza sapere che esistono argomenti, quindi
una schermata lo chiama dopo la pubblicazione e considera un rifiuto come un
fallimento della pubblicazione.

## Dipendenze dirette del modulo

- `back-core`, `nrpc`, `g-community`

## Appartenenza alla soluzione

- `communications`

## Sorgente

`modules/repositories/communications/rp-community`
