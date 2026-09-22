# Ptah-Steuerungsebene

Ptah wandelt eine Beschreibung einer Converged-Plattform in laufende Kubernetes-Ressourcen um.
Es ist die Steuerungsebene des Systems: Sie entscheidet, was für eine Plattform vorhanden sein sollte,
welche Lösungen aktiv sind und wie Mandanten-Workloads und Speicher platziert werden.

## Gewünschtes Plattformmodell

Das Bereitstellungsmodell hat drei Ebenen:

| Ressource | Bedeutung |
| --- | --- |
| Plattform | Gemeinsame Laufzeitumgebung, Routing, Speicherprofil, Anwendungen und Modulzuordnung. |
| Lösung | Eine Gruppe von Geschäftmodulen, Workflows und Prozessoren, die einer Plattform hinzugefügt werden. |
| Mandant | Eine isolierte Site mit eigenem Gültigkeitsbereich, eigenen Routen und, falls erforderlich, eigenem Speicher-Shard. |

Ptah überwacht diese Ressourcen und erstellt den vollständigen gewünschten Satz an
Deployments, Services, Volumes, Konfigurationen und Routen. Kubernetes bringt den
Cluster anschließend mit dieser Beschreibung in Übereinstimmung.

```text
Plattform + Lösung + Mandant
              |
              v
             Ptah
              |
              v
Kubernetes-Workloads, Speicher und Routen
```

## Richtlinie und Mechanismus

Ptah trennt Clustermechanik von Produktrichtlinien. Der native Controller
überwacht Kubernetes, wendet Ressourcen an, erfasst den Status und entfernt
veraltete Objekte. Eine reine Richtlinienebene wandelt beobachtete Plattformdaten
in ein gewünschtes Ergebnis um, ohne Netzwerkaufrufe durchzuführen oder den
Cluster selbst zu verändern.

Dieselbe Richtlinie kann daher vor der Bereitstellung ausgewertet werden. Dadurch
werden Platzierungs- und Lebenszyklusentscheidungen prüfbar, ohne sie in einem
zweiten Konfigurationsgenerator nachbilden zu müssen.

## Bereitstellungsprofile

Profile ändern die Speicherplatzierung, ohne die Anwendungs-Images zu ändern:

- `mono` führt eine Speicherinstanz für eine kompakte Plattform aus;
- `multi` teilt Gültigkeitsbereiche auf Speicher-Shards auf;
- `cloud` stellt jedem Mandanten eine isolierte Speicherinstanz und eine eigene Routing-Grenze bereit.

Die Regel für den Volume-Besitz bleibt in jedem Profil gleich: Jeder Microservice
hat sein eigenes Speicher-Volume. Ptah entscheidet, welche Behemoth-Instanz diese
Volumes einbindet, und veröffentlicht die Zuordnung von Gültigkeitsbereich zu
Speicher, die von zustandslosen Workloads verwendet wird.

## Module und Rollout

Lösungen benennen Module, statt ihre Bytes einzubetten. Ptah verteilt eine
content-adressierte Modulzuordnung und stellt unveränderliche Modulinhalte über
einen gemeinsamen Cache bereit. Verbraucher erhalten den exakten Digest, den sie
laden sollen.

Wenn sich der ausgewählte Digest ändert, ändert sich auch die Workload-Beschreibung,
und Kubernetes führt den Rollout durch. Ein laufender Pod zeichnet daher den
präzisen Modulinhalt auf, mit dem er gestartet wurde, und ein Rollback bedeutet,
erneut den vorherigen Digest auszuwählen.

## Sichere Abstimmung

Ptah wendet einen vollständigen gewünschten Satz an und entfernt Ressourcen, die
nicht mehr zu ihm gehören. Ressourcen mit Daten werden beibehalten, sofern ihre
Löschung nicht ausdrücklich angefordert wird. Unvollständige Eingaben oder ein
Fehler in der Richtlinie unterdrücken das Entfernen, sodass ein vorübergehendes
Abhängigkeitsproblem nicht als Aufforderung interpretiert wird, die Plattform zu
entfernen.

## Platz im System

Ptah ist kein Peer im Fujin-Nachrichtenbus und verarbeitet keinen
Geschäftsverkehr. Es erstellt und konfiguriert die Peers, den Speicher und die
Routen, aus denen die Laufzeitumgebung besteht. Sobald sie ausgeführt werden,
erledigen Fujin, Behemoth, Centimanus und Resonus ihre Arbeit unabhängig von der
Steuerungsebene.
