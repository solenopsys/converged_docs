## Architektur

Converged ist als modulare Ausführungsumgebung aufgebaut, in der Oberfläche, Geschäftslogik und Infrastruktur getrennt sind und gleichzeitig als ein einziges System arbeiten.

Auf Benutzerebene besteht das System aus **Oberflächen**, die den Arbeitskontext organisieren, und **Projektionen** — einzelnen Bildschirmen, die zur Lösung bestimmter Benutzeraufgaben entwickelt wurden.

Die Geschäftslogik ist in **TypeScript** über verschiedene Arten von **Diensten** implementiert: Repositories, Lambdas und Runtimes. Komplexere Prozesse werden zu **Workflows** zusammengesetzt, die über die DAG-Verarbeitungs-Engine Centimanus ausgeführt werden.

Das Fundament des Systems bilden die **Apps**. Sie sind Infrastruktur-Ausführungsumgebungen mit einem kompakten Zig-Kern, in dem TypeScript-Skripte ausgeführt werden. Apps stellen die grundlegenden Fähigkeiten bereit, auf denen Dienste, Workflows und die Benutzeroberfläche aufbauen.

```text
Benutzer
  ↓
Oberflächen
  └── Projektionen
        ↓
Dienste — TypeScript
  ├── Repositories
  ├── Lambdas
  └── Runtimes
        ↓
Workflows
        ↓
Apps — Zig + TypeScript
  ├── Fujin
  ├── Centimanus
  ├── Resonus
  ├── Behemoth
  ├── Ptah
  └── Cruller
        ↓
Kubernetes
  ↓
Edge / Server / Cluster
```

### Oberflächen und Projektionen

Eine **Oberfläche** ist ein Benutzerarbeitsbereich, der um einen bestimmten Arbeitskontext organisiert ist. Sie vereint die Daten, Aktionen und Ansichten, die für die Arbeit in einem bestimmten Bereich erforderlich sind.

Eine Oberfläche muss nicht einem einzelnen Dienst entsprechen. Sie kann Daten und Aktionen aus mehreren Repositories, Lambdas, Runtimes und Workflows kombinieren.

Eine **Projektion** ist ein einzelner Bildschirm innerhalb einer Oberfläche, der für eine bestimmte Funktion entwickelt wurde. Sie stellt Daten in einer für den Benutzer geeigneten Form dar und bietet die erforderlichen Aktionen.

Die Benutzeroberfläche ist daher um **das organisiert, womit der Benutzer arbeitet**, und nicht um die interne Struktur der Dienste.

### Dienste

Die Geschäftslogik von Converged wird in TypeScript geschrieben und in verschiedene Arten von Diensten aufgeteilt.

**Repositories** kapseln den Datenzugriff. Sie bieten eine Schnittstelle zum Lesen, Ändern und Abfragen von Daten und verbergen dabei den zugrunde liegenden Speichermechanismus.

**Lambdas** sind zustandslose Funktionen für einzelne Operationen wie Datenverarbeitung und -transformation, Berechnung, Validierung oder als Gateways zu externen APIs.

**Runtimes** stellen spezialisierte Ausführungsumgebungen für Logik bereit, die ihren eigenen Ausführungskontext benötigt.

Dienste sind die Bausteine des Systems. Sie müssen die Geschäftsprozesse, in denen sie eingesetzt werden, nicht kennen und können von verschiedenen Oberflächen und Workflows wiederverwendet werden.

### Workflows

Ein **Workflow** verbindet Dienste zu einem vollständigen Geschäftsprozess.

Anstatt Dienste durch direkte Aufrufe zu verbinden, definiert ein Workflow, welche Operationen ausgeführt werden müssen, in welcher Reihenfolge, welche Schritte parallel ausgeführt werden können, wo das System auf ein Ereignis warten muss und was beim Fehlschlagen einer Operation geschehen soll.

Zum Beispiel:

```text
Bestellung
  ↓
Zahlung
  ↓
Aufteilung
  ↓
Produktion
  ↓
Lieferung
```

Ein Workflow kann Repositories für Datenoperationen, Lambdas für einzelne Operationen sowie Runtimes oder Apps für spezialisierte Aufgaben verwenden.

### Centimanus

**Centimanus ist die DAG-Engine, die Workflows ausführt.**

