## Ein Modul hinzufügen

Die Schritte sind für die Basisplattform und eine Produktschicht gleich.

1. **Erstelle das Verzeichnis** nach Konvention: `modules/microservices/<domain>/ms-<name>` für einen Service, `modules/surfaces/<domain>/sf-<name>` für einen Bildschirm, `modules/workflows/wf-<name>` für einen Prozess.
2. **Deklariere den Vertrag** in `modules/types/<domain>/` und generiere die Clients mit `bun run gen`. Der Client erscheint als Paket `g-<name>` und kann im Browser, von einem anderen Prozess auf dem Bus und innerhalb eines Workflows verwendet werden.
3. **Schreibe die README** mit einem Abschnitt `## Purpose` und einem Abschnitt zur Verantwortungsgrenze. Der erste Absatz jedes Abschnitts landet im Register der Website — schreibe sie für Leser, nicht für dich selbst.
4. **Füge das Modul einer Lösung hinzu**, wenn es nicht allein ausgeliefert wird: Trage seinen Kurznamen in `modules/solutions/solutions.json` ein und deklariere seine Abhängigkeiten.
5. **Baue die Dokumentation neu**: `bun run build:doc` im Repository-Stammverzeichnis. Das Modul erscheint im Register, und die Zähler auf der Ökosystemseite werden neu berechnet.

Was du nicht tun musst: Modullisten in den Websitedaten bearbeiten, die Beschreibung auf der Landingpage wiederholen oder das Modul irgendwo anders registrieren. Die Generierung läuft nur in eine Richtung — von den Quellen in die Daten, niemals zurück. Alles unter `data/` wird beim nächsten Build überschrieben.

Was das Review von einem Modul verlangt: Es greift nicht auf den Speicher eines anderen Moduls zu, umgeht den Bus nicht durch direkte Aufrufe, deklariert nur die tatsächlich verwendeten Berechtigungen und erweitert seinen Verantwortungsbereich nicht stillschweigend.
