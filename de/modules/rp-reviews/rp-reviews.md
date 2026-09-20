# rp-reviews

## Zweck

Das Bewertungssystem des Shops in drei Tabellen, die drei unterschiedliche Fragen beantworten.

- `reviews` — was ein Kunde gesagt hat, was der Shop darauf geantwortet hat und ob die Bewertung auf der Website angezeigt wird. Die Moderation findet hier statt: Eine Bewertung, die von außerhalb eingegangen ist, wird als `pending` angelegt und ist nur innerhalb der Konsole sichtbar, bis sie jemand veröffentlicht.
- `review_invites` — ein persönlicher, nur einmal verwendbarer Link pro Bestellung und was daraus geworden ist: gesendet, geöffnet, beantwortet, abgelaufen. Das ist der Trichter, den der Shop auswertet.
- `review_settings` — eine JSON-Zeile: die externen Plattformen, der Schwellenwert, die E-Mail-Vorlagen, die Verzögerungen und die erlaubte Anzahl an Nachfassaktionen.

## Zuständigkeitsgrenze

Verantwortlich für Bewertungen, Einladungen und die Einstellungen des Trichters. Kennt keine Bestellungen: `Review.orderId` und `ReviewInvite.orderId` sind undurchsichtige Zeichenfolgen, und die Verknüpfung mit tatsächlichen Bestellungen ist Aufgabe von `wf-order-review-request` (das die Anfrage stellt) und `sf-reviews` (das sie anzeigt). Verantwortet keine Community-Threads.

## Zwei Türen

Der Zugriff erfolgt wie überall über Tags: Eine veröffentlichte Bewertung trägt `public`, alles andere trägt `authenticated` plus `moderator`. Dadurch kann der Shop eine Bewertung bearbeiten, die niemand im Shop verfasst hat.

Die Tür des Kunden ist anders. `getInviteByToken`, `markInviteOpened` und `submitByToken` werden durch das Token selbst autorisiert — eine Berechtigung, keine Sitzung —, sodass das öffentliche Formular ganz ohne Anmeldung funktioniert. Sie geben eine eingeschränkte Ansicht zurück, die weder die Kontaktdaten noch die Einladungs-ID enthält, und `submitByToken` verbraucht den Link bedingt. Dadurch erzeugen zwei Einsendungen aus derselben E-Mail eine Bewertung und eine Ablehnung statt zweier Bewertungen.

## Bewertungssteuerung

`positiveThreshold` verschiebt nur den Schwerpunkt des öffentlichen Formulars und sonst nichts: Bei Erreichen oder Überschreiten wird dem Verfasser zuerst die Möglichkeit angeboten, externe Plattformen zu nutzen; bei einem niedrigeren Wert steht zunächst ein Wort mit dem Shop im Vordergrund. Die Plattform-Links bleiben in jedem Fall sichtbar, denn den Weg zu einer öffentlichen Bewertung nur zufriedenen Kunden zu zeigen, wird von Google und mehreren anderen Plattformen untersagt. Das sichere Verhalten ist die Standardeinstellung.

## Direkte Modulabhängigkeiten

- Keine

## Zugehörigkeit zur Lösung

- `production`

## Quelle

`modules/repositories/business/rp-reviews`