Ein Workflow wird als Graph von Operationen dargestellt, während Centimanus seine Ausführung verwaltet: Abhängigkeiten zwischen Schritten, Wiederholungen, das Warten auf Ereignisse, parallele Operationen und Kompensation im Fehlerfall.

Jede Ausführung erzeugt einen Prüfpfad, der zeigt, was gestartet und abgeschlossen wurde, welche Operationen wiederholt wurden und warum ein Fehler auftrat.

Dadurch können lang laufende, robuste Prozesse erstellt werden, die ihren Ausführungsstatus bewahren und nach einem Neustart fortgesetzt werden können.

Dienste bleiben unabhängig, da sie nicht über direkte Aufrufketten verbunden werden müssen, um einen bestimmten Geschäftsprozess zu implementieren.

### Apps

**Apps sind das Infrastrukturfundament von Converged.**

Eine App ist eine leichtgewichtige virtuelle Ausführungsumgebung. Ihr Systemkern ist in **Zig** geschrieben, während veränderliche Logik als **TypeScript-Skripte** ausgeführt wird.

Diese Trennung hält die kritische Infrastruktur in einem kompakten, leistungsfähigen Kern und bewahrt gleichzeitig die Flexibilität von TypeScript für Anwendungslogik und Konfiguration.

Apps stellen die von den übrigen Teilen des Systems verwendeten Infrastrukturfunktionen bereit:

* **Fujin** — Kommunikationsschicht für Befehle, Ereignisse, WebSockets und Maschinentelemetrie.
* **Centimanus** — DAG-Verarbeitung und Workflow-Ausführung.
* **Resonus** — Echtzeit-Gateway für Sprache, Medien, Transkription und KI-Anbieter.
* **Behemoth** — isolierter Multi-Speicher für verschiedene Datentypen.
* **Ptah** — Bereitstellung und Verwaltung der Kubernetes-Topologie.
* **Cruller** — Runtime, in der UI- und TypeScript-Module ausgeführt werden.

Apps sind keine weitere Ebene der Geschäftslogik. Sie stellen die **Infrastruktur- und Ausführungsumgebungen** bereit, in denen die TypeScript-Schicht arbeitet.

### Fujin

**Fujin ist die einheitliche Schicht für Befehle, Ereignisse und Telemetrie.**

Alle Systemkomponenten kommunizieren über Fujin, anstatt sich direkt aufzurufen. Ein Befehl aus der Benutzeroberfläche, ein Workflow-Ereignis, ein Maschinensensorwert oder eine Aktualisierung des Produktionsfortschritts läuft durch dieselbe Kommunikationsschicht.

WebSockets übertragen Änderungen in Echtzeit an die Benutzeroberfläche, ohne Polling.

Da die Kommunikation durch eine einzige Schicht läuft, kann sie zentral verfolgt, wiedergegeben und ratenbegrenzt werden.

**Ergebnis:** Dienste bleiben unabhängig, Echtzeit wird Teil der gemeinsamen Infrastruktur und Systemereignisse werden beobachtbar.

### Resonus

**Resonus ist eine einheitliche Echtzeitschnittstelle für Sprache, Medien und KI.**

Sie verbindet Telefonate, Audiostreams, Transkription und Adapter für KI-Anbieter in einer einzigen Schicht.

Ein Gespräch kann von einem Telefonat zur Transkription und anschließend zur KI-Analyse wechseln, ohne zwischen getrennten Systemen übertragen zu werden. Medien können direkt mit Bestellungen, Geräten und Ereignissen verknüpft werden.

Anbieteradapter kapseln das System gegenüber einzelnen Sprach- und KI-Anbietern.

**Ergebnis:** Sprache, Medien und KI werden Teil der gemeinsamen Workflow-Umgebung, während Anbieter ersetzt werden können, ohne die Anwendungslogik neu zu strukturieren.

### Behemoth

**Behemoth ist das einheitliche Multi-Speicher-System für Converged-Daten.**

Verschiedene Datentypen erhalten geeigneten Speicher: SQL für Bestellungen und Kunden, Dateien für Modelle und Dokumente, Vektoren für die KI-Suche, Cache für häufig verwendeten Status sowie bei Bedarf weitere spezialisierte Speichertypen.

