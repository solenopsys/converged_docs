# UVtools-Direktadapter

Der UVtools-Adapter bereitet Dateien für Harzdrucker vor. Er führt `UVtoolsCmd`
für geslicte Dateien aus, wobei er Schichten untersuchen, eine Datei
validieren, reparieren, zwischen unterstützten Formaten konvertieren,
Miniaturansichten extrahieren sowie Dateieigenschaften oder erkannte Probleme
melden kann. Diese Arbeit findet statt, bevor eine Datei an einen
Druckeradapter übergeben wird.

Der Wrapper hält UVtools als externe ausführbare Datei. Seine API stellt sowohl
den rohen Argumentpfad als auch benannte Vorgänge für Konvertierung,
Untersuchung, Vergleich, Miniaturansichtsextraktion und Problemmeldung bereit.
Er gibt die Standardausgabe, die Standardfehlerausgabe, den Beendigungsstatus
und den Adapterstatus des untergeordneten Prozesses an den Aufrufer zurück.

UVtools selbst muss auf dem Host installiert sein. Der Wrapper stellt die
Prozessgrenze bereit: Befehlszeitüberschreitung, Arbeitsverzeichnis,
Ausgabelimits und Ergebniserfassung.
