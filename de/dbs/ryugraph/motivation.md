## Warum Graphspeicher für KI-Agenten geeignet ist

Der Wert einer Graphdatenbank in einem KI-zentrierten System beschränkt sich nicht auf das schnellere Durchlaufen von Beziehungen. Ihr größerer Vorteil besteht darin, dass ein Graph Informationen in einer Form darstellt, die für einen LLM-Agenten von Natur aus leicht zu verstehen und zu erkunden ist.

Eine relationale Datenbank basiert auf Tabellen, Spalten, Fremdschlüsseln und vordefinierten Joins. Das funktioniert äußerst gut, wenn die Struktur der Abfrage im Voraus bekannt ist. Ein Agent arbeitet jedoch häufig anders. Er kann mit einer unvollständigen Anfrage beginnen, ein relevantes Objekt finden, dessen Umgebung untersuchen, einer nützlichen Beziehung folgen und fortfahren, bis genügend Kontext gesammelt wurde.

Ein Graph unterstützt diesen Arbeitsstil direkt.

Beispielsweise kann ein Produktionsunternehmen Objekte wie ein Unternehmen, einen Mitarbeiter, einen E-Mail-Thread, einen Anhang, ein Teil, ein Material, eine RFQ, ein Angebot, einen Auftrag und eine Maschine umfassen. Diese Objekte können durch aussagekräftige Beziehungen verbunden werden:

```text
John Smith → WORKS_AT → Acme CNC
Message → SENT_BY → John Smith
Message → HAS_FILE → housing_revC.step
housing_revC.step → REVISION_OF → Housing
RFQ → REQUESTS → Housing
Quote → ANSWERS → RFQ
Order → BASED_ON → Quote
```

Für ein LLM ist diese Struktur bereits informativ. `Acme CNC`, `Housing`, `REVISION_OF`, `SENT_BY` und `BASED_ON` sind keine undurchsichtigen Datenbankschlüssel. Ihre Namen tragen semantische Bedeutung. Der Graph dient daher nicht nur als Speicher, sondern auch als kompakte Beschreibung der Geschäftsdomäne.

Dies verändert die Arbeitsweise des Agenten.

Angenommen, ein Benutzer fragt:

> Finde heraus, was der Kunde bei diesem Acme-Gehäuseauftrag wollte.

Der Agent muss nicht sofort eine große Abfrage erstellen. Er kann zunächst `Acme CNC` finden, die verbundenen Aufträge untersuchen, den relevanten Gehäuseauftrag identifizieren, seine Threads untersuchen und erst dann die wenigen wichtigen Nachrichten abrufen.

Eine typische Erkundung kann so aussehen:

```text
Acme CNC
  ↓
Orders
  ↓
Housing Order
  ↓
Threads
  ↓
Messages
  ↓
Attachments
```

Bei jedem Schritt erhält der Agent nur eine kleine lokale Ansicht des Graphen. Zum Beispiel:

```json
{
  "id": "order_551",
  "type": "Order",
  "name": "Housing batch",
  "relations": {
    "CUSTOMER": 1,
    "THREAD": 3,
    "FILE": 11,
    "PART": 2,
    "QUOTE": 2
  }
}
```

Dies reicht aus, damit das Modell versteht, welche Art von Objekt es betrachtet und in welche Richtung die nächste Erkundung sinnvoll ist.

Die wichtige Konsequenz besteht darin, dass der Agent nicht das gesamte Datenbankschema in seinem Kontext benötigt. Er muss sich nicht Dutzende von Tabellen, Fremdschlüsseln, Verknüpfungstabellen oder rekursiven SQL-Ausdrücken merken. Er benötigt lediglich ein aktuelles Objekt und eine kleine Beschreibung seiner lokalen Beziehungen.

Dadurch wird die rekursive Erkundung sowohl kostengünstig als auch robust.

Große Inhalte müssen ebenfalls nicht im Graphen gespeichert werden. E-Mail-Texte, PDF-Dateien, CAD-Modelle, Bilder und andere umfangreiche Objekte können in KVS oder einem Objektspeicher verbleiben. Der Graph enthält nur kompakte Metadaten, Objektkennungen, Speicherschlüssel und Beziehungen.

