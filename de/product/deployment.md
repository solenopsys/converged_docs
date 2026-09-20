## Bereitstellung

Converged unterstützt mehrere Bereitstellungsszenarien — von kompakten Edge-Geräten und lokalen Servern bis hin zu Cloud-Infrastrukturen für viele unabhängige Unternehmen. Die Basisplattform läuft auf **k3s**, einer leichtgewichtigen Kubernetes-Distribution für Mikrocomputer, lokale Infrastruktur und Cloud-Cluster.

Es gibt drei wichtige Bereitstellungsprofile:

* **Mono** — UI, Dienste, Speicher und Cache laufen in einer kompakten Konfiguration auf einem einzigen Computer. Dies eignet sich gut für **Mikrocomputer wie Raspberry Pi und Orange Pi**, Edge-Geräte, kleine lokale Server, Entwicklung, Prototypen und Demos.
* **Multi** — das System ist über mehrere Computer in einem Kubernetes-Cluster verteilt. UI, Dienstgruppen, Speicher und Cache können unabhängig bereitgestellt und skaliert werden. Dieses Profil eignet sich für Produktionsumgebungen, in denen zusätzliche Kapazität, Fehlertoleranz und eine präzisere Ressourcenkontrolle erforderlich sind.
* **Cloud** — mehrere Unternehmen arbeiten innerhalb **desselben Kubernetes-Clusters** mit einer mandantenfähigen Architektur. Jeder **Mandant** verfügt über eine isolierte Umgebung mit eigenen Daten, eigener Konfiguration und eigenen Ressourcen, während die zugrunde liegende Cluster-Infrastruktur gemeinsam genutzt wird. So können viele Unternehmen effizient bedient werden, ohne für jeden Kunden einen separaten Cluster zu benötigen.

Alle drei Profile verwenden dieselbe Codebasis. Nur Bereitstellungstopologie und Konfiguration ändern sich. Ein System kann daher als kompakte Mono-Installation auf einem Mikrocomputer beginnen, bei wachsenden Anforderungen in einen Multi-Cluster wechseln oder als Cloud-Dienst für viele unabhängige Unternehmen betrieben werden.

Bei einer **Self-Hosted**-Bereitstellung kontrolliert das Unternehmen Installation, Netzwerk, Backups, Aktualisierungen und den physischen Standort seiner Daten. Dies eignet sich für Organisationen, die vollständige Kontrolle über ihre Infrastruktur benötigen.

In der **Cloud** wird die Infrastruktur zentral betrieben. Mehrere Unternehmen teilen denselben Cluster und bleiben dennoch auf Mandantenebene isoliert, einschließlich ihrer Daten, Konfiguration und zugewiesenen Ressourcen.

Auch eine **hybride** Bereitstellung ist möglich: Sensible Daten und Geräte können lokal verbleiben, während die Cloud für Aktualisierungen, externen Zugriff, verteilte Teams oder ausgewählte KI-Funktionen genutzt wird.

Das zentrale Prinzip lautet: **Converged bindet die Plattform nicht an ein einziges Bereitstellungsmodell.** Dasselbe System kann auf einem kleinen Mikrocomputer, über einen Cluster mit mehreren Computern oder als mandantenfähiger Cloud-Dienst laufen.
