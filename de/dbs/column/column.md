# Stanchion

Stanchion fügt SQLite spaltenorientierte Tabellen hinzu. Es wird verwendet, wenn
ein Converged-Store eine kleine Anzahl von Feldern aus vielen Datensätzen lesen
muss: Messwerte, Ereignisverläufe, Protokolle und andere daten, die nur angehängt
werden. Eine normale SQLite-Tabelle hält eine Zeile zusammen; eine
Stanchion-Tabelle speichert jede Spalte in eigenen Segmenten, sodass eine Abfrage
nur die von ihr genannten Spalten liest.

Stanchion wird über die virtuelle Tabellenschnittstelle von SQLite bereitgestellt.
Eine Tabelle wird mit `USING stanchion` und einem `SORT KEY` deklariert; der
Sortierschlüssel definiert die physische Reihenfolge der Datensätze und ermöglicht
es der Erweiterung, Zeilengruppen zu überspringen, die ein Prädikat nicht erfüllen
können. Werte werden als ausstehende Einfügungen gepuffert und anschließend mit
den von der Erweiterung ausgewählten Kodierungen in Spaltensegmente geschrieben.

Der Wrapper erstellt die Erweiterung für die native SQLite-Laufzeitumgebung.
Stanchion befindet sich noch in der Alpha-Phase: Das Format auf dem Datenträger
und die unterstützten Tabellenoperationen sind noch nicht endgültig festgelegt.
