# Fujin-Nachrichtenbus

Fujin ist das Kommunikationszentrum der Converged-Laufzeitumgebung. Es bietet
Browsern, Domänendiensten, Speicher-, Workflow-, Mediendiensten und Prozessoren
eine gemeinsame Möglichkeit zum Austauschen von Nachrichten.

## Warum es Fujin gibt

Eine modulare Plattform benötigt Komponenten, die sich unabhängig voneinander
bewegen können. Direkte HTTP-Verbindungen würden jeden Dienst mit den Adressen,
Replikaten und der Bereitstellungstopologie vertraut machen. Fujin ersetzt diese
Verbindungen durch logische Ziele: Ein Absender gibt an, welcher Laufzeitpartner
eine Nachricht empfangen soll, und Fujin leitet sie an die aktive Verbindung
weiter, die dieses Ziel derzeit besitzt.

```text
Absender -> logisches Ziel -> Fujin -> aktive Verbindung -> lokaler Dienst
```

Der Absender weiß nicht, wo der Empfänger ausgeführt wird. Ein Prozess kann neu
gestartet oder auf einen anderen Knoten verschoben werden und dasselbe Ziel
wieder übernehmen, ohne dass seine Aufrufer geändert werden müssen.

## Routingmodell

Fujin trifft eine Routingentscheidung: Es ordnet ein Ziel einer Verbindung zu.
Das Ziel bestimmt einen Prozess wie die UI-Laufzeitumgebung, Domänendienste oder
Centimanus. Der Dienstname innerhalb der Nachricht wird erst interpretiert,
nachdem der empfangende Prozess die Nachricht erhalten hat.

Es ist wichtig, diese Entscheidungen getrennt zu halten. Fujin bleibt ein
kleiner Nachrichten-Broker, anstatt zu einer Registrierung jedes
Geschäftsdienstes, jeder Speichereinheit oder jedes Workflows zu werden.

## Drei Datenströme

Fujin überträgt drei Arten von Datenverkehr, die sich einen Transport, aber
sonst nichts teilen. Die Dienstkommunikation bewegt Anfragen zwischen Partnern.
Die Protokollaufnahme empfängt alles, was die Collector-Komponenten der
Bereitstellung ausgeben, gruppiert es und übergibt ganze Blöcke an die
Analyse-Repositories, sodass der Speicher Stapel statt eines Stroms einzelner
Zeilen sieht. Benachrichtigungen für Benutzer sind geschäftliche Nachrichten,
die an eine Person adressiert sind: Eine Bestellung ist eingegangen, ein Auftrag
ist abgeschlossen, ein Brief wartet.

Der dritte Datenstrom benötigt einen eigenen Namen. `pushrouter` ist ein Dienst,
den Fujin hostet, anstatt Nachrichten dorthin zu routen, weil die Zustellung eine
Eigenschaft der aktiven Sitzungen ist, die Fujin bereits besitzt — kein anderer
Prozess weiß, welche Browser einer Person derzeit verbunden sind. Er antwortet
damit, wie viele Sitzungen eine Nachricht erreicht hat. Dadurch kann ein Aufrufer
entscheiden, ob zusätzlich ein dauerhafter Kanal erforderlich ist. Außerdem hält
er ein begrenztes Wiedergabefenster vor, damit ein Browser nach der
Wiederverbindung sieht, was er verpasst hat. Alles, was einen Neustart überleben
muss, gehört in ein Repository, nicht hierher.

Benachrichtigungen enthalten Übersetzungsschlüssel statt Sätzen. Der Dienst, der
eine Benachrichtigung veröffentlicht, kennt die Sprache des Lesers nicht, sodass
eine gerenderte Zeichenkette immer nur für einen von ihnen richtig sein könnte.

## Browser- und Cluster-Datenverkehr

Native Partner verbinden sich über den Cluster-Transport. Browser und mobile
Clients greifen über WebSocket zu und nehmen am selben Nachrichtenmodell teil.
So erhalten interaktive Oberflächen Live-Ereignisse, ohne ein zweites
Anwendungs-Routing-System einzuführen.

Große Nutzdaten bleiben außerhalb des Browser-Steuerkanals. Clients erhalten ein
Verfügbarkeitsereignis und rufen die Daten über den passenden Inhaltspfad ab.
Dadurch bleibt die Echtzeitsignalisierung reaktionsfähig.

## Kontext und Vertrauen

Der gemeinsame Nachrichtenumschlag enthält Korrelationsdaten, Fristen, Fehler
und den vertrauenswürdigen Mandantenbereich. Fujin transportiert diesen Kontext,
ohne ihn aus einer Geschäftsnutzlast abzuleiten oder seine Bedeutung zu ändern.
Empfangende Dienste können Autorisierungs- und Speicherregeln anhand desselben
Kontexts anwenden, der am Rand festgelegt wurde.

## Zuständigkeitsgrenze

Fujin ist für Konnektivität und Ziel-Routing zuständig. Es führt keine
Geschäftslogik aus, wählt keinen Handler innerhalb eines anderen Prozesses aus,
speichert keine Domänendaten und entscheidet nicht über die Platzierung der
Bereitstellung. Diese Zuständigkeiten verbleiben beim Laufzeitpartner, der die
Nachricht empfängt, sowie bei Ptah als Steuerungsebene.
