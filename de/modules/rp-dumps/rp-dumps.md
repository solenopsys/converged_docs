# rp-dumps

## Zweck

Der gemeinsame Export-Dock: Jede Domäne erstellt hier Snapshots ihrer Daten für Migration,
Backup oder Übergabe, statt ein eigenes Dump-Format zu erfinden. Paketierte
Snapshots mit Abruf-Metadaten.

## Mentales Modell

Domäne fordert einen Dump an (Umfang, Zeit) → Dump wird erzeugt und paketiert →
Abruf-Metadaten verweisen auf das gespeicherte Artefakt.
Erzeugung und Buchführung liegen hier; langfristige Archivierung liegt anderswo.

## Ökosystemnutzen

Eine Export-Story für die Plattform:

- Speicherauflistung, Statistiken, Kompaktierung und Dump-Segmente hinter einer API.
- Jede Domäne wird exportierbar ohne eigene Snapshot-Maschinerie.

## Nicht-Ziele

- Kein Live-Datei-Serving.
- Kein paralleler Byte-Speicher.
## Verantwortungsbereich

Besitzt Dump-Erzeugung, Paketierung und Abruf-Metadaten; besitzt nicht
die langfristige Archivierungsplattform.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/repositories/data/rp-dumps`