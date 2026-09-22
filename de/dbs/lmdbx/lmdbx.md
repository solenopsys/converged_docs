# LMDBX

LMDBX ist der geordnete Schlüssel-Wert-Speicher, der dort verwendet wird, wo Converged direkten Zugriff auf Bytes statt auf SQL benötigt. Der Wrapper öffnet eine Umgebung auf der Festplatte und stellt über Zig- und C-APIs put, get, delete, Transaktionen und Cursor bereit. Cursor machen Bereichsscans und eine geordnete Iteration zu einem Bestandteil derselben Speicherprimitive wie Punktabfragen.

libmdbx speichert seine B+-Bäume in speicherabgebildeten Dateien und verwendet MVCC für Leser. Lesetransaktionen sehen einen stabilen Snapshot, während ein Schreiber Änderungen festschreibt. Dieses Modell eignet sich für Indizes und den Servicestatus, die häufig gelesen und in kurzen Transaktionen aktualisiert werden.

Der Wrapper bindet libmdbx statisch ein und erzeugt native gemeinsam genutzte Bibliotheken für die unterstützten Ziele. Er ist die FFI-Schicht um die Engine und kein separater Datenbankprozess.
