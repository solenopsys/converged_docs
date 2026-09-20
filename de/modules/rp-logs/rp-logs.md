# rp-logs

## Zweck

Das einzige Append-only-Journal des Ökosystems: Jeder Dienst, jede Ausrüstung
oder jeder Workflow schreibt „was passiert ist“ hierher, anstatt seinen eigenen Log-
Speicher aufzubauen. Günstige Schreibvorgänge, Lesezugriffe nach Zeit/Quelle.

## Denkmodell

Der Produzent sendet ein Ereignis (Zeit, Quelle, Level, Text/Payload) → es landet auf
dem gemeinsamen Stream. Der Konsument liest einen Ausschnitt nach Quelle oder Intervall. Keine
Aggregation oder Alarmierung im Inneren — nur die Aufzeichnung des Fakts.

## Ökosystemnutzen

Ein Stream, der von allen wiederverwendet wird:

- Dienste: Betriebs-Logs ohne eigenen Speicher pro `rp-*`.
- Ausrüstung: Maschinen-/Gerätelogs — gleiche API, andere Quelle, von 3D-
  Druckern bis zu jedem Modul oder externen System.
- Jeder Produzent schreibt „was passiert ist“ an einen Ort, anstatt seinen
  eigenen Log-Speicher aufzubauen; Audit und Review lesen eine Zeitlinie.

## Nicht-Ziele

- Keine Zähler oder Aggregate.
- Keine numerischen Samples oder Nutzungsdatensätze.
- Kein Tracing verteilter Aufrufe oder Alarmierung.
## Verantwortungsgrenze

Besitzt Log-Ingestion- und Abruf-APIs; besitzt keine Geschäftsmetriken,
Aggregation, Alarmierung oder Tracing-Strategie.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `analitycs`

## Quelle

`modules/repositories/analytics/rp-logs`