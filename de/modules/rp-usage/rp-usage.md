# rp-usage

## Zweck

Der gemeinsame Verbrauchszähler: Jede Funktion meldet hier, „wie viel verbraucht wurde",
anstatt Kontingente lokal zu verfolgen. Aggregiert pro Verbraucher und Zeitraum —
die Quelle, aus der Abrechnung und Limits lesen.

## Denkmodell

Funktion erfasst Verbrauch (wer, was, wie viel, Zeitraum) → Nutzung
aggregiert ihn pro Konto/Zeitraum. Die nachgelagerte Rechnungsstellung verwandelt Aggregate in Geld;
Limitprüfungen lesen aktuelle Summen. Die Messung lebt hier, die Preisgestaltung lebt
nachgelagert.

## Ökosystemwert

Ein Nutzungs-Ereignisprotokoll:

- Jede Funktion erfasst (Funktion, Benutzer, Datum)-Zeilen auf die gleiche Weise.
- Solution-Function-Verknüpfungen ermöglichen es jedem Bericht, Aufrufe nach Solution zu gruppieren, ohne Quota-Tabellen pro Modul.

## Nicht-Ziele

- Keine Rechnungsstellung oder Zahlungsausführung.
- Keine Authentifizierung oder Berechtigungsprüfungen.
- Keine Rohzähler für Dashboards.
## Verantwortungsgrenze

Besitzt Nutzungsmessung und -aggregation; besitzt keine Rechnungsstellung, Zahlungsausführung
oder Preisrichtlinie.

## Direkte Modulabhängigkeiten

- Keine

## Solution-Zugehörigkeit

- `analitycs`

## Quelle

`modules/repositories/analytics/rp-usage`