# lm-secrets

## Zweck

Der gemeinsame Secret-Vault-Adapter: benannte Secret-Werte für die gesamte
Plattform hinter einem Vertrag. Dienste lesen Konfigurations-Secrets hier statt
env-sprawl oder Vault-Clients pro Modul.

## Denkmodell

Dienst fragt nach Secret-Namen → erhält den Wert. Rotation erfolgt an einem
Ort und wird an jeden Verbraucher propagiert. Speicher-Backend-Details bleiben hinter
dem Vertrag.

## Ökosystemwert

Eine Vault-Tür für alle:

- Anbieter-Anmeldedaten, Integrations-Token, OAuth-Secrets — gleiche get/set/delete-Form.
- Jeder Verbraucher hält Secrets aus Code und Konfiguration heraus; Rotation erfolgt an einem Ort.
- Neue Integrationen benötigen keine neue Secret-Verkabelung.

## Nicht-Ziele

- Keine Authentifizierung oder Berechtigungsprüfungen.
- Keine Benutzeridentitätsdatensätze.
## Verantwortungsgrenze

Zuständig für das Speichern, Abrufen und Löschen benannter Secret-Werte; nicht zuständig für
Identität, Berechtigungen oder Sitzungslogik.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/sequrity/lm-secrets`