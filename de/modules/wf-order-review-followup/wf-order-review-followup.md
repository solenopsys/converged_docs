# wf-order-review-followup

## Zweck

Die einmalige Erinnerung. Jeder Durchlauf nimmt einen Bewertungslink, der gesendet wurde, für
die konfigurierte Anzahl an Tagen unbeachtet geblieben ist und noch nicht so oft erinnert wurde,
wie es erlaubt ist, und fragt ein weiteres Mal nach.

## Warum dies ein Workflow ist

Die Auswahl ist es nicht: `reviews.findInvitesToFollowUp` ist eine Abfrage zu Einladungen
und gehört zu `rp-reviews`. Dieser Ablauf ergänzt den Namen der Bestellung
für die E-Mail und den Versand — zwei Dienste in einem Prozess, was hier die Definition eines
Workflows ist.

## Was er bewusst niemals tut

Er erinnert niemals jemanden, der das Formular geöffnet hat. Die Person hat die Bitte gelesen und sich dagegen entschieden,
etwas zu schreiben; erneut zu fragen, macht aus einer Bewertungsanfrage Spam. Diese Bedingung liegt
in der Repository-Abfrage und nicht in diesem Ablauf, damit ein zukünftiger Aufrufer sie nicht
vergessen kann.

Eine verweigerte Erinnerung lässt die Einladung auf `sent` statt auf `failed`: Die erste E-Mail
wurde tatsächlich versendet, und der Kunde kann noch darauf antworten.

## Aufbau

```
read-settings → find-due (sent, nie geöffnet, innerhalb des Limits)
              → read-order (nur für den Namen)
              → send-email → count-followup
```

Das Zählen der Erinnerung macht sie *einmalig*: Dieselbe Abfrage wird diesen Link nicht erneut
zurückgeben. `dryRun` rendert die E-Mail und zählt nichts. `maxFollowups: 0`
deaktiviert Erinnerungen vollständig, und der Ablauf endet, bevor er fragt.

## Parameter

- `from` (erforderlich) — Absenderadresse.
- `ses` (erforderlich) — `SesCredentials`.
- `shopName`, `delayDays`, `maxFollowups`, `dryRun` — Überschreibungen; die Standardwerte
  stammen aus `reviews.getSettings()`.

## Direkte Modulabhängigkeiten

- `g-orders`
- `g-reviews`
- `g-ses`

## Quelle

`modules/workflows/wf-order-review-followup`
