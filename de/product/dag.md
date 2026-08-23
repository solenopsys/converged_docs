## Prozesse

Das Hauptproblem einer wachsenden Werkstatt ist selten, dass noch ein Button fehlt. Häufiger leben Prozesse in den Köpfen der Mitarbeitenden: wer dem Kunden antwortet, wann der Preis berechnet wird, wer die Datei prüft, wann Produktion startet, wer bei Verzögerung informiert wird und was nach dem Versand passiert.

In Converged werden solche Ketten als Workflows beschrieben. Ein typischer Prozess kann von Anfrage über Kalkulation, Freigabe, Warteschlange, Produktion, Qualitätskontrolle, Zahlung, Lieferung und Benachrichtigungen laufen. Der Nutzer baut normalerweise keinen Graphen von Grund auf: fertige Szenarien kommen mit den Lösungen, und die Konfiguration reduziert sich auf Regeln, Rollen, Fristen, Integrationen und Benachrichtigungen.

Technisch wird die Ausführung in die Runtime-Schicht verlagert. Sie führt Workflows, Cron-Aufgaben, Integrationsschritte und Geschäftslogik aus und bleibt dabei stateless: persistente Daten liegen in den Microservices, Runtime ist für die Ausführung der Ketten zuständig. So wird Geschäftslogik nicht über Dutzende Services verstreut, sondern hat einen klaren Ort.

Für komplexe Implementierungen können Workflows erweitert werden. Ein Entwickler beschreibt Szenarien als typisierte TypeScript-Klassen, und KI-Agenten können erlaubte Aktionen innerhalb dieser Szenarien starten. Für normale Nutzer ist das Ziel aber ein anderes: keinen Editor bauen, sondern einen fertigen Prozess aktivieren und ein kontrolliertes Ergebnis erhalten.
