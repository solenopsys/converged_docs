# RyuGraph

RyuGraph stellt den Graphspeicher für Daten bereit, deren Bedeutung durch die
Verbindungen zwischen Datensätzen bestimmt wird: Abhängigkeiten, Besitz,
Topologie, Herkunft und ähnliche beziehungsintensive Modelle. Es handelt sich
um eine eingebettete Property-Graph-Engine mit Cypher-Abfragen, sodass eine
Traversal und die dafür erforderlichen Joins im nativen Prozess ausgeführt
werden, anstatt im Anwendungscode neu erstellt zu werden.

Die Engine speichert Graphdaten auf der Festplatte und führt analytische
Graphabfragen mit spaltenbasierter Speicherung, komprimierten
Adjazenzstrukturen und vektorisierter Abfrageverarbeitung aus. Converged
verwendet den Wrapper, um diese Engine neben seinen anderen
Speicherkomponenten als native gemeinsam genutzte Bibliothek verfügbar zu
machen.

Der Build lässt die vorgelagerten Sprachbindungen, Beispiele, die Shell und
Benchmark-Ziele absichtlich weg. Das resultierende Artefakt enthält die
Graph-Engine und die von der Plattform benötigte ABI.
