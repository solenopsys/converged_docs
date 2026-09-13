# rp-files

## Zweck

Stellt APIs für Dateimetadaten und Workflows zur Dateiverwaltung bereit.

## Zuständigkeitsgrenze

Verantwortet Dateidatensätze und dateibezogene Vorgänge; Details der Objektspeicherimplementierung gehören nicht dazu.

## Direkte Modulabhängigkeiten

- `rp-store` — der inhaltsadressierte Blockspeicher, in dem die Bytes jeder Datei liegen.
  rp-files verwaltet Namen, Sammlungen und die Chunk-Liste; es speichert keine Daten.

## Zugehörigkeit zur Lösung

- `requests`

## Quelle

`modules/repositories/data/rp-files`
