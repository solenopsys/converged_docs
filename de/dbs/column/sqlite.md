# SQLite

SQLite ist die relationale Speicher-Engine hinter den nativen Datenbank-Wrappern.
Sie speichert eine Datenbank in einer lokalen Datei und führt SQL im aufrufenden Prozess aus. Dadurch kann ein Converged-Dienst seine Datensätze, Indizes und Transaktionen nahe an dem Code halten, der sie verwendet.

Dieselbe SQLite-Verbindung dient auch als Host für spezialisierte Tabellen. Stanchion fügt spaltenbasierte virtuelle Tabellen für analytische Lesezugriffe hinzu; `sqlite-vec` ergänzt Vektortabellen und Distanzabfragen. Gewöhnliche Tabellen und diese Erweiterungen können sich eine Datenbank teilen und am selben Workflow auf Anwendungsebene teilnehmen.

Dieser Wrapper bildet die native SQLite-Grenze: Er stellt die Bibliothek und den Pfad zum Laden von Erweiterungen bereit, die von der übergeordneten Speicherimplementierung verwendet werden.
