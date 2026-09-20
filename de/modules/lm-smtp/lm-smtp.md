# lm-smtp

## Zweck

SMTP-Zweig des gemeinsamen Notification-Fan-outs: reiner Provider-Transport hinter dem rp-notify-Vertrag.

## Ökosystemwert

Die Domäne sendet einmalig eine Notify-Absicht über rp-notify → dieser Adapter stellt über SMTP zu. Das Austauschen oder Hinzufügen von E-Mail-Anbietern berührt niemals Domänen.

## Nicht-Ziele

Keine Kanalrichtlinien, Wiederholungen oder Vorlagen — das sind rp-notify und die aufrufende Domäne.


## Verantwortungsgrenze

Besitzt den SMTP-Transport und die Zustellungsbehandlung auf Protokollebene; besitzt keine übergeordnete Benachrichtigungsorchestrierung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/providers/lm-smtp`