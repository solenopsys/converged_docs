# wf-order-review-request

## Zweck

Kontur 2 des Bewertungssystems: den Kunden nach Abschluss der Arbeit einmalig fragen.

Ein Durchlauf findet eine Bestellung, deren Abschluss lange genug zurückliegt, die einen Kunden zum Anschreiben hat und bei der noch nie eine Anfrage gestellt wurde; erzeugt ihren persönlichen, einmalig verwendbaren Bewertungslink in `rp-reviews`; und sendet die Anfrage über `lm-ses`.

## Warum dies ein Workflow ist

Die Frage „Welche abgeschlossenen Bestellungen wurden noch nicht angefragt?“ erstreckt sich über zwei Dienste, die nichts voneinander wissen dürfen: `rp-orders` weiß nicht, was eine Bewertung ist, und `rp-reviews` behandelt `orderId` als undurchsichtige Zeichenkette. Zwei Listen nebeneinanderzustellen, ist genau der Zweck eines Flows – und `rt.node` sorgt dafür, dass die Link-Erzeugung einen Neustart übersteht, ohne einen zweiten Link zu erzeugen.

## Aufbau

```
read-settings → list-finished (completed, updatedAt ≤ now − delay)
              → list-invites (which of those were already asked)
              → create-invite → send-email → mark-sent | mark-failed
```

Ein Mail pro Durchlauf, damit eine blockierte Adresse die dahinterliegende Warteschlange nie aufhält und der Zeitplan die Rate bestimmt. `dryRun` rendert die Mail und erzeugt nichts: Eine Probe, die einen aktiven Link hinterlässt, würde dazu führen, dass der nächste echte Durchlauf diese Bestellung als bereits angefragt überspringt.

Eine abgelehnte Mail kommt von `lm-ses` als `{ success: false }` zurück, nicht als Exception, daher ist sie ein gewöhnlicher Zweig, der die Einladung als `failed` markiert – keine Fehlergrenze.

## Parameter

- `from` (erforderlich) – Absenderadresse.
- `ses` (erforderlich) – `SesCredentials`.
- `shopName` – wird in den Vorlagen in `{{shopName}}` eingesetzt.
- `delayHours` – überschreibt `ReviewSettings.requestDelayHours` für ein Nachholen.
- `dryRun` – rendern und beenden.

Betreff, Text, Link-Basis und Verzögerung stammen aus `reviews.getSettings()`, sodass der Shop seine eigene Formulierung ändern kann, ohne diesen Flow anzupassen.

## Direkte Modulabhängigkeiten

- `g-orders`
- `g-reviews`
- `g-ses`

## Quelle

`modules/workflows/wf-order-review-request`
