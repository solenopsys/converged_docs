## Technologien

Converged basiert auf einer kompakten Systemgrundlage, die für hohe Leistung und eine effiziente Ressourcennutzung in Kubernetes-Umgebungen jeder Größenordnung ausgelegt ist — von einem einzelnen Mikrocomputer bis hin zu einem verteilten Cluster.

Im Zentrum der Infrastruktur steht **Zig** — eine moderne, extrem schnelle und einfache Systemprogrammiersprache. Zig wird für Infrastrukturelemente eingesetzt, bei denen Leistung, Ressourceneffizienz, Hardwarezugriff und Kontrolle auf niedriger Ebene wichtig sind.

**Cruller** stellt die Ausführungsumgebung für TypeScript und JavaScript bereit. Es handelt sich um eine spezialisierte Laufzeitumgebung, die von Bun abgeleitet und an die Architektur und Anforderungen von Converged angepasst wurde.

**Behemoth** stellt eine einheitliche Datenschicht bereit, die verschiedene Speichermodelle unterstützt, darunter SQL, Schlüssel-Wert-Daten, Dateien, Vektoren und andere spezialisierte Datenstrukturen. Der Speicher kann entsprechend den Anforderungen jeder Bereitstellung verteilt und skaliert werden.

**Fujin** stellt die Kommunikationsschicht bereit und verbindet Services, Schnittstellen, Ereignisse und Anlagen über eine einheitliche Echtzeit-Kommunikationsstruktur. **Centimanus** führt Workflows aus und verwaltet ihre Abhängigkeiten, parallele Ausführung, Ereignisse, Wiederholungen und lang laufenden Vorgänge.

Converged läuft immer in **Kubernetes**. Die Basisumgebung ist **k3s**, eine leichtgewichtige Kubernetes-Distribution, die dasselbe Bereitstellungsmodell auch auf kleinen Edge-Geräten wie dem Raspberry Pi praktikabel macht. Auf einer einzelnen Maschine läuft Converged als kompakter Single-Node-Cluster; bei Bedarf kann derselbe Cluster auf mehrere Maschinen verteilt werden.

Dadurch entsteht eine einheitliche technologische Grundlage für die gesamte Infrastruktur — von einem kleinen Edge-Gerät bis hin zu einem verteilten Cloud-Cluster.