Die Architektur trennt daher Struktur und Inhalt:

```text
Graph
    → objects, relationships, metadata, storage keys

KVS / Object Storage
    → email bodies, PDF, STEP, STL, DXF, images

LLM Agent
    → explores the graph first
    → retrieves heavy content only when necessary
```

Dies ist besonders wichtig bei der Arbeit mit vielen Jahren Unternehmensgeschichte. Hunderte Gigabyte an E-Mails und Anhängen können durch einen wesentlich kleineren Graphen dargestellt werden, der Unternehmen, Personen, Threads, Dateien, Aufträge, Teile und ihre Beziehungen enthält.

Der Agent kann zehn oder zwanzig kleine Graphoperationen ausführen und dabei nur wenige Kilobyte strukturierten Kontext verbrauchen. Am Ende dieser Erkundung weiß er möglicherweise bereits, welches Unternehmen beteiligt ist, welche Aufträge relevant sind, welche Personen teilgenommen haben, welche Dateien zum Fall gehören und wo sich die wichtigen Gespräche befinden. Erst dann lädt er die tatsächlichen Nachrichtentexte oder Dateien, die zur Beantwortung der Frage erforderlich sind.

Der Graph ist außerdem von Natur aus erweiterbar. Ein System kann zunächst nur `Company`, `Person`, `Message`, `File` und `Order` enthalten. Später kann es um `Part`, `Revision`, `Material`, `Machine`, `Job`, `Supplier` oder `Contract` sowie um neue Beziehungen wie `REVISION_OF`, `USES_MATERIAL`, `MANUFACTURED_ON` oder `SUPPLIED_BY` ergänzt werden.

Die Schnittstelle des Agenten muss sich dabei nicht grundlegend ändern. Er kann weiterhin denselben kleinen Satz von Operationen verwenden:

```text
find
inspect
follow
expand
search
fetch
```

Dies ist ein wichtiger Unterschied zu einem System, in dem jede neue Geschäftsbeziehung letztlich eine weitere Reihe von SQL-Joins, API-Methoden und abfragespezifischer Logik erzeugt.

Ein praktisches Beispiel veranschaulicht den Vorteil besonders gut.

Der Benutzer fragt:

> Finde den Vertrag für das Unternehmen, für das wir im vergangenen Jahr Nylonteile gedruckt haben.

Der Benutzer erinnert sich weder an den Unternehmensnamen noch an die Auftragsnummer, den E-Mail-Betreff oder den Dateinamen.

Der Agent kann mit dem Konzept beginnen, das er kennt:

```text
Nylon
  ↓
Jobs
  ↓
Orders
  ↓
Companies
  ↓
Documents
  ↓
Contract
```

Eine andere Anfrage könnte lauten:

> Finde die CAD-Datei, die der Kunde geschickt hat, bevor wir das Angebot neu berechnet haben.

Auch hier kann der Agent Beziehungen und zeitliche Abfolgen durchlaufen, bis er den relevanten Anhang findet, ohne dass der Benutzer wissen muss, wie die zugrunde liegenden Daten organisiert sind.

Dies ist der zentrale architektonische Grund für die Verwendung eines Graphen mit einem LLM-Agenten.

Der Graph ist nicht lediglich ein schnellerer Ersatz für SQL-Joins. Er ist eine kompakte semantische Darstellung der Domäne, die das Modell lesen, verstehen und schrittweise erkunden kann.

In dieser Architektur wird der Graph zum strukturellen Gedächtnis, der Objektspeicher enthält die umfangreichen Inhalte, und das LLM wird zum semantischen Erkunder, der sich durch die Struktur bewegt.

Das Kernprinzip ist einfach:

> **Graph ist ein agentenorientiertes Datenmodell.**

Er bietet dem Agenten eine Datenform, die kompakt, aussagekräftig, erweiterbar und von Natur aus für die rekursive Erkundung geeignet ist.
