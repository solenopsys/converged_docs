# CuraEngine

CuraEngine bereitet FDM- und FFF-Aufträge für Converged vor. Ausgehend von einem Modell und einem Druckerprofil teilt es die Geometrie in Schichten auf, erzeugt Außenwände, Füllungen und Stützstrukturen und schreibt anschließend den G-Code, den ein Materialextrusionsdrucker ausführt.
Es ist der Slicer im Cura-Ökosystem, der hier ohne die Desktop-Oberfläche verwendet wird.

Der native Wrapper führt `CuraEngine slice` in einem isolierten temporären Verzeichnis aus und gibt den erzeugten G-Code über seine C-ABI zurück. Durch die Ausführung des Slicers außerhalb des Prozesses werden dessen globaler Zustand und Fehlerpfade eingegrenzt, sodass ein ungültiges Modell oder Profil nicht den Prozessor beendet, der den Slice-Vorgang angefordert hat.

Der Wrapper bereitet einen Auftrag vor; er sendet keinen G-Code an einen Drucker. Die Weiterleitung und Ausführung werden später vom entsprechenden Geräteadapter übernommen.
