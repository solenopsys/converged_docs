# rp-notify

## Zweck

Der einzelne Benachrichtigungs-Fan-out des Ökosystems: Jede Domäne sagt einmal „Benutzer informieren“, und dieses Modul wählt Kanäle, Richtlinie und Wiederholungsversuche. Domänen greifen niemals direkt auf SMTP-/SMS-/Push-APIs zu.

## Denkmodell

Domäne sendet eine Benachrichtigungsabsicht (wer, was, Vorlage, Dringlichkeit) → Notify löst Kanäle und Zustellrichtlinie auf → externe Provider-Adapter übernehmen den eigentlichen Versand. Wiederholungen und Kanal-Fallback leben hier, die Nachrichtenbedeutung lebt in der Domäne.

## Wert für das Ökosystem

Ein einziger „Benutzer informieren“-Speicher:

- Vorlagen, Kanäle, Profil und Versanddatensätze hinter einer API.
- Jede Domäne hält ihre Benachrichtigungstexte und Zustelldatensätze an einem Ort.

## Nicht-Ziele

- Nicht die Nachrichtenzustellung selbst — nur Vorlagen, Kanäle und Versanddatensätze.
- Keine Dialog-Threads.

## Verantwortungsbereich

Verantwortet Orchestrierung von Benachrichtigungen und Zustellrichtlinie; verantwortet keine Low-Level providerspezifischen Versandadapter oder domänenspezifische Auslöserlogik.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/repositories/communications/rp-notify`