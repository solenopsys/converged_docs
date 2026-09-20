# rp-contexts

## Zweck

Der gemeinsame benannte Kontextspeicher für KI: Prompts, Sprachvarianten und
Domänenwissen befinden sich hier, statt in jedem Workflow hartcodiert zu sein.
Versioniert nach Name, aufgelöst nach Sprache.

## Mentales Modell

Workflow oder Assistent fragt einen Kontext nach Namen (+ Sprache) an → erhält den
aktuellen Text. Redakteure aktualisieren Kontexte, ohne Verbraucher erneut bereitzustellen.
Speicherung und Abruf befinden sich hier; Prompt-Engineering liegt bei den Redakteuren.

## Nutzen für das Ökosystem

Ein Wissensregal für KI-Pfade:

- Benannte Kontexte mit Sprachvarianten hinter einer API.
- Jeder KI-Pfad löst denselben benannten Kontext auf, statt eigener Prompt-Kopien.

## Nicht-Ziele

- Kein Chatverlauf oder Dialog-Threads.
- Keine Prompt-Ausführung — nur gespeicherte Kontexttexte.
## Verantwortungsabgrenzung

Besitzt Speicherung und Abruf benannter KI-Kontexte und Sprachvarianten;
besitzt keine Modellanbieter-Infrastruktur und kein Dialogverhalten.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- `ai`

## Quelle

`modules/repositories/ai/rp-contexts`