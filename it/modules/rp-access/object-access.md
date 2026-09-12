# Accesso agli oggetti

## Due livelli, non uno

L'accesso ai metodi e l'accesso agli oggetti rispondono a domande diverse e nessuno dei due sostituisce
l'altro.

**Accesso ai metodi** — questo attore può chiamare `rp/community/listTopics`? È contenuto
nell'albero dei permessi, rilasciato da `rp-access` e applicato dal guard nrpc prima che
venga eseguito l'handler. Senza di esso, chiunque può chiamare `deleteTopic`.

**Accesso agli oggetti** — quali topic restituisce `listTopics`? Questo è l'argomento del
presente documento. Senza di esso, un attore autorizzato a chiamare `listTopics` riceve ogni topic
presente nello store.

L'accesso agli oggetti riutilizza il trasporto dell'accesso ai metodi invece di aggiungere un secondo
sistema: un tag è un grant ordinario nel kind `tg`, trasportato dallo stesso JWT e rilasciato dalle
stesse chiamate.

## Il meccanismo

Due elementi, entrambi locali al servizio che possiede i dati.

Una tabella per store, che serve ogni tipo di oggetto al suo interno:

```sql
CREATE TABLE access_tags (
  objectId TEXT NOT NULL,
  tag      TEXT NOT NULL,
  PRIMARY KEY (tag, objectId)
);
CREATE INDEX access_tags_object ON access_tags (objectId);
```

E i tag con cui viene associato un attore. Non esiste una colonna per il tipo di oggetto: è il join
con la tabella proprietaria a effettuare il filtraggio, poiché un id appartenente a un altro tipo non
viene trovato al suo interno.

## Tag

**Tag di gruppo** — `team-support`, `moderator`. Memorizzati per utente nel KV store `access`
di `rp-access`, all'interno dell'albero dei permessi esistente come
`tg/<tag>/*(mode)`, e trasportati nel JWT. Concessi con `addTagToUser`.

**Il tag personale** — `u-<userId>`. Non viene mai memorizzato né rilasciato: è derivato dal subject
del token, che ogni token verificato contiene già. Un oggetto aperto a una persona viene taggato con
il tag di quella persona, quindi una concessione individuale costa una riga e nulla nel token.

**Tag noti** — `public` (chiunque, inclusi i chiamanti anonimi) e `authenticated` (qualsiasi attore
verificato). La visibilità è determinata da quale di questi tag viene assegnato a un oggetto, non da
una colonna, così ogni selezione resta una ricerca per tag.

Quindi la proprietà, la condivisione individuale, l'accesso di gruppo e la visibilità pubblica sono un
solo meccanismo con quattro tipi di tag, non quattro meccanismi.

## Selezione

Una selezione deve iniziare dalla tabella dei tag ed effettuare il join con gli oggetti. `visibleFrom`
in `back-core/access` fa questo:

```ts
import { listVisible, visibleFrom } from "back-core";

const page = await listVisible<Topic>(this.store.db, "topics", { limit: 50 });

const custom = await visibleFrom(this.store.db, "topics")
  .selectAll("obj")
  .where("obj.status", "=", "open")
  .orderBy("obj.id")
  .limit(50)
  .execute();
```

La direzione non è una scelta stilistica. Scritta in forma piatta —
`access_tags JOIN topics ... WHERE tag IN (...) ORDER BY topics.id` — SQLite
preferisce scansionare la tabella degli oggetti in ordine di chiave primaria per soddisfare
l'ordinamento. Su una tabella di un milione di righe con dieci elementi visibili, una pagina di
cinquanta ha richiesto **363 ms**. Attraverso la sottoquery costruita da `visibleFrom`, la stessa
pagina ha richiesto **0.28 ms**. Entrambe restituiscono risultati identici, motivo per cui la forma
ha un test che verifica il piano della query anziché l'output.

Non filtrare mai dopo la query, al di fuori del database, e non inserire mai i tag in una colonna
lista verificata per ogni riga: entrambi i metodi leggono l'intera tabella.

`listVisible` restituisce `totalCount` calcolato con lo stesso restringimento applicato alla pagina.
Contare senza di esso rivela quanti oggetti vengono nascosti.

