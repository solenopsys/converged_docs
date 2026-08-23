## Technologien

Die Serverseite von Converged basiert auf **Bun** und **Elysia**. Bun startet JavaScript und TypeScript schnell, nutzt Speicher effizient und passt gut zu kompakten Edge-Deployments. Elysia dient als HTTP-Schicht für Backend-Plugins und Microservices.

Serviceverträge werden typisiert beschrieben. NRPC verbindet TypeScript-Interfaces mit Implementierungen und generiert Client-Pakete, damit Frontend, Runtime und Backend mit denselben Verträgen arbeiten statt mit verstreuten String-APIs.

Für Daten werden mehrere leichte Stores je nach Aufgabe genutzt: SQL, Key-Value, Dateien, Spaltendaten, Vektorindizes und Graphbeziehungen. Die native Behemoth-Schicht und Zig-Adapter decken Fälle ab, in denen geringer Overhead, Zugriff auf Ausrüstung, Unix-Sockets oder FFI wichtig sind.

Das Frontend ist eine React-Plattform mit Micro-Frontends. Die gemeinsame Shell lädt getrennte UI-Module, und Produktszenarien können unabhängig wachsen. Das ist wichtig für eine Plattform mit vielen Lösungen: Die Oberfläche darf nicht zu einem schweren Monolithen werden.

Orchestrierung und Lieferung basieren auf k3s, Helm und Konfigurationsprofilen. Derselbe Komponentensatz kann als kompaktes Mono-Profil oder in getrennten Gruppen für Production zusammengesetzt werden.
