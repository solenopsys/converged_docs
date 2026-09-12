# NRPC-Laufzeit für Verträge

NRPC ist Convergeds typisierte Schicht für Remote-Aufrufe. Sie wandelt einen
getypten TypeScript-Servicevertrag in passende Clients und Servicemetadaten um,
sodass ein Browser, Microservice, Workflow oder eine native Laufzeit dieselbe
Funktion aufrufen kann, ohne separate zeichenfolgenbasierte API-Definitionen
pflegen zu müssen.

## Warum es existiert

Die Plattform besteht aus unabhängig bereitgestellten Modulen. Würde ein Modul
direkt über eine Adresse aufgerufen, wären seine Aufrufer davon abhängig, wo es
läuft und welchen Transport es verwendet. NRPC trennt diese Aspekte: Ein
Vertrag benennt den Service und seine Methoden, während die Laufzeit einen
Aufruf an den Prozess zustellt, der derzeit das angeforderte Ziel besitzt.

So bleibt die Vereinbarung zwischen Aufrufern und Implementierungen an einer
Stelle. Die Parameter, der Rückgabetyp, das Streaming-Verhalten und die
Zugriffsebene einer Methode sind der Codegenerierung bekannt und stehen jedem
unterstützten Client zur Verfügung.

## Vom Vertrag zum Aufruf

Verträge sind TypeScript-Schnittstellen unter `modules/types/<domain>`. Das
Ausführen von `bun run gen` in `core/tools/nrpc` analysiert diese Schnittstellen
und erstellt ein Paket `modules/generated/g-<service>`. Das Paket enthält die
Vertragsmetadaten, eine Serverschnittstelle und typsichere Client-Fabriken für
jede Laufzeit.

```text
TypeScript interface
        |
        v
NRPC generator -> g-<service> package
        |                    |
        |                    +-> browser client
        |                    +-> cluster client
        |                    +-> workflow RT client
        v
service implementation -> messaging backend
```

Ein Service registriert seine Implementierung mit `createMessagingBackend`. NRPC
verwendet die generierten Metadaten, um die angeforderte Methode zu finden,
validiert die Aufrufstruktur an der Client-Grenze, stellt typisierte Werte
wieder her und ruft die passende Implementierungsmethode auf. Eine Methode, die
`AsyncIterable` zurückgibt, wird als Stream zugestellt; gewöhnliche Methoden
erzeugen eine einzelne Antwort.

## Zustellungswege

NRPC bewahrt denselben Vertrag über mehrere Ausführungsumgebungen hinweg:

- Browser-Clients verwenden einen gemeinsam genutzten WebSocket-Kanal, um
  Anfragen an Fujin zu senden.
- Service- und native Clients verwenden den Cluster-Transport über Fujin und
  adressieren dabei ein logisches Prozessziel statt einer Hostadresse.
- Workflow-Clients verwenden den RT-Einstiegspunkt, der über den QuickJS/Zig-
  Host-Transport aufruft und für eine einzelne Workflow-Auswertung synchron
  bleibt.

Fujin leitet eine Anfrage an die Zielverbindung weiter. Der empfangende Prozess
wählt den NRPC-Service und die Methode anhand der Anfragemetadaten aus; Fujin
muss die Domänendienste der Plattform nicht verstehen. `createHttpBackend` ist
verfügbar, wenn ein HTTP-Edge erforderlich ist, und kann dieselbe
Serviceimplementierung in der Messaging-Laufzeit registrieren, sodass
HTTP-Aufrufe und interne Aufrufe aufeinander abgestimmt bleiben.

## Kontext und Zugriff

Aufrufe enthalten in ihrem Envelope Korrelationsdaten, Deadlines und einen
vertrauenswürdigen Workspace- oder Scope-Kontext. Der empfangende Service wird
mit diesem Kontext ausgeführt, sodass Speicher- und Autorisierungscode dieselbe
Mandantengrenze verwenden kann, die am Edge festgelegt wurde. Services dürfen
die Workspace-Identität nicht aus einer Geschäftsnutzlast ableiten.

Der `@Access`-Decorator deklariert eine Klasse oder Methode als `public`, `user`
oder `internal`. NRPC ermittelt die spezifischste deklarierte Ebene und wendet
die konfigurierten Berechtigungsregeln an, bevor die Implementierung aufgerufen
wird. Dadurch wird die Zugriffsrichtlinie zu einem Bestandteil der
Servicegrenze statt zu einer uneinheitlichen Konvention der Clients.

## Verantwortungsgrenze

NRPC ist für Vertragsmetadaten, generierte typisierte Clients,
Werteserialisierung, Aufrufverteilung und die von diesen Aufrufen verwendeten
Transportadapter zuständig. NRPC ist nicht für Geschäftsregeln,
Service-Erkennung, Bereitstellungsplatzierung, Domänenpersistenz oder das
Routing über den Nachrichtenbus zuständig. Diese Verantwortlichkeiten verbleiben
beim Service, bei der Bereitstellungssteuerung, bei der Speicherschicht
beziehungsweise bei Fujin.
