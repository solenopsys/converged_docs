## Prozesse

### Architektur ohne Abhängigkeitsnetzwerk

Converged ist eine offene Plattform, auf der die Community Tausende von Diensten, Modulen und Workflows erstellen, verbinden und kontinuierlich aktualisieren kann. Diese Komponenten entwickeln sich unabhängig voneinander weiter und müssen dennoch präzise zusammenarbeiten.

In herkömmlichen Servicearchitekturen entsteht dadurch mit wachsendem System ein ernstes Problem: Jede neue Komponente kann neue Verbindungen zu bestehenden Komponenten einführen. Direkte Aufrufe, Abhängigkeitsketten, Service-Mesh, Routing und Fehlerbehandlung bilden allmählich eine separate, immer komplexer werdende Schicht. Wenn Tausende von Komponenten unabhängig entwickelt und aktualisiert werden, wird die Pflege eines solchen Verbindungsnetzwerks zunehmend schwierig.

**Converged löst dieses Problem auf architektonische Weise: Dienste wissen nichts voneinander und rufen sich niemals direkt auf.** Statt eines Netzes direkter Abhängigkeiten verwendet das System zwei Kompositionsebenen: Die UI kombiniert Daten, während Workflows Operationen zu Geschäftsprozessen verbinden.

### Komposition von Daten und Geschäftsprozessen

Auf UI-Ebene können Daten aus mehreren Diensten parallel angefordert und innerhalb eines einzigen Benutzerkontexts kombiniert werden. Leichtgewichtige zustandslose Funktionen können Daten aus verschiedenen Quellen abrufen, transformieren und die für eine Oberfläche oder Projektion benötigten Daten erzeugen. Die Dienste selbst müssen nicht wissen, wo oder neben welchen anderen Daten ihre Ergebnisse verwendet werden.

Operationen und automatisierte Prozesse werden über **Workflows** abgewickelt. Ein Workflow ist ein einzelnes Szenario, das aus einer Folge von Skripten und Operationen besteht. Er definiert, welche Aktionen ausgeführt werden sollen, in welcher Reihenfolge, welche Schritte parallel laufen können, wo der Prozess auf ein Ereignis warten muss und was geschieht, wenn eine Operation fehlschlägt.

Die Plattform kann **Tausende unabhängiger Workflows** enthalten. Jeder kann bestehende Dienste und Skripte verwenden, ohne direkte Abhängigkeiten zwischen den Diensten selbst zu erzeugen.

Beispielsweise kann ein Workflow eine Anfrage, Preisberechnung, Genehmigung, Einreihung, Produktion, Qualitätskontrolle, Zahlung und Lieferung kombinieren. Ein anderer Workflow kann dieselben Dienste für einen völlig anderen Prozess verwenden.

### Ausführung durch Centimanus

**Centimanus** ist die DAG-Engine, die Workflows ausführt. Sie verwaltet Abhängigkeiten zwischen Schritten, parallele Ausführung, das Warten auf Ereignisse, Wiederholungen, Fehlerbehebung und den Zustand lang laufender Prozesse.

Jeder Workflow ist ein unabhängiges Szenario, während Centimanus einen einheitlichen Ausführungsmechanismus für alle bereitstellt. Das Hinzufügen eines neuen Prozesses erfordert daher weder Änderungen an bestehenden Diensten noch neue direkte Verbindungen zwischen ihnen.

Dies ist besonders für eine offene Plattform wichtig. Die Community kann neue Dienste, Skripte und Workflows hinzufügen, ohne eine Kaskade von Abhängigkeiten im gesamten System zu erzeugen.

**Dadurch können Anzahl und Umfang der Komponenten und Prozesse auf Tausende anwachsen, ohne dass die Komplexität ihrer Beziehungen proportional zunimmt.** Dienste bleiben unabhängig, Daten werden auf UI-Ebene zusammengesetzt und Operationen über einzelne Workflows kombiniert.

Dies verschafft Converged einen architektonischen Vorteil bei der Skalierung: Das System kann durch neue Komponenten und Szenarien erweitert werden, ohne dass ihre Interaktion zu einem immer größeren Netz direkter Abhängigkeiten wird.

### Offenes Ökosystem

Für Entwickler werden neue Fähigkeiten über Dienste, zustandslose Skripte und Workflows hinzugefügt. KI-Agenten können außerdem erlaubte Aktionen innerhalb bestehender Szenarien ausführen und dabei innerhalb definierter Regeln und Einschränkungen bleiben.

Für normale Benutzer bleibt diese Komplexität verborgen. Sie müssen keine Dienste verwalten, Graphen erstellen oder ihre Abhängigkeiten verstehen. Fertige Workflows werden mit Lösungen ausgeliefert, während Benutzer sie über Regeln, Rollen, Fristen, Integrationen und Benachrichtigungen konfigurieren können.

**Der Benutzer aktiviert einfach den benötigten Prozess und erhält ein verwaltetes Ergebnis.**
