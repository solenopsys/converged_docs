# MTConnect CppAgent

Dieser Wrapper führt den MTConnect-C++-Agenten für Converged aus. Der Agent empfängt
Signale von konfigurierten Maschinenadaptern und veröffentlicht sie als einen MTConnect-
Datenstrom. Dadurch erhalten CNC-Anlagen, Roboter, Sensoren und andere Geräte in der
Fertigung ein gemeinsames Modell, das der Rest der Plattform nutzen kann.

Der Wrapper startet `cppagent` mit einer `agent.cfg`, wartet, bis sein HTTP-Endpunkt
bereit ist, und beendet den Prozess, wenn der Dienst freigegeben wird. Die Geräte-XML
beschreibt das Gerätemodell; die Agentenkonfiguration legt Adapter,
Ports und Laufzeitoptionen fest. Clients lesen die resultierenden `/probe`-, `/current`-
und `/sample`-Endpunkte des laufenden Agenten.

Die Integration basiert bewusst auf einem separaten Prozess. Sie verwendet die native
Konfiguration und HTTP-Schnittstelle des Agenten, anstatt dessen C++-Bibliothek in die
Zig-Laufzeit einzubetten.
