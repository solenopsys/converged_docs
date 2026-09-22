# sqlite-vec

`sqlite-vec` bringt Vektorspalten und Abfragen nach nächsten Nachbarn in die von Converged verwendeten SQLite-Speicher. Eine Vektortabelle kann Embeddings neben den Feldern speichern, die das Quellobjekt identifizieren und beschreiben, sodass eine Suchanfrage den Speicher nicht verlassen muss, nur um ähnliche Datensätze zu bewerten.

Die Erweiterung stellt virtuelle `vec0`-Tabellen für Float-, int8- und Binärvektoren bereit. Abfragen geben Zeilen nach Distanz sortiert zurück; Metadaten, zusätzliche Spalten und Partitionsschlüssel bleiben für dieselbe SQLite-Abfrage verfügbar. Dies ist für die semantischen Such- und Abrufpfade der Plattform nützlich, bei denen Filtern und Bewerten zu einer einzigen Operation gehören.

Der Wrapper erstellt die vorgelagerte C-Erweiterung als natives Artefakt. SQLite lädt sie in den Prozess, der die Datenbank besitzt; in dieser Integration gibt es keinen separaten Vektorsuchdienst.
