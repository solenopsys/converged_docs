# rp-requests

## Zweck

Service-Request-Erfassung und -Lebenszyklus: Einreichung, Statusübergänge, Dateianhänge (per fileId) und Umwandlung in Aufträge über wf-request-to-order. Die Analyse erfolgt über wf-request-analyze.

## Verantwortungsabgrenzung

Besitzt den Request-Lebenszyklus und Statusübergänge; besitzt nicht den Messaging-Transport, Datei-Bytes oder die Analyseausführung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `requests`

## Quelle

`modules/repositories/business/rp-requests`