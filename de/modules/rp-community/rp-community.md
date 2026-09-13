# rp-community

## Zweck

Forumsstruktur und Zuständigkeit: Abschnitte, Themen, wer sie verfasst hat und wer sie sehen darf. Die Diskussion unter einem Thema steht nicht hier — ein Thema enthält eine `threadId`, und die Nachrichten liegen in `rp-threads`.

## Zuständigkeitsgrenze

Verwaltet Abschnitte und Themen. Ruft `rp-threads` oder ein anderes Repository nicht auf: `createTopic` erzeugt eine `threadId` und gibt sie zurück, und der Aufrufer registriert den Thread und schreibt den Eröffnungsbeitrag selbst.

## Identität und Urheberschaft

`createdBy` wird niemals von einem Aufrufer akzeptiert. Der Wert wird über `getCurrentWorkspaceContext()` aus dem verifizierten Token gelesen, das `messaging-backend` gegenüber allen Angaben im Envelope bevorzugt. Themen- und Thread-IDs werden aus demselben Grund hier erzeugt — eine ID, die ein Client wählen kann, ist eine ID, die er stehlen kann, und die Zugriffstag-Tabelle enthält keinen Objekttyp, um die Kollision zu erkennen.

## Sichtbarkeit

Abschnitte und Themen enthalten eine `visibility`-Spalte (`public` | `authenticated` | `private` | `tagged`), und ein neues Thema übernimmt den Wert seines Abschnitts, sofern es nicht nach etwas Eingeschränkterem fragt. Die Tags hinter `tagged` gehören in die gemeinsame Relation `access_tags`, die in `access-control.md` beschrieben ist; dieser Teil ist noch nicht implementiert, daher wird `visibility` heute erfasst, aber nicht durchgesetzt.

## Sperrung

`touchTopicActivity` ist die einzige Stelle, an der eine Sperre durchgesetzt werden kann: `rp-threads` akzeptiert eine Nachricht, ohne zu wissen, dass Themen existieren, daher ruft eine Ansicht dies nach dem Posten auf und behandelt eine Ablehnung als fehlgeschlagenen Beitrag.

## Direkte Modulabhängigkeiten

- `back-core`, `nrpc`, `g-community`

## Zugehörigkeit zur Lösung

- `communications`

## Quelle

`modules/repositories/communications/rp-community`
