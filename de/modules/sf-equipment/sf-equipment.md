# sf-equipment

## Zweck

Die Werkhalle als ein gemeinsamer Arbeitsbereich: welche Maschinen vorhanden sind,
in welchem Zustand sich jede befindet, welchen Auftrag sie ausführt, was ihre
Telemetrie aktuell meldet, was mit ihr geschehen ist
und was als Nächstes für sie eingeplant ist.

## Struktur

Die Oberfläche stellt drei `setOf`-Ansichten bereit — Maschinen, Journal,
Zeitplan — die der Arbeitsbereich in die permanenten Schaltflächen dieses Tabs
umwandelt, sowie eine `objectOf`-Ansicht für eine Maschine. Das Öffnen eines
Druckers öffnet daher einen Untertab *innerhalb* der Ausrüstung, anstatt von ihr
wegzunavigieren. Wenn nichts ausgewählt ist, zeigt die Oberfläche ihren eigenen
Bildschirm, `EquipmentDashboardView`.

## Zuständigkeitsgrenze

Liest aus `rp-equipment` und schreibt dorthin. Liest `rp-orders` für den Auftrag,
den eine Maschine ausführt, und `rp-telemetry` für ihre Live-Parameter — beides
direkt aus dem Browser, da dort eine Komposition aus zwei Aufrufen hingehört;
keines der beiden Repositories kennt das jeweils andere.

Der Maschinenzustand wird von hier aus geschrieben, weil der Bediener, der neben
der Maschine steht, bis eine Telemetriebrücke ihn meldet, die einzige
Wahrheitsquelle dafür ist.

## Direkte Modulabhängigkeiten

- `g-equipment`
- `g-orders`
- `g-telemetry`

## Lösungszugehörigkeit

- `production`

## Quelle

`modules/surfaces/business/sf-equipment`
