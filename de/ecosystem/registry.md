## Das Modulregister

Das Register ist weder ein separates Dokument noch eine Datenbank. Es ist der Quellbaum selbst.

```text
modules/
├── microservices/<domain>/ms-<name>    eine Datendomäne und ihre API
├── surfaces/<domain>/sf-<name>   ein zur Laufzeit eingebundener Bildschirm
├── workflows/wf-<name>                 ein Prozess für die DAG-Laufzeit
├── types/<domain>/                     NRPC-Verträge
└── solutions/                          welche Module gemeinsam ausgeliefert werden
```

Ein Modul existiert, weil sein Verzeichnis existiert. Es gehört zu einer Domäne, weil es im Ordner dieser Domäne liegt. Es gehört zu einer Lösung, weil `solutions/solutions.json` es benennt. Es gibt keinen vierten Ort, an dem dies wiederholt werden muss — deshalb wird die Ökosystemseite der Website erzeugt, indem der Baum durchlaufen wird, statt eine Liste zu bearbeiten.

Der Zweck eines Moduls wird aus seiner `README.md` übernommen: der erste Absatz unter `## Purpose` (bei Oberflächen `## UI Purpose`) und der Absatz unter der Überschrift zur Verantwortungsgrenze. Diese beiden Absätze sind der Vertrag des Moduls in verständlicher Sprache, und jedes Modul muss sie enthalten.

Eine Produktschicht auf der Basis — zum Beispiel `club` — ist auf dieselbe Weise aufgebaut und kann die Domänenebene weglassen: Ihre Module liegen direkt in `modules/microservices/ms-<name>`. Der Build versteht beide Strukturen.
