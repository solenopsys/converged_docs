# lm-compressors

## Zweck

Das gemeinsame Byte-Arbeitstier der Datei-Pipeline: Assemblierung, Dekomprimierung,
ZIP-Parsing, Ausgabe-Chunking und Staging. Zustandslos — keine `files`- oder
`store`-Clients im Inneren; es gibt Bytes und Cache-Referenzen zurück, Persistenz
ist Aufgabe des Workflows.

## Denkmodell

Workflow übergibt Chunk-Refs + Operation (entpacken, assemblieren, chunken) → Lambda
leistet reine Byte-Arbeit → gibt gestagte Bytes/Cache-Refs zurück. Es entscheidet nie,
was eine Datei bedeutet, und speichert niemals etwas.

## Wert im Ökosystem

Ein Ort, an dem Archiv-Bytes berührt werden:

- Komprimierte Chunks rein, gestagte Einträge raus — eine Entpack-Form für jeden Aufrufer.
- Jedes zukünftige Archiv- oder Komprimierungsformat landet hier einmal und wertet jeden Intake zugleich auf.

## Nicht-Ziele

- Kein Dateispeicher und keine Klassifizierung.
- Keine Modellkonvertierung oder Vorschau-Rendering.
## Verantwortungsgrenze

Besitzt Byte-Assemblierung, Dekomprimierung, Archiv-Parsing, Ausgabe-Chunking und
Staging; besitzt keine Dateidatensätze oder Persistenz.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `requests`

## Quelle

`modules/lambdas/data/lm-compressors`