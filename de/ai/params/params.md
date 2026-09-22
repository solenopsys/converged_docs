# PARAMS

PARAMS extrahiert die Werte, die ein Befehl aus der Anfrage des Benutzers benötigt. Es wird
ausgeführt, nachdem CASE den Befehl erkannt hat. Bei „show order 4815“ wählt CASE den
Bestellbefehl aus, und PARAMS gibt die Bestellnummer zurück. Die Anwendung kann dann
die Bestellansicht mit dieser Nummer bereits eingetragen öffnen.

Der Befehl stellt die von ihm akzeptierten Parameter sowie, sofern relevant, die
verfügbaren Werte bereit, die im Text genannt werden können. PARAMS verwendet das
GLiNER2-ONNX-Modell, um Werte in der Anfrage zu finden und sie den entsprechenden
Parametern zuzuordnen. Derselbe Mechanismus verarbeitet sowohl einen direkten Wert
wie eine Bestellnummer als auch eine benannte Auswahl wie einen Kunden, Status oder
Ausrüstungsgegenstand.

Zusammen wandeln CASE und PARAMS eine Anfrage in einen Befehl und seine Argumente um.
Die Anwendung erhält beide Teile und führt die übliche Navigation oder Aktion aus.
