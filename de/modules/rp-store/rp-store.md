# rp-store

## Zweck

Inhaltsadressierter Blockspeicher — die unterste binäre Speicherebene des
gesamten Ökosystems. Speichert Chunks anhand des Content-Hash; weiß nichts über Dateien,
Bestellungen, Benutzer oder Geschäftsobjekte.

## Mentales Modell

Produzent zerlegt Bytes in Chunks → legt sie im Store ab → erhält
Referenzen zurück. Konsument setzt Bytes aus Referenzen wieder zusammen. Der Store
selbst ist eine simple key(blob_hash) → Bytes-Map mit Deduplizierung: ein
identischer, zweimal hochgeladener Chunk wird einmal gespeichert.

## Ökosystemnutzen

Inhaltsadressierte Byte-Grundlage:

- Opake Byte-Blobs per Hash adressiert, einmal gespeichert, überall referenziert.
- Jeder Produzent persistiert Bytes ohne eigenen Binärspeicher.

## Nicht-Ziele

- Keine Dateimetadaten oder Sammlungen.
- Keine Staged-Cache-Einträge.
## Verantwortungsgrenze

Besitzt Block-put/get per Content-Referenz und Chunk-Lebenszyklus; besitzt keine
Benennung/Sammlungen auf Dateiebene oder Geschäftssemantik aufrufender Dienste.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `requests`

## Quelle

`modules/repositories/data/rp-store`