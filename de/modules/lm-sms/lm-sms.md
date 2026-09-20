# lm-sms

## Zweck

SMS-Zweig des gemeinsamen Benachrichtigungs-Fan-outs: Provider-Transport hinter dem rp-notify-Vertrag.

## Ökosystemwert

Dringende Pings (Incidents, Einladungscodes, Statusänderungen) erreichen Telefone, während andere Kanäle die Langform übernehmen. Gleiche Intent-API wie E-Mail/Push.

## Nicht-Ziele

Keine Kampagnen- oder Segmentierungsregeln — die aufrufende Domäne entscheidet.

## Verantwortungsbereich

Besitzt SMS-Provider-Konnektivität und Payload-Formatierung; besitzt keine Kampagnen-/Business-Segmentierungsregeln.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/providers/lm-sms`