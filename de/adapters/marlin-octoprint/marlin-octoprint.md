# Marlin-Serielladapter

Der Marlin-Adapter ist der direkte serielle Pfad von Converged zu einem FDM-Drucker,
der mit Marlin-Firmware betrieben wird. Er öffnet den seriellen Anschluss des Druckers, sendet
G-Code und verfolgt die Protokolldetails, die einen zuverlässigen Druckdatenstrom gewährleisten:
Zeilennummern, Prüfsummen, `ok`-Antworten und Neuübertragungsanforderungen.

Die API deckt die Jobsteuerung, Bewegung und Referenzfahrten, Heizelemente, Extrusion,
SD-Kartenoperationen, den Not-Aus und rohen G-Code ab. Firmware-Antworten werden in den
Druckerstatus geparst: Temperaturen, Koordinaten, Identität, SD-Fortschritt und Druckstatus.
So kann die Geräteebene ein einheitliches Zustandsmodell verwenden, während der Adapter
weiterhin das serielle Protokoll der Firmware spricht.

Der Name bleibt aus Kompatibilitätsgründen mit der umgebenden API bestehen. Der Wrapper
führt weder OctoPrint aus noch ruft er dessen HTTP-API auf; er kommuniziert direkt mit Marlin.
