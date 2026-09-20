# rp-auth

## Zweck

Die zentrale Anlaufstelle für den Nachweis von „wer du bist“: Sitzungen, Anmeldeinformationen und
Token-Ausstellung für das gesamte Ökosystem. Keine Domäne betreibt ein eigenes Login.

## Mentales Modell

Benutzer legt Anmeldeinformationen vor → Auth validiert und stellt eine Sitzung/ein Token aus →
jeder nachgelagerte Aufruf überträgt es und die Zugriffsschicht entscheidet, was damit getan werden darf.
Login beweist Identität; Berechtigungen sind eine separate Ebene.

## Nutzen für das Ökosystem

Ein Login-Backend für alle Oberflächen:

- Magic Links, Refresh-Sitzungen und OAuth-Client-Datensätze an einem Ort.
- Jedes Frontend meldet Benutzer auf dieselbe Weise an, statt eigener Sitzungstabellen.

## Nicht-Ziele

- Keine Berechtigungsrichtlinien.
- Keine Benutzerprofildatensätze.

## Verantwortungsgrenze

Besitzt Auth-Abläufe und Token-/Sitzungs-Ausstellungslogik; besitzt keine
OAuth-Anbieter-Adapter von Drittanbietern oder Autorisierungsrichtlinien-Auswertung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `security`

## Quelle

`modules/repositories/sequrity/rp-auth`