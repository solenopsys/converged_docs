## Bereitstellung

Converged unterstützt mehrere Installationsszenarien: von einer kleinen Werkstatt bis zum Production-Deployment in der Infrastruktur eines Unternehmens. Die Basisplattform läuft auf **k3s**, einer leichtgewichtigen Kubernetes-Distribution für Edge-Geräte, lokale Server und Cloud-Umgebungen.

Es gibt zwei Hauptprofile:

- **Mono** — UI, Runtime, Microservices, Storage und Cache sind kompakt gepackt. Dieser Modus ist für Entwicklung, Prototypen, Demos und kleine Installationen gedacht, bei denen einfacher Start wichtiger ist.
- **Multi** — UI, Runtime-Gruppen, domänenbezogene Microservice-Gruppen, Storage und Cache sind getrennt. Das ist das Standard-Production-Profil, wenn Isolation, Skalierung und präzisere Lastkontrolle nötig sind.

Beide Profile verwenden denselben Code. Nur Container-Topologie und Konfiguration unterscheiden sich. Ein Unternehmen kann mit einer kompakten Installation beginnen und dasselbe System später in ernsthaftere Infrastruktur verschieben, ohne das Produkt neu zu schreiben.

Bei Self-hosted-Szenarien kontrolliert der Kunde Installation, Netzwerk, Backups, Updates und den physischen Speicherort der Daten. Das passt zu Unternehmen mit internen Sicherheitsanforderungen oder dem Wunsch, die Produktion vollständig auf der eigenen Seite zu halten. Die Cloud-Lieferung nimmt operative Aufgaben ab: Die Plattform wird vom Serviceteam bereitgestellt und aktualisiert, während der Kunde eine fertige Arbeitsumgebung erhält.

Eine hybride Variante ist ebenfalls möglich: sensible Daten und Ausrüstung bleiben lokal, während die Cloud für Updates, externen Zugriff, Koordination verteilter Teams oder einzelne KI-Funktionen genutzt wird. Der wichtige Grundsatz ist, den Kunden nicht auf ein einziges Liefermodell festzulegen.
