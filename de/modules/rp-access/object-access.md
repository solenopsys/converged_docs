# Objektzugriff

## Zwei Ebenen, nicht eine

Methodenzugriff und Objektzugriff beantworten unterschiedliche Fragen, und keiner
ersetzt den anderen.

**Methodenzugriff** — darf dieser Akteur `rp/community/listTopics` überhaupt aufrufen? Er ist
im Berechtigungsbaum hinterlegt, wird von `rp-access` ausgestellt und vom nrpc-Guard
überprüft, bevor der Handler ausgeführt wird. Ohne ihn kann jeder `deleteTopic` aufrufen.

**Objektzugriff** — welche Themen gibt `listTopics` zurück? Darum geht es in diesem
Dokument. Ohne ihn erhält ein Akteur, der `listTopics` aufrufen darf, jedes Thema
im Speicher.

Der Objektzugriff verwendet den Transport des Methodenzugriffs erneut, statt ein zweites
System hinzuzufügen: Ein Tag ist eine gewöhnliche Berechtigung unter dem Typ `tg`, wird
vom selben JWT übertragen und durch dieselben Aufrufe ausgestellt.

## Der Mechanismus

Zwei Dinge, beide lokal zu dem Dienst, der die Daten besitzt.

Eine Tabelle pro Speicher, die jeden darin enthaltenen Objekttyp bedient:

```sql
CREATE TABLE access_tags (
  objectId TEXT NOT NULL,
  tag      TEXT NOT NULL,
  PRIMARY KEY (tag, objectId)
);
CREATE INDEX access_tags_object ON access_tags (objectId);
```

Und die Tags, anhand derer ein Akteur gefunden wird. Es gibt keine Spalte für den
Objekttyp: Der Join zurück zur Eigentümertabelle übernimmt diese Filterung, da eine
ID, die zu einem anderen Typ gehört, dort nicht gefunden wird.

## Tags

**Gruppen-Tags** — `team-support`, `moderator`. Sie werden pro Benutzer im `access`-
KV-Speicher von `rp-access` gespeichert, innerhalb des bestehenden Berechtigungsbaums als
`tg/<tag>/*(mode)`, und im JWT übertragen. Sie werden mit `addTagToUser` vergeben.

**Das persönliche Tag** — `u-<userId>`. Es wird niemals gespeichert und niemals ausgestellt:
Es wird aus dem Token-Subjekt abgeleitet, das jedes verifizierte Token bereits enthält. Ein
Objekt, das für eine Person geöffnet wird, erhält das Tag dieser Person, sodass eine
individuelle Berechtigung eine Zeile kostet und nichts im Token.

**Vordefinierte Tags** — `public` (jeder, einschließlich anonymer Aufrufer) und
`authenticated` (jeder verifizierte Akteur). Die Sichtbarkeit ergibt sich daraus, mit welchem
dieser Tags ein Objekt geschrieben wird, nicht aus einer Spalte; dadurch bleibt jede
Auswahl eine Suche nach einem Tag.

Somit sind Besitz, individuelle Freigabe, Gruppenzugriff und öffentliche Sichtbarkeit ein
einziger Mechanismus mit vier Tag-Arten, nicht vier Mechanismen.

## Auswählen

Eine Auswahl muss bei der Tag-Tabelle beginnen und mit den Objekten verbunden werden. `visibleFrom`
in `back-core/access` erledigt dies:

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

Die Richtung ist keine Stilfrage. Flach geschrieben —
`access_tags JOIN topics ... WHERE tag IN (...) ORDER BY topics.id` — bevorzugt SQLite,
die Objekttabelle in Primärschlüsselreihenfolge zu durchsuchen, um die Sortierung zu erfüllen.
Bei einer Tabelle mit einer Million Zeilen und zehn sichtbaren Zeilen dauerte eine Seite mit
fünfzig gemessene **363 ms**. Über die von `visibleFrom` aufgebaute Unterabfrage dauerte
dieselbe Seite **0.28 ms**. Beide liefern identische Ergebnisse; deshalb gibt es einen Test,
der den Abfrageplan statt der Ausgabe prüft.

Niemals nach der Abfrage außerhalb der Datenbank filtern und Tags niemals in einer pro Zeile
geprüften Listen-Spalte ablegen: Beide Varianten lesen die gesamte Tabelle.

`listVisible` gibt `totalCount` zurück, das mit derselben Einschränkung wie die Seite ermittelt
wird. Ohne diese Einschränkung zu zählen, würde veröffentlichen, wie viele Objekte verborgen
werden.

## Berechtigungen vergeben

