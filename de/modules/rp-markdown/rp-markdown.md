# rp-markdown

## Zweck

Die gemeinsame Markdown-Pipeline: Parsing, Transformation und Rendering für
jedes Modul, das mit Textinhalten arbeitet. Ein Parser-Verhalten statt
Varianten pro Oberfläche.

## Mentales Modell

Markdown-Quelle rein → parsen/transformieren → gerenderte Ausgabe (HTML, Blöcke).
Inhaltsautoren schreiben einmal; Docs, Chats, Landingpages und Benachrichtigungen rendern
dieselbe Quelle konsistent.

## Wert für das Ökosystem

Einheitliches Text-Rückgrat:

- Markdown-Dateien plus JSON-Konvertierung hinter einer API.
- Jeder Producer speichert menschlichen Text auf dieselbe Weise statt eigenem Datei-Handling.

## Nicht-Ziele

- Kein typisierter Block-Speicher.
- Kein HTML-Rendering.
## Verantwortungsbereich

Besitzt Markdown-Konvertierungs-/Parsing-Verhalten; besitzt kein Rich-Media-
Transcoding oder Seitenkomposition.

## Direkte Modulabhängigkeiten

- Keine

## Lösungsmitgliedschaft

- `content`

## Quelle

`modules/repositories/content/rp-markdown`