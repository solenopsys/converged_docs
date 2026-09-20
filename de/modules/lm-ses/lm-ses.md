# lm-ses

## Zweck

SES-Zweig des gemeinsamen Notification-Fan-outs: AWS-E-Mail-Transport hinter dem rp-notify-Vertrag.

## Wert im Ökosystem

Massen- und Transaktionsmails (Review-Einladungen, Bestellaktualisierungen, Teameinladungen) laufen über eine SES-Integration. Anmeldeinformationen werden über lm-secrets aufgelöst.

## Nicht-Ziele

Keine Kanalrichtlinie oder Vorlagen — das liegt bei rp-notify und der aufrufenden Domäne.


## Verantwortungsbereich

Besitzt die SES-spezifische Sendeintegration und Zuordnung; besitzt nicht die Domäne zur Erstellung von E-Mail-Vorlagen.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/providers/lm-ses`