```ts
const access = new AccessTags(this.store);

await access.tagNew(id, { owner: actorId, visibility: "private" });
await access.grantToUser(id, otherUserId);   // sofort wirksam
await access.revokeFromUser(id, otherUserId);
await access.dropObject(id);                 // beim Löschen; eine übrig gebliebene Zeile würde
                                             // später zu einer wiederverwendeten ID passen
await access.requireRead(id);                // wirft AccessDeniedError
```

Die Gruppenmitgliedschaft läuft stattdessen über `rp-access`, weil sie im Token lebt:

```ts
await access.addTagToUser(userId, "team-support");
await access.removeTagFromUser(userId, "team-support");
await access.getTagsOfUser(userId);
```

## Anforderungen

**IDs müssen über die von Tags abgedeckten Tabellen hinweg eindeutig sein.** Eine gemeinsame
Sequenz, eine UUID oder ein Typpräfix — je nachdem, was der Speicher bereits verwendet.
Entitäten, die nicht von Tags abgedeckt sind, bleiben unberührt; dies ist keine plattformweite
Umstellung auf UUIDs.

**IDs müssen vom Server erzeugt werden.** Ohne Spalte für den Objekttyp ist eine ID, die der
Aufrufer selbst wählen kann, ein Objekt, auf das der Aufrufer zugreifen kann. Vom Client
bereitgestellte IDs gibt es heute in `rp-sales`, `rp-classifier` und `rp-chats`; sie müssen
geschlossen werden, bevor diese Repositories Tags übernehmen.

**Monoton steigende IDs sind ein Vorteil, keine Voraussetzung.** Eine gemeinsame Sequenz oder
UUIDv7 liefert die Erstellungsreihenfolge direkt aus dem Tag-Index. UUIDv4 tut das nicht, und
das ist die einzige Konsequenz — stattdessen ein explizites `orderBy` verwenden.

**Die Byte-Reihenfolge muss der Bedeutung entsprechen.** Eine numerische Sequenz in einer
Textspalte benötigt führende Nullen, sonst wird `"10"` vor `"9"` sortiert.

**Keine `:` oder `;` in IDs oder Tags.** Sie sind `KEY_SEPARATOR` und `RANGE_END_SUFFIX` in
`back-core`; ein Trennzeichen innerhalb eines Schlüssels macht ihn in KV-Speichern mehrdeutig.
`addTagToUser` weist solche Tags zurück.

**`NRPC_ACCESS_MODE` muss `required` sein.** Wenn der Guard deaktiviert ist, fällt der
Kontextbenutzer auf das Envelope zurück, das der Aufrufer schreibt — das persönliche Tag
würde dann aus einer vom Client bereitgestellten ID abgeleitet. In `confs/dev` und
`confs/prod` ist es `required`; der Code-Standardwert ist für lokale Ausführungen und Tests
`off`.

## Nicht-SQL-Speicher

KV: dieselbe Form wie Schlüssel im selben Speicher — `tag:<tag>:<objectId>` vorwärts,
`obj:<objectId>:<tag>` rückwärts. Das Lesen einer Liste ist ein Präfix-Scan pro Tag, dessen
Ergebnisse zusammengeführt und dedupliziert werden. Eine korrekte Seitennummerierung benötigt
einen Cursor in `kvList`, das derzeit einen ganzen Bereich zurückgibt; bis dahin sind
KV-Listen durch das begrenzt, was in den Arbeitsspeicher passt.

Dateien und JSON (`JsonStore` erweitert `FileStore`): kein eigener Tag-Index. Der Dateiname ist
die Objekt-ID, und der Zugriff darauf entspricht dem Zugriff auf den Datensatz, der darauf
verweist; dieser Datensatz lebt in einem SQL- oder KV-Speicher desselben Dienstes.

Graph: Tag als Knoten, Berechtigung als Kante, Traversierung ausgehend vom Tag.

## Akzeptierte Einschränkungen

**Das Entfernen eines Gruppen-Tags wartet auf die erneute Ausstellung des Tokens** —
`DEFAULT_TTL_SECONDS` beträgt 90 Tage. Individuelle Berechtigungen und Entziehungen wirken
sofort, da die Tabelle bei jeder Anfrage gelesen wird. Zugriff, der sich sofort ändern muss,
verwendet das persönliche Tag, nicht eine Gruppe.

**Ein exaktes `totalCount`** benötigt den Join; bei mehreren sich überschneidenden Tags wird
über unterschiedliche IDs gezählt, was mit wachsender sichtbarer Menge mehr kostet.

**Das Sortieren nach einem anderen Feld als der ID** ist günstig, solange wenige Objekte einem
Tag entsprechen. Falls ein Tag jemals Hunderttausende Objekte abdeckt, muss diese Reihenfolge
in der Tag-Tabelle denormalisiert oder verworfen werden.
