# rp-identity

## Zweck

Das gemeinsame Profilregister: ein Identitätsdatensatz pro Person oder Servicekonto,
verlinkt aus jeder Domäne. Bestellungen, Chats, Mitarbeiterkarten — alle verweisen
auf dasselbe Profil, statt Namen und Attribute zu kopieren.

## Denkmodell

Identität = stabiler Datensatz (id, Kernattribute, Lebenszyklusstatus). Domänen
speichern die Identitäts-ID und lesen Attribute bei Bedarf; sie verzweigen das
Profil niemals. Auth weist die Identität nach, Zugriff prüft sie, Domänen referenzieren sie.

## Wert im Ökosystem

Ein „Wer“ für die Plattform:

- Benutzerdatensätze, Auth-Methoden-Verknüpfungen und Einladungen an einem Ort.
- Jede Domäne speichert eine opake Benutzer-ID und liest Attribute bei Bedarf, statt Profile zu verzweigen.

## Nicht-Ziele

- Kein Login oder Sitzungen.
- Keine Berechtigungen.
- Keine Organisationsstruktur- oder Personalsemantik.
## Verantwortungsbereich

Besitzt Identitätsdatensätze und den Lebenszyklusstatus von Identitäten; besitzt keine
feingranularen Berechtigungsrichtlinien oder Authentifizierungsabläufe.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `security`

## Quelle

`modules/repositories/sequrity/rp-identity`