# sf-chats

## Zweck

Chatrooms als drei separate Tabs: die Raumliste, die Unterhaltung eines Raums und
die Mitgliedschaft eines Raums. Zu verwalten, wer sich in einem Raum befindet, und zu lesen, was die Mitglieder gesagt haben, sind
zwei Aufgaben und daher zwei Tabs.

## Verantwortungsgrenze

Verantwortet die Raumnavigation, den Unterhaltungsbildschirm und die Bearbeitung der Mitgliedschaft. Nachrichten
gehören zu `rp-threads` und werden direkt aus dem Browser gelesen; Dateien gehören zu
`rp-files` über eine `link`-Nachricht.

## Erstellung eines Raums

`createRoom` auf `rp-chats` erzeugt die Raum-ID und die Thread-ID und zeichnet den
Ersteller aus dem Token als `owner` auf; diese Oberfläche registriert den Thread anschließend bei
`rp-threads`. `rp-chats` ruft niemals ein anderes Repository auf.

## Live-Aktualisierungen

Eine neue Nachricht wird jedem Mitglied namentlich über Fujins `pushrouter` zugestellt,
niemals an den gesamten Mandanten: Die Existenz eines privaten Raums ist nicht öffentlich, selbst wenn sein
Inhalt hinter dem Lesepredicate verborgen bleibt. Die Push-Nachricht enthält nur Bezeichner.

## Direkte Modulabhängigkeiten

- `effector`, `front-core`, `g-chats`, `g-threads`, `signal-channel`, `threads-state`

## Lösungsmitgliedschaft

- `communications`

## Quelle

`modules/surfaces/communications/sf-chats`
