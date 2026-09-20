# rp-counters

## Zweck

Mandantenbezogene Konfiguration externer Analyse-Counter: speichert Tracking-IDs (GA4, GTM, Yandex Metrika, Meta Pixel) oder ein benutzerdefiniertes Head-Snippet, sodass SSR die richtigen Skripte pro Mandant einbinden kann.

## Denkmodell

Der Operator speichert einen Counter (Typ, Tracking-ID oder Snippet, Aktiviert-Flag) → der Store behält die Konfiguration. SSR liest aktivierte Counter für den aktuellen Mandanten und rendert die passenden Tags. Hier werden keine Kennzahlen erfasst, nur die Counter-Einstellungen.

## Mehrwert im Ökosystem

Ein zentraler Ort für die Analytics-Anbindung:

- Externe Counter (GA4, GTM, Metrika, Pixel) und benutzerdefinierte Snippets werden pro Mandant konfiguriert, statt pro Landingpage fest codiert zu sein.

## Nicht-Ziele

- Kein Roh-Event-Speicher.
- Keine numerischen Sample-Journale.
- Keine Nutzungsdatensätze oder Abrechnung.
## Verantwortungsgrenze

Verwaltet Counter-Konfigurationen (Typ, Tracking-ID oder Snippet, Aktiviert-Flag); erfasst keine Metriken, aggregiert keine Nutzung und übernimmt keine Abrechnung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `analitycs`

## Quelle

`modules/repositories/analytics/rp-counters`