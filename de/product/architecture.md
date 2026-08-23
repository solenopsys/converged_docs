## Architektur

Converged ist als modulare Plattform entworfen, aber nicht als chaotische Sammlung von Microservices. Die Trennung ist einfach: Die Oberfläche zeigt Daten und startet Aktionen, Runtime führt Prozesse aus, Microservices besitzen Daten, und Adapter verbinden Ausrüstung und externe Systeme.

```text
Nutzer / Kunde
        ↓
UI und Micro-Frontends
        ↓
Runtime: Workflows, Cron, Integrationen, KI-Aktionen
        ↓
Microservices: typisierte APIs und eigene Daten
        ↓
Storage / Behemoth / Dateien / SQL / KV / Metriken
        ↓
Ausrüstung, Messenger, Zahlungen und externe Dienste
```

Microservices bleiben bewusst schlank. Jeder Service ist für seinen Datenbereich, Validierung und eine typisierte API verantwortlich. Er soll die interne Logik benachbarter Services nicht kennen und nicht zum versteckten Zentrum von Geschäftsprozessen werden. Das senkt Kopplung und macht das System leichter wartbar.

Die gesamte bereichsübergreifende Logik wird in Runtime verschoben. Wenn das System einen Auftrag annehmen, mehrere Services abfragen, eine Aufgabe erstellen, eine Benachrichtigung senden, auf ein Ereignis warten und den Status aktualisieren muss, geschieht das in einem Workflow. Runtime speichert selbst keinen persistenten Zustand: Historie, Variablen und Ergebnisse werden über die Services geschrieben, denen ihre Speicher gehören.

Storage ist um Isolation herum aufgebaut. Statt einer gemeinsamen Datenbank erhält jeder Bereich eigene Datengrenzen: SQL, Key-Value, Dateien, Spaltendaten, Vektorindizes oder Graphbeziehungen, wo sie nötig sind. Dieser Ansatz hilft, Workspaces zu verschieben, Zugriff zu begrenzen und eine gemeinsame Datenbank zu vermeiden, in der Daten verschiedener Kunden vermischt werden.

Auch das Frontend ist modular. Die gemeinsame Shell lädt unabhängige Micro-Frontends über eine Import Map, sodass einzelne Bereiche der Oberfläche sich weiterentwickeln können, ohne das gesamte Produkt neu zu bauen. Für den Nutzer bleibt es ein System; für die Entwicklung entstehen klare Verantwortungsbereiche.
