# sf-community

## Zweck

Das Forum als drei separate Tabs: Bereiche, die Themen eines Bereichs und die
Diskussion eines einzelnen Themas. Das Öffnen einer Zeile öffnet einen Tab neben
dem aktuellen – es gibt keinen Bildschirm, der gleichzeitig einen Bereichsbaum,
eine Thementabelle und einen Thread anzeigt.

## Zuständigkeitsgrenze

Verantwortet die Forumnavigation und die Themenansicht. Die Nachrichten selbst
gehören zu `rp-threads`, das der Browser direkt liest; Anhänge gehören über eine
`link`-Nachricht zu `rp-files`. Mitgliedschaften, Rollen und Tickets gehören
nicht hierher.

## So wird ein Thema erstellt

`createTopic` auf `rp-community` erzeugt die Themen-ID und die Thread-ID und
übernimmt den Autor aus dem Token; diese Oberfläche registriert anschließend den
Thread und schreibt den Eröffnungsbeitrag in `rp-threads`. Die Aufteilung ist
absichtlich so gestaltet: IDs, die ein Client selbst wählen kann, kann er auch
stehlen, und ein Repository, das ein anderes Repository aufruft, ist genau das,
was die Architektur verbietet.

## Live-Aktualisierungen

Antworten treffen über Fujins Geschäftskanal (`pushrouter`) mithilfe der
Bibliothek `threads-state` ein, nicht durch Abfragen. Ein Push übermittelt nur
Bezeichner; der Text wird aus `rp-threads` erneut gelesen, wo das
Leseprädikat angewendet wird.

## Direkte Modulabhängigkeiten

- `front-core`, `g-community`, `g-threads`, `signal-channel`, `threads-state`

## Zugehörigkeit zur Lösung

- `communications`

## Quelle

`modules/surfaces/communications/sf-community`