## Concessione

```ts
const access = new AccessTags(this.store);

await access.tagNew(id, { owner: actorId, visibility: "private" });
await access.grantToUser(id, otherUserId);   // effettivo immediatamente
await access.revokeFromUser(id, otherUserId);
await access.dropObject(id);                 // alla cancellazione; una riga residua potrebbe
                                             // in seguito corrispondere a un id riutilizzato
await access.requireRead(id);                // genera AccessDeniedError
```

L'appartenenza ai gruppi passa invece da `rp-access`, perché risiede nel token:

```ts
await access.addTagToUser(userId, "team-support");
await access.removeTagFromUser(userId, "team-support");
await access.getTagsOfUser(userId);
```

## Requisiti

**Gli id devono essere univoci tra le tabelle coperte dai tag.** Una sequenza condivisa, un UUID o
un prefisso del tipo — a seconda di ciò che lo store utilizza già. Le entità non coperte dai tag non
sono interessate; non si tratta di una migrazione a UUID dell'intera piattaforma.

**Gli id devono essere generati dal server.** In assenza di una colonna per il tipo di oggetto, un id
che il chiamante può scegliere identifica un oggetto che il chiamante può raggiungere. Gli id forniti
dal client esistono oggi in `rp-sales`, `rp-classifier` e `rp-chats` e devono essere eliminati prima
che questi repository adottino i tag.

**Gli id monotoni sono un vantaggio, non un requisito.** Una sequenza condivisa o UUIDv7 fornisce
l'ordine di creazione direttamente dall'indice dei tag. UUIDv4 non lo fa, e questa è l'unica
conseguenza: usa invece un `orderBy` esplicito.

**L'ordine dei byte deve corrispondere al significato.** Una sequenza numerica mantenuta in una
colonna di testo necessita di zeri iniziali, altrimenti `"10"` viene ordinato prima di `"9"`.

**Niente `:` o `;` negli id o nei tag.** Sono `KEY_SEPARATOR` e `RANGE_END_SUFFIX` in
`back-core`; un separatore all'interno di una chiave la rende ambigua negli store KV.
`addTagToUser` rifiuta tali tag.

**`NRPC_ACCESS_MODE` deve essere `required`.** Quando il guard è disattivato, l'utente del contesto
ricade nell'envelope, che viene scritto dal chiamante: il tag personale verrebbe quindi derivato da
un id fornito dal client. È `required` in `confs/dev` e `confs/prod`; il valore predefinito del codice
è `off` per le esecuzioni locali e i test.

## Store non SQL

KV: la stessa struttura delle chiavi nello stesso store — `tag:<tag>:<objectId>` in avanti,
`obj:<objectId>:<tag>` al contrario. La lettura di una lista è una scansione per prefisso per ogni
tag, con unione e deduplicazione. Una paginazione corretta richiede un cursore in `kvList`, che
attualmente restituisce un intero intervallo; fino ad allora, le liste KV sono limitate da ciò che
può essere contenuto in memoria.

File e JSON (`JsonStore` estende `FileStore`): nessun indice dei tag autonomo. Il nome del file è
l'id dell'oggetto e l'accesso a esso è l'accesso al record che lo referenzia, il quale risiede in uno
store SQL o KV dello stesso servizio.

Graph: tag come nodo, grant come arco, attraversamento a partire dal tag.

## Limiti accettati

**La rimozione di un tag di gruppo attende la riemissione del token** — `DEFAULT_TTL_SECONDS`
è di 90 giorni. Le concessioni e le revoche individuali sono immediate, perché la tabella viene
letta a ogni richiesta. L'accesso che deve cambiare immediatamente usa il tag personale, non un
gruppo.

**Un `totalCount` esatto** richiede il join; con diversi tag sovrapposti il conteggio viene effettuato
sugli id distinti, con un costo maggiore all'aumentare dell'insieme visibile.

**Ordinare per un campo diverso dall'id** è economico finché pochi oggetti corrispondono a un tag.
Se un tag dovesse mai coprire centinaia di migliaia di oggetti, quell'ordinamento dovrebbe essere
denormalizzato nella tabella dei tag oppure eliminato.
