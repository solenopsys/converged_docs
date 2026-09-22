# SPEACH

SPEACH ist der lokale Spracheingabepfad für Converged. Es wandelt Mikrofon- und
Gesprächsaudio in denselben Text um, den CASE und PARAMS von einer Tastatur
empfangen. Eine gesprochene Anweisung kann dadurch in den normalen Befehls- und
Parameterablauf gelangen, ohne Audio an einen entfernten Transkriptionsdienst zu
senden.

Für eine aufgezeichnete Anfrage akzeptiert SPEACH WAV- oder Opus-Audio, wandelt
es in eine monophone Wellenform mit 16 kHz um und führt das lokale CTC-Modell
aus. Bei einer Live-Verbindung dekodiert es Opus-Pakete, verwendet
Sprachaktivitätserkennung zum Erfassen einer Phrase und erzeugt Ereignisse für
Teil- und vollständige Transkripte. Kurze Pausen bleiben innerhalb einer Phrase;
Stille beendet sie. Ein Segment ist auf vierzig Sekunden begrenzt.

Die Erkennung endet beim Text. SPEACH errät nicht, auf welchen Bildschirmbefehl
sich die Wörter beziehen. Das Transkript wird an dieselbe kontextabhängige
Weiterleitung und Parameterextraktion übergeben, die auch für getippte Eingaben
verwendet wird.
