## Sicherheit

Converged geht davon aus, dass Produktionsdaten nicht in einen gemeinsamen Haufen geworfen werden dürfen. Aufträge, Kundendateien, technische Parameter, Zahlungen, Nachrichten und Maschinentelemetrie müssen nach Workspaces und Verantwortungsbereichen getrennt werden.

Architektonisch wird das durch Datenisolation unterstützt. Microservices besitzen ihre Stores, und Workspaces können getrennte Verzeichnisse, Schlüssel, Dateien und Zugriffsgrenzen haben. Das vereinfacht Export, Self-hosted-Migration, Backups und Audit.

Zugriffsrechte gelten nicht nur für Menschen, sondern auch für KI-Agenten. Wenn ein Modell eine Aktion startet, Daten liest oder einen Workflow aufruft, muss das innerhalb seines Berechtigungsprofils passieren. Aktionen werden protokolliert, sodass nachvollziehbar ist, wer oder welcher Agent einen Schritt ausgelöst hat, welche Daten betroffen waren und wie das Szenario endete.

Self-hosted- und Private-Deployments geben dem Kunden volle Kontrolle über Infrastruktur: Netzwerk, Secrets, API-Keys, Backups und physischen Datenstandort. Der Cloud-Modus ist operativ einfacher, darf aber nicht zum Vendor-Lock-in werden: Daten müssen portabel bleiben, und Szenarien müssen in einer anderen Installation reproduzierbar sein.
