# rp-webhooks

## Zweck

Die einzige Eingangstür für die Außenwelt: Externe Systeme rufen einen
Webhook-Endpunkt auf, und dieses Modul validiert, normalisiert und verteilt Ereignisse
nach innen. Keine Domäne legt ein eigenes Callback-URL-Schema offen.

## Mentales Modell

Externes System sendet POST → Webhook prüft Signatur und Struktur → normalisiertes
Ereignis wird als Zustellung erfasst und an das konfigurierte Topic weitergeleitet.
Zustellversuche und Validierung liegen hier; die fachliche Reaktion erfolgt
nachgelagert.

## Ökosystemnutzen

Ein Eingang für externe Callbacks:

- Endpunktkonfigurationen und Zustelldatensätze hinter einer API.
- Jedes externe System erhält dieselbe Endpunktform statt einer eigenen Anbindung pro Integration.

## Nicht-Ziele

- Keine Workflow-Ausführung.
- Kein Event-Publishing oder Versand von Benachrichtigungen.
## Verantwortungsabgrenzung

Verantwortlich für Webhook-Transport, Validierung und Zustellversuche; nicht verantwortlich
für die fachliche Verarbeitung im Zielsystem.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/repositories/automation/rp-webhooks`