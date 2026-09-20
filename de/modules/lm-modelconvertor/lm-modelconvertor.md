# lm-modelconvertor

## Zweck

Die gemeinsame Modellformat-Brücke: konvertiert Produktionsmodelle zwischen internen und externen Darstellungen (z. B. in GLB-Vorschauen), sodass kein Workflow eine native Konverter-Bibliothek direkt einbindet.

## Mentales Modell

Workflow stellt Modell-Bytes bereit → Konverter transformiert das Format → gibt Vorschau-/konvertierte Bytes als Cache-Refs für `rp-files.persist` zurück. Reine Transformation: keine Speicherung, keine Schätzungen, keine Geschäftsentscheidungen.

## Ökosystem-Nutzen

Ein Konvertierungspunkt für Produktionsmodelle:

- Eine bereitgestellte Datei hinein, konvertierte Ausgaben als Cache-Refs hinaus — gleiche Form für jeden Aufrufer.
- Neue Formate und Konverter-Versionen landen einmal und aktualisieren jeden Analysepfad.
- Hält schwere native Abhängigkeiten aus Workflows und Repositorien heraus.

## Nicht-Ziele

- Kein Dateispeicher und keine Intake-Orchestrierung.
- Kein Vorschau-Rendering oder Slicing-Schätzungen.

## Verantwortungsgrenze

Besitzt Konvertierungs-/Transformationsroutinen; besitzt weder vorgelagertes Modelltraining noch nachgelagertes Serving oder Persistenz.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/convertors/lm-modelconvertor`