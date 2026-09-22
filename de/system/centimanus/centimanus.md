# Centimanus-Workflow-Laufzeit

Centimanus führt die mehrstufigen Prozesse aus, die ansonsten unabhängige
Converged-Module verbinden. Auftragsrouting, Benachrichtigungen, Genehmigungen,
KI-gestützte Arbeit und Produktionsabläufe können sich als Workflows
weiterentwickeln, ohne die Orchestrierung in Domänendienste zu verlagern.

## Wiedergabefähige Ausführung

Ein Workflow ist ein Programm, dessen bedeutungsvolle Operationen in benannte
Knoten unterteilt sind. Centimanus führt einen noch nicht abgeschlossenen Knoten
aus, zeichnet dessen Ergebnis auf und wertet den Workflow anschließend erneut
aus. Abgeschlossene Knoten geben ihre gespeicherten Ergebnisse zurück, anstatt
ihre Seiteneffekte zu wiederholen.

```text
erster Durchlauf:   Auftrag finden -> Ergebnis speichern
zweiter Durchlauf:  Auftrag wiedergeben -> Maschine reservieren -> Ergebnis speichern
dritter Durchlauf:  beides wiedergeben -> Bediener benachrichtigen -> abschließen
```

Verzweigungen und Schleifen können von früheren Ergebnissen abhängen, sodass der
Graph aus dem Prozess selbst entsteht und nicht aus einem separaten statischen
Diagramm. Die aufgezeichneten Knotenergebnisse machen den Fortschritt explizit
und ermöglichen es, die Ausführung ab dem ersten noch nicht abgeschlossenen
Schritt fortzusetzen.

## Warum Workflows getrennt sind

Domänen-Microservices in Converged besitzen Daten und kleine geschäftliche
Fähigkeiten. Sie rufen einander nicht auf, um einen durchgängigen Prozess
umzusetzen. Dadurch werden verborgene Ketten vermieden, in denen eine Änderung
oder ein Fehler in einem Dienst unerwartet viele andere beeinflusst.

Centimanus ist der Ort, an dem die domänenübergreifende Koordination sichtbar
ist. Ein Workflow kann Dienste aufrufen, KI-Arbeit anfordern und den nächsten
Schritt auswählen, während jeder Dienst auf seine eigene Grenze fokussiert
bleibt.

## Bereitstellung von Workflows

Lösungen bestimmen, welche Workflows aktiv sind. Ptah veröffentlicht diese
Auswahl, der DAG-Dienst stellt die ausgewählten Deskriptoren bereit, und
Centimanus lädt die entsprechenden Inhalte über den inhaltsadressierten Proxy
von Ptah. Ein Workflow, der nicht Teil der aktiven Lösung ist, steht nicht zur
Ausführung zur Verfügung.

Dadurch werden vier Belange getrennt: Produktauswahl, Inhaltsbereitstellung,
Ausführung und Beobachtbarkeit. Jeder dieser Bereiche kann sich ändern, ohne
die Workflow-Laufzeit in eine Modulregistrierung oder einen
Bereitstellungscontroller zu verwandeln.

## Zuverlässigkeitsgrenze

Centimanus zeichnet abgeschlossene Knotenergebnisse auf, doch externe
Operationen müssen weiterhin ihre eigenen Idempotenzregeln einhalten. Die
Workflow-Telemetrie dient der Übersicht; sie entscheidet nicht über den
Ausführungsstatus. Geschäftsdaten verbleiben in den Diensten, die für sie
zuständig sind, anstatt zum Zustand der Workflow-Engine zu werden.

## Rolle im System

Centimanus empfängt Arbeit und ruft Dienste über Fujin auf. Es nutzt den
Plattformspeicher für den Workflow-Fortschritt und meldet Lebenszyklusereignisse
für die Überwachung. Es besitzt keine Domänendatensätze, wählt keine aktiven
Lösungen aus und leitet keine Nachrichten zwischen anderen Peers weiter.
