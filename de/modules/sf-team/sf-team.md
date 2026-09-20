# sf-team

## Zweck

Das Team als ein Arbeitsbereich: wer hier arbeitet, was jede Person tun darf und wer
hereingebeten wurde, aber noch nicht angekommen ist.

## Projektionen

Vier `setOf`-Ansichten, die die Shell in die permanenten Schaltflächen des Tabs
verwandelt — **Team**, **Einladungen**, **Zeitplan**, **Rechte** — sowie eine
`objectOf`-Ansicht, die Karte der Person, die als Untertab *innerhalb* desselben
Bereichs geöffnet wird. Wenn nichts gedrückt wurde, zeigt der Bereich seinen eigenen
Bildschirm (`team.statistic`, aufgelöst über seine `setOf`-Ansicht, das Muster, das
`sf-logs` und `sf-equipment` verwenden).

## Was diese Oberfläche prägt

**Die Konsole kann nichts gewähren.** `rp-access` ist `@Access("internal")` und
die Laufzeit weist ein Benutzer-JWT zurück, bevor irgendeine Berechtigung geprüft wird
(`messaging-access.ts:176`). Daher führt jede Operation, die ändert, was jemand tun darf,
`wf-team-invite` auf centimanus aus, das das Service-Token des Clusters besitzt.
Wer es ausführen darf, ist die gewöhnliche Gewährung `wf/workflows/wf-team-invite.js(x)`,
die in einer Preset-Datei liegt — diese Gewährung umfasst vollständig, „wer Personen
hinzufügen darf“.

Drei Einladungsmethoden auf `rp-identity` tragen einen methodenbezogenen `@Access("user")`,
sodass die Zustellungsspalte ohne einen Workflow für jede Tabellenaktualisierung gelesen
werden kann; sie werden durch `rp/identity/listInvites(r)` in den Besitzer- und Manager-Presets
beschränkt.

Die Projektion **Rechte** wird im Browser aus dem Kader und den Einladungen zusammengesetzt,
weil der Dienst, der die tatsächliche Antwort kennt, von hier aus nicht abgefragt werden kann.
Sie zeigt die dokumentierte Absicht — die Rolle, die einer Person zugewiesen wurde, und die
Tags, die damit einhergingen — und nicht eine Auslesung ihres aktuellen Tokens.

## Operationen

`team.member.import` (der Zweck, für den diese Kontur existiert — eine eingefügte Liste hinein,
eine ausgefüllte Tabelle genau dieser Personen hinaus), `team.member.create`,
`team.member.save`, `team.member.setRole`, `team.member.deactivate`,
`team.invite.revoke`, `team.shift.create`.

Drei davon werden im Chat-Katalog in `llm.json` veröffentlicht.

## Direkte Modulabhängigkeiten

- `front-core`, `g-centimanus`, `g-identity`, `g-staff`

## Lösungszugehörigkeit

- `production`

## Quelle

`modules/surfaces/sequrity/sf-team`
