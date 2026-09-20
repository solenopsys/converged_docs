# rp-classifier

## Zweck

Der gemeinsame Labeling-Dienst: Jede Erfassung leitet Rohinhalte hierher und erhält
Kategorien, Labels oder Intents zurück. Eine Klassifizierungslogik statt
domänenspezifischer If-Ketten.

## Denkmodell

Der Produzent sendet Roh-Elemente (Dateien, Texte, Anfragen) → der Klassifizierer weist
Labels zu → der Aufrufer routet nach Label (Produktionsmodell vs. Zeichnung, dringend
vs. Rauschen). Labels sind Empfehlungen; die Geschäftsentscheidung bleibt beim Aufrufer.

## Wert im Ökosystem

Ein einziges Taxonomie-Regal:

- Baumknoten und Schlüsselzuordnungen hinter einer API.
- Jede Erfassung löst Labels aus demselben Baum auf statt aus eigenen Wörterbüchern.

## Nicht-Ziele

- Keine Dateibytes oder Konvertierung.
- Keine JSON-Dokumentspeicherung.
## Verantwortungsgrenze

Besitzt Klassifizierungslogik und Label-Zuweisung; besitzt keine Quell-
Inhalte-Erfassungspipelines und kein nachgelagertes Geschäfts-Routing.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/repositories/content/rp-classifier`