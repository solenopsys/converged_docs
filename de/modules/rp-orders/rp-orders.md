# rp-orders

## Zweck

Auftragslebenszyklus: Erstellung, Aktualisierungen, Auflistung und Nachverfolgung. Dateien werden per fileId angehängt (rp-files), Diskussionen laufen über eine threadId (rp-threads), der Abschluss kann Einladungen zu Bewertungen auslösen.

## Verantwortungsgrenze

Besitzt Bestelldatensätze und Statusübergänge; besitzt keinen Dateispeicher, kein Messaging und keine Bewertungsmechanismen.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/repositories/business/rp-orders`