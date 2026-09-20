# rp-threads

## Zweck

Die einzelne Konversationsebene des Ökosystems: Jedes Modul, in dem Personen
oder Agenten Nachrichten austauschen, speichert keine eigenen Nachrichten — es hält eine
`threadId`, und der Dialog selbst lebt hier.

## Mentales Modell

Entität (Chatraum, Forenthema, Anruf, Anfrage) speichert nur eine `threadId`.
Alle Nachrichten, Reihenfolge und Kontext leben im Thread. Erstellen einer Entität
= Erzeugen einer `threadId` und Übergabe an den Aufrufer, der sie registriert.

## Wert für das Ökosystem

Ein Dialogformat überall:

- Threads und geordnete Nachrichten hinter einer API, indiziert über opake Thread-ID.
- Jede Entität fügt eine Diskussion an, ohne eigene Nachrichtentabellen.

## Nicht-Ziele

- Keine Chaträume oder Forenthemen — nur die dahinterliegenden Nachrichten-Threads.
- Keine Benachrichtigungszustellung oder Dialogzusammenfassungen.
## Verantwortungsgrenze

Besitzt Thread-Lebenszyklus, Nachrichtenreihenfolge und Metadaten auf Thread-Ebene; besitzt
keine Räume/Themen, Mitgliedschaften oder Transport-Gateways für
email/SMS/push.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `ai`

## Quelle

`modules/repositories/communications/rp-threads`