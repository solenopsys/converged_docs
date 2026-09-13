# Automatisierung

## Zweck

Verantwortet den Automatisierungsarbeitsbereich: Workflows und deren Ausführungen, die Bus-Trigger, die sie starten, wiederkehrende Zeitpläne und eingehende Webhook-Endpunkte.

## Verantwortungsbereich

Steuert die Arbeitsbereichserfahrung. Führt keine Workflows aus, verwaltet keine Zeitpläne und stellt keine Webhooks zu — stattdessen startet es eine Ausführung über die Laufzeitumgebung und liest das Protokoll aus rp-dag zurück.

## Der DAG-Bereich

- **Workflows** — der Katalog, den die aktive Solution veröffentlicht, schreibgeschützt.
  Einen zu öffnen bedeutet, ihn auszuführen: Parameter werden als JSON typisiert und an
  `centimanus.runWorkflow` übergeben.
- **Ausführungen** — jede Ausführung mit ihrem Status.
- **Ausführungsdetails** — der Baum dessen, was die Ausführung getan hat. Eine Zeile pro Knoten: wie tief er sitzt, ob er abgeschlossen ist und wie lange er gedauert hat. Beim Aufklappen eines Knotens werden die von ihm getätigten Serviceaufrufe und die zurückgegebenen Ergebnisse angezeigt. Auf einen Knoten, der über
  `rt.sub` delegiert hat, folgen die Knoten der Ausführung, an die er delegiert hat, eine Ebene tiefer.
  Eine noch laufende Ausführung aktualisiert sich selbst.
- **Trigger** — „wenn dieses Busthema erscheint, diesen Workflow ausführen“. Thema,
  Workflow, JSON-Parameter, ein/aus.
- **Variablen** — der von `rt.set` geschriebene Workflow-Zustand.

Parameter werden überall als JSON typisiert, anstatt in ein Formular generiert zu werden: Die Parameter eines Workflows gehören ihm selbst und ändern sich mit ihm, sodass ein Textfeld korrekt bleibt, wenn sie sich ändern, und das Eingegebene genau dem entspricht, was der Workflow erhält.

## Direkte Modulabhängigkeiten

- Keine

## Solution-Zugehörigkeit

- Nicht in einer vordefinierten Solution enthalten

## Quelle

`modules/surfaces/automation/sf-automation`
