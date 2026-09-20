# rp-access

## Zweck

Die gemeinsame Autorisierungsebene: Jedes `rp-*` fragt hier „darf dieser Akteur dies tun“, anstatt eigene Berechtigungsprüfungen zu erfinden. Ein Berechtigungsbaum, eine Auswertungsregel, durchgesetzt, bevor ein Handler ausgeführt wird.

## Mentales Modell

Zwei Fragen, zwei Ebenen: Der Methodenzugriff („darf X überhaupt aufrufen“) wird im Berechtigungsbaum gehalten und vom Guard durchgesetzt; der Objektzugriff („welche Zeilen gibt der Aufruf zurück“) wird pro Entität ausgewertet. Ohne Ersteres könnte jeder `deleteTopic` aufrufen.

## Wert im Ökosystem

Einzige Vertrauenswurzel für Entscheidungen:

- Berechtigungsbaum, Presets, Tags und ausgestellte Tokens befinden sich an einem Ort.
- Jeder Dienst prüft denselben Baum, anstatt eigene Richtlinientabellen aufzubauen.

## Nicht-Ziele

- Kein Login und keine Sitzungsausstellung.
- Keine Speicherung von Geheimnissen.
## Verantwortungsgrenze

Besitzt die Auswertung von Autorisierungsrichtlinien und Zugriffsbereiche; besitzt keine Identitätsprüfung/Authentifizierungs-Anmeldung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `security`

## Quelle

`modules/repositories/sequrity/rp-access`