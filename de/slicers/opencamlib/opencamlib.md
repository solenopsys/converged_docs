# OpenCAMLib

OpenCAMLib liefert den geometrischen Teil des CNC-Werkzeugpfadablaufs in Converged.
Die Bibliothek arbeitet mit STL-Oberflächengeometrie und Fräserparametern, um Fräsbahnen
und Schätzungen zu berechnen. Während CuraEngine additive Bahnen Schicht für Schicht erstellt,
modelliert OpenCAMLib den Kontakt des Fräsers mit dem Werkstück für subtraktive
Operationen.

Die Bibliothek implementiert Drop-Cutter-, Push-Cutter- und Waterline-Operationen und
unterstützt zylindrische, Kugel-, Torus-, Kegel- und zusammengesetzte Fräser. Der lokale
Wrapper stellt die kleine benötigte C-ABI für den bestehenden STL-Frässchätzungsablauf bereit
und erstellt die vorgelagerte C++-Bibliothek als natives Artefakt.

OpenCAMLib erzeugt Werkzeugpfadgeometrie. Die Nachbearbeitung in das Befehls-
dialekt eines bestimmten Controllers und die anschließende Ausführung auf einer Maschine
gehören zu den nachfolgenden CAM- und Ausrüstungspfaden.
