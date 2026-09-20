# rp-files

## Zweck

Die zentrale Dateiabstraktion des Ökosystems: Jedes Modul, das
„Dateien“ benötigt, kommt hierher, statt eine eigene Tabelle aus Namen und Pfaden aufzubauen.
Verwaltet Metadaten, Sammlungen und Chunk-Listen; die Bytes selbst liegen im
Blockspeicher und werden über einen Store-Service-Client erreicht.

## Denkmodell

Datei = Datensatz (Name, Erweiterung, Sammlung, Besitzer) + geordnete Liste von Chunk-
Referenzen im Blockspeicher. Klassifizierung (`detectType`), Materialisierung
und Persistierung arbeiten auf Metadaten — Bytes werden nur bei tatsächlichem Bedarf geladen
(Modell-Staging, Download-Bereitstellung).

## Wert im Ökosystem

Der Einstiegspunkt für die Dateiübernahme:

- Dateien, Chunks, Sammlungen und Metadaten hinter einer API; Chunk-Bytes sind an den Blockspeicher delegiert.
- Jede Domäne bindet eine opake Datei-ID an ihre Entität, statt Bytes zu kopieren.

## Nicht-Ziele

- Kein reiner Blockspeicher — Chunk-Bytes liegen im Block-Store.
- Kein Entpacken von Archiven oder Modellkonvertierung.
## Verantwortungsgrenze

Besitzt Dateidatensätze, Sammlungen und den Lebenszyklus der Chunk-Listen; besitzt keine
Objektspeicher-Implementierungsdetails oder Byte-Transformationen.

## Direkte Modulabhängigkeiten

- Keine — Chunk-Bytes laufen über einen Store-Service-Client, also einen Transport-
  Aufruf wie ihn jeder externe Consumer durchführt, keine Modul-zu-Modul-Verknüpfung.
  rp-files verwaltet Namen, Sammlungen und die Chunk-Liste; es speichert keine Daten.

## Lösungszugehörigkeit

- `requests`

## Quelle

`modules/repositories/data/rp-files`