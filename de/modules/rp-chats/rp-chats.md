# rp-chats

## Zweck

Chaträume, ihre Mitgliedschaft und ihre raumbezogenen Kontexte. Die Unterhaltung
selbst befindet sich nicht hier: Ein Raum enthält eine `threadId`, und die Nachrichten
liegen in `rp-threads`.

## Zuständigkeitsgrenze

Verwaltet Räume, Rollen und Kontexte. Ruft kein anderes Repository auf — `createRoom` erzeugt
die `threadId` und gibt sie zurück, und der Aufrufer registriert den Thread.

## Identität und Zugriff

Der Aufrufer stammt aus dem verifizierten Token, niemals aus einem Parameter. Daraus ergeben sich zwei
nennenswerte Konsequenzen:

- `listRooms` wird innerhalb der Abfrage auf den Aufrufer beschränkt, sodass das Ersetzen der ID eines anderen
  Benutzers nicht mehr dessen Räume liest und `totalCount` nicht die Anzahl
  der Räume preisgeben kann, die ausgeblendet wurden;
- alles, was einen einzelnen Raum anhand seiner ID adressiert, prüft zuerst die Mitgliedschaft.

`chart_room_users` bleibt auch nach der Einführung von `access_tags` bestehen: Ein Tag drückt
Mitgliedschaft aus, aber nicht die Unterscheidung zwischen `owner`, `admin` und `member`.

## Hinweis zu Tabellennamen

Die Tabellen heißen `chart_rooms` / `chart_room_users`. Der Tippfehler ist
über Migrationen, Entitäten und Abfragen hinweg konsistent, daher funktioniert der Code; eine Umbenennung
ist eine Migration, keine Bearbeitung.

## Direkte Modulabhängigkeiten

- `back-core`, `nrpc`, `g-chats`

## Zugehörigkeit zur Lösung

- `communications`

## Quelle

`modules/repositories/communications/rp-chats`
