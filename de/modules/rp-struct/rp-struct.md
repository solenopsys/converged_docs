# rp-struct

## Zweck

Der gemeinsame Struktur-Builder: wandelt lose Inhalte in typisierte, schemaförmige
Darstellungen um, auf die sich jeder Verbraucher verlassen kann. Ein Modellierungspunkt zwischen Rohinhalten
und Kanal-Rendering.

## Mentales Modell

Rohinhalte rein → Strukturmodellierung wendet Schemata und Formen an → typisierte
Blöcke raus. Kanäle (`sf-*`, Markdown, Notify-Vorlagen) rendern Blöcke
ohne erneutes Parsen der Quelle.

## Nutzen im Ökosystem

Ein typloses JSON-Regal:

- JSON-Dokumente hinter einer Datei-API.
- Jeder Producer speichert strukturierte Blobs ohne eigenes Datei-Handling.

## Nicht-Ziele

- Keine Taxonomie oder Kennzeichnung.
- Kein Markdown-Rendering.
## Verantwortungsgrenze

Verantwortlich für Strukturmodellierung und Formgebung auf Schemaebene; nicht verantwortlich für finales
kanalspezifisches Rendering.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `content`

## Quelle

`modules/repositories/content/rp-struct`