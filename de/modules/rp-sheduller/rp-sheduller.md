# rp-sheduller

## Zweck

Der gemeinsame Zeitauslöser: Cron-Zeitpläne und ihre Ausführungshistorie für das
gesamte Ökosystem. Jeder wiederkehrende Job registriert sich hier, anstatt seine
eigene Timer-Schleife auszuführen.

## Denkmodell

Der Operator definiert einen Cron-Eintrag (welcher Workflow, wann, mit welchen Args) → die
Laufzeitumgebung löst planmäßig aus → die Historie erfasst, was ausgeführt wurde und wie es endete.
Dieses Modul speichert und listet Einträge; es führt selbst nichts aus.

## Nutzen für das Ökosystem

Eine Uhr für wiederkehrende Arbeiten:

- Cron-Zeilen, Ausführungsverlauf und Statistiken hinter einer API.
- Jeder wiederkehrende Job benötigt nur eine Cron-Zeile — keine neue Timer-Infrastruktur.

## Nicht-Ziele

- Keine Workflow-Definition oder -Ausführung.
- Keine einmaligen Trigger — nur wiederkehrende Zeitpläne.
## Verantwortungsbereich

Besitzt CRUD/Liste/Statistiken für Cron-Einträge und Verlaufseinträge; führt keine
Workflows, Timer, Wiederholungen oder Hintergrundverteilung aus.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- In keiner vordefinierten Lösung enthalten

## Quelle

`modules/repositories/automation/rp-sheduller`