# Zusammengeführte Befehlszeilenschnittstelle

Die Converged CLI ist eine auf Bediener ausgerichtete Befehls-Engine. Sie stellt
eine einheitliche Befehlsoberfläche für Plattformdiagnosen, Automatisierung,
Speicher- und Domänenoperationen bereit und ermöglicht es gleichzeitig, dass
jede Funktion in ihrem eigenen Befehlsmodul verbleibt.

## Modulare Befehlsoberfläche

Der CLI-Kern enthält keine feste Registrierung von Geschäftsbefehlen. Beim
Start liest er ein oder mehrere über `--commands` angegebene Verzeichnisse und
lädt für jeden Befehlsabschnitt das ausgewählte TypeScript-Modul. Ein Modul
exportiert eine Factory, die einen Prozessor zurückgibt; der Prozessor legt
seine Befehle fest und leitet jeden Befehlsnamen an einen Handler weiter.

```text
bun cli <section> <command> [param]
          |          |
          |          +-> command handler
          v
  command module -> processor -> generated NRPC client
```

Dadurch lässt sich die CLI erweitern, ohne ihre Laufzeitumgebung zu ändern. Eine
Lösung oder ein Produkt kann ein Befehlsverzeichnis hinzufügen, und ein neues
`<section>.ts`-Modul wird zu einem neuen CLI-Abschnitt. Der Kern lädt für die
Ausführung nur den angeforderten Abschnitt, sodass ein optionales oder fehlerhaftes
Modul nicht verhindern kann, dass unabhängige Befehle ausgeführt werden.

`BaseCommandProcessor` stellt die gemeinsame Befehlszuordnung, die
Hilfeausgabe, die Fehlerweitergabe und ein einheitliches Auflistungsverhalten
bereit. Module konzentrieren sich auf ihre eigenen Argumente und
Domänenaktionen; der Runner verwaltet den Verbindungsaufbau, die
Lebenszyklusberichte, die Zeitmessung, den Exit-Status und das Herunterfahren
des Kanals.

## Ein Autorisierungsmodell

Alle NRPC-fähigen Befehlsmodule verwenden dieselbe CLI-Sitzung und denselben
autorisierungsweg. Die CLI liest zunächst das Benutzer-JWT aus der lokalen
Sitzungsdatei und verwendet `SERVICE_TOKEN`, wenn keine Sitzung verfügbar ist.
Die Benutzersitzung hat Vorrang, da Bedieneraktionen möglicherweise die
Identität des Aufrufers erfordern.

Das Token wird während des gemeinsamen Fujin-WebSocket-Handshakes gesendet und
auch der NRPC-Client-Konfiguration bereitgestellt. Wenn eine gespeicherte
Sitzung abgelehnt wird, entfernt der Runner sie aus der aktiven Verbindung und
versucht es einmal erneut mit dem Service-Token, sofern eines konfiguriert ist.
Authentifizierungsfehler werden einheitlich gemeldet, mit dem Hinweis, sich
erneut anzumelden, anstatt den einzelnen Befehlsmodulen die Verwaltung des
Tokenstatus zu überlassen.

Die Autorisierung wird weiterhin vom empfangenden Dienst durchgesetzt. Die CLI
überträgt die Zugangsdaten und den Workspace-Bereich des Aufrufers; sie
interpretiert keine Berechtigungen und gewährt lokal keinen Zugriff. Ein Befehl
kann nur dann auf den WebSocket-Kanal verzichten, wenn er absichtlich mit einem
Nicht-NRPC-Endpunkt kommuniziert, etwa bei einer direkten Diagnoseoperation.

## NRPC-Integration

Befehlsmodule erstellen Clients aus generierten `g-<service>`-Paketen und
übergeben ihnen die gemeinsame Konfiguration
`createCliNrpcClientConfig`. NRPC serialisiert den typisierten Methodenaufruf in
eine WebSocket-Anfrage, die an ein logisches Fujin-Ziel und einen Dienst
adressiert ist. Fujin leitet sie an den aktiven Laufzeit-Peer weiter, und der
Dienst wendet seine normale Zugriffsrichtlinie an, bevor er die Methode
ausführt.

Derselbe Kanal unterstützt gewöhnliche Anfrage-Antwort-Methoden und
Streaming-Methoden. Anfragekennungen, Deadlines, die Reihenfolge der Antworten
und die Behandlung von Verbindungsfehlern sind im CLI-Kanal zentralisiert,
sodass jedes Modul dasselbe Verhalten erhält, ohne Protokollcode neu
implementieren zu müssen.

## Zuständigkeitsgrenze

Die CLI ist für die Befehlsermittlung, den Lebenszyklus der Befehlsausführung,
die Auswahl der lokalen Sitzung und den gemeinsamen NRPC-/WebSocket-Clientkanal
zuständig. Sie ist nicht für die fachliche Geschäftslogik, die
Berechtigungsentscheidungen, die Dienstimplementierung oder das Fujin-Routing
zuständig. Diese Verantwortlichkeiten verbleiben bei den Befehlsmodulen, den
Backend-Diensten und der Laufzeitinfrastruktur, die den Aufruf empfängt.
