# Valkey

Valkey stellt Converged einen In-Memory-Schlüssel-Wert-Dienst bereit. Er wird für
Daten verwendet, die von Valkey-Befehlen und Ablaufsemantik profitieren: zwischengespeicherte Werte,
Zähler, kurzlebiger Koordinationszustand und andere gemeinsam genutzte Werte, die
schnell gelesen oder geändert werden müssen.

Der Wrapper kompiliert den mitgelieferten Server zu einer nativen Bibliothek und startet ihn in
einem eigenen Thread. Der Server lauscht an der konfigurierten lokalen Adresse und dem konfigurierten Port;
der Wrapper kommuniziert anschließend über libvalkey mit ihm. Seine C-API startet und stoppt den
Server, prüft seine Bereitschaft, meldet die Speichernutzung und führt die unterstützten
Schlüssel-Wert-Operationen aus.

Diese eingebettete Konfiguration deaktiviert Snapshots und AOF, verwendet eine einzige logische
Datenbank und setzt innerhalb des konfigurierten Speicherlimits die `allkeys-lru`-Räumungsrichtlinie ein. Diese
Einstellungen machen den Lebenszyklus explizit, anstatt eine externe Valkey-Installation zu übernehmen.
