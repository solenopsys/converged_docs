# rp-dag

## Zweck

Verantwortet die Workflow-Trigger und das Ausführungsprotokoll. Führt selbst nichts aus.

## Verantwortungsgrenze

Hierher gehören genau zwei Dinge und nichts anderes:

- **Trigger** — „wenn dieses Bus-Thema erscheint, führe jenen Workflow aus“. Systemkonfiguration: Dutzende von Zeilen, die ein Operator pflegt und die vollständig im Speicher der Laufzeit gehalten werden, statt abgefragt zu werden.
- **Das Ausführungsprotokoll** — ein Baum dessen, was ein Lauf getan hat. Die Laufzeit schreibt ihn, während das Skript läuft: Ein Knoten wird geöffnet, bevor sein Inhalt ausgeführt wird, und geschlossen, wenn er fertig ist, sodass ein laufender Lauf den Knoten zeigt, bei dem er gerade steht.

Der Workflow-Katalog wird hier nicht verwaltet. Ptah legt die Deskriptoren der aktiven Solution in die Umgebung dieses Dienstes (`WORKFLOWS`, `WORKFLOW_DIGESTS`, `MODULE_PROXY`) und `listAvailableWorkflows` veröffentlicht sie für die Laufzeit und die UI erneut. Die Quelldaten bleiben hinter Ptah-proxy.

## Das Protokoll wird von der Laufzeit geschrieben, nicht von diesem Dienst

Nichts hier schreibt einen Protokolleintrag. Die Laufzeit formatiert ihn, legt ihn unter einem selbst zusammengesetzten Schlüssel in Valkey ab und übergibt später die Schlüssel — niemals die Einträge.
`commitLog` wandelt jeden Schlüssel in einen Speicherort um und weist den Speicher an, den Eintrag abzuholen; der Speicher liest den Cache direkt, sodass ein Eintrag den Transport genau einmal durchquert, als Bytes, die niemand erneut kodiert.

```text
Workflow-Thread ─► Warteschlange ─► Protokollschreiber ─► Valkey
                                      │
                                      └─ commitLog([keys]) ─► rp-dag ─► Speicher liest Valkey
                                                                                 │
                                      ◄──── übernommen ──────────────────────────┘
                                      └─ die übernommenen Schlüssel löschen
```

Das hält die Protokollierung vom kritischen Pfad des Workflows fern: Ein Knoten kostet die Laufzeit einen Eintrag in die Warteschlange und sonst nichts. Es bedeutet außerdem, dass das Protokoll konstruktionsbedingt nach bestem Bemühen geführt wird — ein Eintrag kann bei Rückstau verloren gehen, und ein Stapel kann nach einem Absturz zweimal übernommen werden. Schlüssel werden aus dem Lauf und der Sequenz des Knotens abgeleitet, sodass die zweite Übernahme eine Überschreibung statt eines Duplikats ist.

Aus diesem Grund kommen die Schlüssel von der Laufzeit: Eine von diesem Dienst vergebene Nummer würde pro Knoten eine Hin- und Rückfahrt kosten und wäre nach einem Neustart nicht reproduzierbar.

- `dag:log:<executionId>:exec` — der Lauf
- `dag:log:<executionId>:n:<seq>` — einer seiner Knoten, auf sechs Stellen mit Nullen aufgefüllt

`commitLog` leitet den Speicherort aus dem Schlüssel ab und lehnt alles außerhalb des Präfixes `dag:log:` ab, sodass ein Schlüssel die gesamte Autorität darstellt, die der Aufruf mit sich führt.

## Das Protokoll ist ein Baum

```text
exec:<id>              der Lauf
node:<id>:<seq>        seine Knoten in der Reihenfolge, in der sie geöffnet wurden
```

Ein Knoten, der über `rt.sub` delegiert hat, enthält die ID des untergeordneten Laufs, und das untergeordnete Element ist ein gewöhnlicher Lauf mit eigenen Knoten. `executionTree` folgt diesem Verweis in Tiefensuche und gibt das Ergebnis flach zurück, wobei jede Zeile mit ihrer `depth` gekennzeichnet ist — ein Client stellt den Baum dar, indem er nur einrückt. Ein übergeordneter Index ist nicht erforderlich: Der Verweis ist der Knoten, der ihn erstellt hat.

Sequenzen werden im Schlüssel mit Nullen aufgefüllt, weil der KV-Speicher einen Präfixbereich in lexikografischer Reihenfolge zurückgibt und diese Reihenfolge der Reihenfolge entsprechen muss, in der die Knoten ausgeführt wurden. Die Laufzeit füllt beim Zusammensetzen des Cache-Schlüssels auf dieselbe Breite auf; die beiden Breiten sind ein Vertrag.

Die Aufbewahrung ist auf Läufe begrenzt (`5000` standardmäßig) und wird bei jedem hundertsten Öffnen durchgesetzt. Das Protokoll dient der Diagnose, nicht der Archivierung.

## Trigger-Änderungen erreichen die Laufzeit über den Bus

Beim Erstellen, Ändern oder Löschen eines Triggers wird `dag.triggers.changed` veröffentlicht. Die Laufzeit abonniert dieses Thema zusätzlich zu den eigenen Themen der Trigger, sodass eine Änderung für das nächste Ereignis aktiv ist, statt ein Abfrageintervall abzuwarten. Die Veröffentlichung erfolgt nach bestem Bemühen — ein ausgefallener Bus darf die Änderung durch einen Operator nicht fehlschlagen lassen — und die regelmäßige Aktualisierung der Laufzeit bleibt die Rückfallebene.

## Direkte Modulabhängigkeiten

- g-bus — um eine Trigger-Änderung anzukündigen

## Solution-Zugehörigkeit

- Nicht in einer vordefinierten Solution enthalten

## Quelle

`modules/repositories/automation/rp-dag`
