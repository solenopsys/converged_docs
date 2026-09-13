# Systemarchitektur

Converged ist eine modulare Betriebsschicht für Fertigungsunternehmen. Die Benutzeroberflächen, Domänendienste, Workflow-Engine, Speicherung, Medien-Gateway und industriellen Prozessoren bilden ein System, ohne zu einer Anwendung zu werden.

Die Architektur trennt drei Arten von Arbeit:

- Domänenmodule besitzen Geschäftsdaten und benutzerorientierte Funktionen;
- native Laufzeitdienste übertragen Nachrichten, führen Workflows aus, speichern Daten und verarbeiten Echtzeitmedien;
- die Steuerungsebene entscheidet, welche Teile für jede Plattform und jeden Mandanten ausgeführt werden.

## Ein Nachrichtenbus

Laufzeitkomponenten kommunizieren über Fujin. Jeder Prozess öffnet eine Verbindung, registriert ein Ziel und sendet Nachrichten an logische Ziele. Der Absender benötigt weder die Adresse noch den Bereitstellungsort des Empfängers.

```text
browser and mobile clients
          |
          v
          Fujin message bus
       /     |      |      \
      ui     ms  Centimanus Resonus
              \      |      /
               \  Behemoth /
```

Dadurch werden der HTTP-Aufrufgraph und das Servicenetz aus der Anwendungsebene entfernt. Routing, Anfragekorrelation und vertrauenswürdiger Mandantenkontext werden im gemeinsamen Nachrichtenumschlag übertragen. Ein empfangender Prozess wählt anschließend den angeforderten Service oder Handler innerhalb seiner eigenen Grenze aus.

## Kernlaufzeit

| Komponente | Verantwortung |
| --- | --- |
| Fujin | Verbindet Laufzeit-Peers und leitet Nachrichten an den aktiven Besitzer eines Ziels weiter. |
| Behemoth | Stellt isolierten SQL-, Schlüssel-Wert-, Spalten-, Vektor-, Graph- und Dateispeicher bereit. |
| Centimanus | Führt mehrstufige Geschäftsworkflows als wiedergabefähige Graphen aus. |
| Resonus | Verarbeitet Echtzeitmedien, Anrufe, Transkription und KI-Sitzungen. |
| Ptah | Gleicht die gewünschte Plattform, Lösungen und Mandanten mit Kubernetes-Ressourcen ab. |

Die Komponenten sind bewusst eng gefasst. Fujin versteht keine Geschäftsdienste. Behemoth orchestriert keine Geschäftsabläufe. Centimanus besitzt keine Domänendaten. Resonus entscheidet nicht über die Mandantenidentität. Ptah erstellt und konfiguriert Workloads, nimmt aber nicht an der Laufzeitkommunikation teil.

## Module und Lösungen

Geschäftsfunktionen werden als Microservices, Oberflächen und Workflows bereitgestellt. Eine Lösung ist eine deklarative Auswahl dieser Module für ein bestimmtes Betriebsszenario, etwa Auftragsabwicklung, Produktionsplanung oder Anlagenüberwachung.

Microservices besitzen ihre Daten und stellen typisierte Verträge bereit. Sie rufen einander nicht auf, um einen Prozess zu koordinieren. Sequenzen über mehrere Domänen hinweg gehören in Workflows, die Centimanus jeweils einen dauerhaften Schritt ausführt. So bleiben Domänenmodule klein und eine Lösung kann sie kombinieren, ohne versteckte Kopplung zu erzeugen.

## Datenisolierung

Jeder Microservice besitzt eine eigene physische Speicherwurzel. Behemoth kann viele Wurzeln aus einem Prozess bedienen, bewahrt jedoch deren Eigentumsgrenzen und verweigert das Erstellen von Daten außerhalb der konfigurierten Einbindungen.

Dasselbe Modell skaliert über verschiedene Bereitstellungsprofile hinweg:

- eine Edge-Installation kann eine Behemoth-Instanz für die Plattform ausführen;
- eine größere Installation kann Bereiche über Speicher-Shards aufteilen;
- eine Cloud-Installation kann eine isolierte Speicherinstanz pro Mandant ausführen.

Eine Änderung der Topologie verändert den Anwendungscode nicht, weil Peers weiterhin logische Ziele und Speichergrenzen adressieren.

## Steuerungsebene

Ptah ist die Steuerungsebene und nicht mit Fujin verbunden. Ptah beobachtet die deklarierten Ressourcen für Plattform, Lösung und Mandant, berechnet die gewünschten Workloads und gleicht sie mit Kubernetes ab.

```text
Platform + Solutions + Tenants
              |
              v
             Ptah
              |
              v
Deployments, Services, volumes, configuration and routes
```

Diese Trennung ermöglicht es der Laufzeit, sich auf den Geschäftsverkehr zu konzentrieren, während das Bereitstellungsmodell Platzierung, Speichertopologie, Mandantenrouten und Lebenszyklus behandelt. Dadurch können dieselben Anwendungs-Images in einem kompakten Edge-Cluster oder in einer mandantenfähigen Cloud-Umgebung ausgeführt werden.

## Vertrauenswürdiger Kontext

Der Mandantenbereich wird am Plattformrand festgelegt und im Nachrichtenumschlag übertragen. Laufzeitdienste verwenden diesen vertrauenswürdigen Kontext, anstatt einen Mandanten aus Anwendungspayloads abzuleiten. Speicherplatzierung, Serviceaufrufe und Mediensitzungen bewahren dieselbe Bereichsgrenze.

Zusammen ermöglichen logische Nachrichtenübertragung, isolierter Speicher, wiedergabefähige Workflows und eine separate Steuerungsebene, dass Converged modular bleibt, ohne die Komplexität verteilter Systeme in jedes Geschäftsmodul zu verlagern.
