# rp-telemetry

## Zweck

Der gemeinsame technische Health-Feed: Dienste melden „wie es ihnen geht“ (Latenz, Fehler, Ressourcensignale) hier, statt dass jedes Ops-Tool sie einzeln abfragt. Normalisierte Erfassung, eine Abfrageoberfläche für Health.

## Mentales Modell

Der Dienst pusht Health-Events (Quelle, Signal, Zeit, Payload) → Telemetrie normalisiert sie in eine einheitliche Form. Ops-Konsumenten (Dashboards, Incident-Workflows) lesen den Health-Zustand pro Dienst über die Zeit. Die fachliche Bedeutung wird vom Leser zugeordnet, nicht vom Speicher.

## Ökosystemnutzen

Ein Journal für numerische Samples:

- Jeder Producer schreibt (Gerät, Parameter, Wert, Einheit, Zeit)-Zeilen in Hot-/Cold-Stores.
- Eine Zeitlinie für Zahlen jeder Herkunft — Gerätesensoren oder alles andere.

## Nicht-Ziele

- Kein Text-Log-Speicher.
- Keine Nutzungsdatensätze.
- Keine Alarmierungsrichtlinie oder Incident-Behebung.
## Verantwortungsgrenze

Verantwortlich für Erfassung und Normalisierung von Telemetrie-Events; nicht verantwortlich für Produkt-Analytics-Definitionen, Alarmierung oder Behebung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `analitycs`

## Quelle

`modules/repositories/analytics/rp-telemetry`