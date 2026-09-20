# lm-push

## Zweck

Push-Zweig des gemeinsamen Notification-Fan-outs: Web-/Mobile-Push-Transport hinter dem rp-notify-Vertrag.

## Nutzen im Ökosystem

Echtzeit-Hinweise für Chats, Bestellungen, Anfragen – zusammen mit E-Mail/SMS aus einer einzigen Notify-Absicht zugestellt.

## Nicht-Ziele

Kein Targeting und keine Geschäftslogik – das liegt bei rp-notify und der aufrufenden Domäne.

## Verantwortungsgrenze

Besitzt die Push-Provider-Integrationsdetails; besitzt keine geschäftliche Targeting-Logik für Benachrichtigungen.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/providers/lm-push`