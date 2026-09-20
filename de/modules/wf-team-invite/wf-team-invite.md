# wf-team-invite

## Zweck

Verwandelt eine eingefügte Liste von Personen — „Name + Adresse“, in jeder Form,
in der ein Mensch sie geschrieben hat — in Benutzerkonten, Rollen,
Mitarbeiterkarten und Einladungen und sendet jeder Person den Link, mit dem sie
sich anmeldet.

Es existiert, weil vier Dienste für eine Zeile dieser Liste gemeinsam arbeiten
müssen (`rp-identity`, `rp-access`, `rp-staff`, `rp-auth` sowie eine Mail-Lambda),
und Microservices rufen sich nicht gegenseitig auf.

## Warum es auch die Privilegiengrenze ist

`rp-access` lehnt ein Benutzer-JWT direkt ab (`@Access("internal")`), daher kann
keine Oberfläche eine Rolle vergeben. centimanus führt dieses Skript mit
`SERVICE_TOKEN` aus, und wer es ausführen darf, ist eine gewöhnliche Berechtigung
— `wf/workflows/wf-team-invite.js(x)` — die am Rand (`signal_provider.zig:146`)
geprüft und in einer voreingestellten Datei festgehalten wird. Deshalb gibt es
im Produkt kein Konzept eines „Administrators“.

Das Skript kann nicht sehen, wer es aufgerufen hat, daher ist die
Eskalationssicherung eine feste Liste: `manager`, `operator`, `viewer`. `owner`
und `root` können hier nicht vergeben werden.

## Aufbau

1. Textquellen — `files.materialize` + `files.extractText` sowie `rawText`;
2. Personen — zuerst `rt.llm`, zeilenweise Regex als Fallback;
3. ein `rt.attempt` pro Person — Benutzer, Basisvoreinstellung + Rolle,
   Gruppen-Tags, Karte, Einladung;
4. das Schreiben — ein eigener Versuch, sodass ein abgelehntes Relay ein Zweig
   und kein verlorenes Konto ist;
5. der Bericht, dessen `staffIds` die Oberfläche in eine offene Tabelle genau
   dieser Personen umwandelt.

Das erneute Ausführen derselben Liste ist unproblematisch: Eine bekannte Adresse
wird `updated`, niemals ein zweites Konto.

## Direkte Modulabhängigkeiten

- `g-access`, `g-auth`, `g-files`, `g-identity`, `g-notify`, `g-ses`, `g-smtp`,
  `g-staff`

## Lösungszugehörigkeit

- `production`

## Quelle

`modules/workflows/wf-team-invite`
