# rp-events

## Zweck

Das gemeinsame Journal des Business-Event-Bus: Jede Domäne veröffentlicht hier „was passiert ist“, ohne ihre Konsumenten zu kennen. Aufträge, Anfragen, Geräte, Zahlungen — alle sprechen eine Event-Sprache.

## Mentales Modell

Der Producer sendet ein typisiertes Ereignis (kind, entity, time, payload) → es landet im gemeinsamen Feed. Konsumenten (Workflow-Trigger, Benachrichtiger, Analysen) abonnieren nach Art und reagieren. Der Publisher ruft den Konsumenten niemals direkt auf.

## Nutzen im Ökosystem

Entkopplungspunkt für Zustandsänderungen:

- Typisierte Geschäftsereignisse werden einmal veröffentlicht und über eine API zurückgelistet.
- Jede Domäne protokolliert „was passiert ist“, ohne ihre Leser zu kennen.

## Nicht-Ziele

- Nicht das rohe Protokollband.
- Keine Zähler oder Aggregate.
- Nicht die Workflow-Ausführung selbst.
## Verantwortungsgrenze

Besitzt Ereigniserstellung, Speicherung und Abruf; besitzt keine verbraucherseitige Geschäftsverarbeitung oder Workflow-Ausführung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/repositories/business/rp-events`