Die Isolierung ist strukturell: Daten aus verschiedenen Arbeitsbereichen werden nicht vermischt und können unabhängig skaliert, gesichert und verschoben werden.

Dasselbe Modell funktioniert bei Edge-, Server- und Cluster-Bereitstellungen. Auf einem kleinen Edge-Gerät können alle Speicherdomänen auf einem einzigen Knoten liegen; in einem Cluster können sie über spezialisierte Speicherhardware verteilt werden.

**Ergebnis:** Daten sind konstruktionsbedingt isoliert, während die Speicherinfrastruktur mit der Installation wachsen kann, ohne die Anwendungsschicht zu verändern.

### Ptah

**Ptah ist der Converged-Bereitstellungsorchestrator auf Kubernetes.**

Er verwaltet die Platzierung von Apps, Containern und Daten entsprechend der Bereitstellungstopologie: Edge, Server oder Cluster.

Der Ptah-Kern ist in Zig geschrieben, während Verwaltungsregeln als TypeScript-Skripte implementiert sind. Dadurch können Platzierung, Rollout-Reihenfolge, Ausfallsicherung und Datenverteilungslogik geändert werden, ohne den Kern neu zu erstellen.

Derselbe Mechanismus wird für verschiedene Installationstypen verwendet — von einem einzelnen Edge-Knoten bis zu einem verteilten Cluster.

**Ergebnis:** Das gesamte System wird über eine einheitliche Bereitstellungsschicht verwaltet, während die Bereitstellungslogik dynamisch und veränderbar bleibt.

### Cruller

**Cruller ist die Runtime für UI- und TypeScript-Module.**

Sie stellt die Umgebung bereit, in der die TypeScript-Logik von Converged ausgeführt wird, einschließlich der UI- und Anwendungsmodule.

Cruller verbindet die dynamische TypeScript-Schicht mit den von Apps bereitgestellten Infrastrukturfunktionen. Dadurch kann sich die Anwendungsschicht weiterentwickeln, ohne den Low-Level-Kern zu verändern.

### Kubernetes und Topologie

Alle Apps und zugehörigen Komponenten werden über **Kubernetes** bereitgestellt.

Converged verwendet unabhängig vom Umfang der Installation dasselbe Architekturmodell:

```text
Edge
  → einzelner Knoten

Server
  → einzelner Server mit mehr Ressourcen

Cluster
  → mehrere Knoten und verteilter Speicher
```

Die physische Topologie ändert sich, das Anwendungsmodell jedoch nicht. Dienste, Workflows, Oberflächen und Projektionen funktionieren auf einem Edge-Gerät genauso wie in einem vollständigen Cluster.

### Einheitliches Modell

Die verschiedenen Teile von Converged sind nach unterschiedlichen Verantwortlichkeiten organisiert:

**Oberfläche** — Arbeitskontext des Benutzers.
**Projektion** — eine bestimmte Funktion und ihre visuelle Darstellung.
**Repository** — Datenzugriff.
**Lambda** — eine einzelne zustandslose Operation.
**Runtime** — eine spezialisierte Ausführungsumgebung.
**Workflow** — ein Geschäftsprozess, der Dienste kombiniert.
**Apps** — Infrastruktur-Ausführungsumgebungen mit einem Zig-Kern und TypeScript im Inneren.
**Fujin** — Kommunikation und Ereignisse.
**Centimanus** — Workflow-Ausführung.
**Resonus** — Echtzeit für Sprache, Medien und KI.
**Behemoth** — Speicher.
**Ptah** — Bereitstellung und Kubernetes-Verwaltung.
**Cruller** — Ausführungsumgebung für UI und TypeScript.

Das zentrale Prinzip von Converged besteht darin, **Benutzerkontext, Anwendungslogik und Infrastruktur zu trennen, ohne sie in dieselbe Struktur zu zwingen**.

Eine Oberfläche kann mehrere Dienste kombinieren. Ein Workflow kann mehrere Operationen kombinieren. Und mehrere Workflows und Dienste können dieselben zugrunde liegenden Apps verwenden.

Das Ergebnis ist ein System, das auf Ebene der Geschäftslogik modular, auf Ebene der Infrastruktur kompakt und aus Sicht des Benutzers einheitlich bleibt.
