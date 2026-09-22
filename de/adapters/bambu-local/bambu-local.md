# Bambu-Lab-Lokaladapter

Mit dem Bambu-Lab-Lokaladapter kann Converged mit einem Bambu-Lab-Drucker über dessen
lokale Netzwerkschnittstelle arbeiten. Er verbindet sich mit dem MQTT-over-TLS-Endpunkt
des Druckers, authentifiziert sich mit dem LAN-Zugangscode und adressiert das Gerät über
die Seriennummer. Die Drucksteuerung und Telemetrie bleiben im lokalen Netzwerk; die
Bambu Cloud ist nicht Bestandteil dieses Pfads.

Der Adapter veröffentlicht Befehle zum Pausieren, Fortsetzen, Stoppen sowie für rohes
JSON und G-Code. Er abonniert Gerätemeldungen und leitet den neuesten Status,
Druckerinformationen, Fehler und Drucktelemetrie über Callbacks weiter. Aufrufer können
ebenfalls einen JSON-Schnappschuss anfordern, wenn sie den aktuellen Status synchron
benötigen.

Die Standardverbindung akzeptiert das selbstsignierte Zertifikat, das Drucker im
LAN-Modus üblicherweise präsentieren. Die erweiterte Verbindungs-API akzeptiert ein
CA-Zertifikat, wenn eine Zertifikatsüberprüfung erforderlich ist.
