## Leistung

Converged ist für Produktionsstandorte entworfen, die nicht immer über eine große Serverflotte verfügen. Deshalb vermeidet das System unnötiges Gewicht: Bun senkt den Overhead von Backend-Prozessen, Runtime bleibt stateless, und Microservices können nach Lasttyp gruppiert werden, statt Hunderte separate Container zu starten.

Leistung entsteht hier durch Architektur, nicht durch einen einzelnen Trick. Daten laufen nicht durch unnötige Schichten, Services besitzen ihre Stores, Runtime parallelisiert Workflows und Cron-Aufgaben, und native Adapter werden dort eingesetzt, wo HTTP oder eine normale JS-Schicht zu viel Overhead hinzufügen würden.

Eine kompakte Installation kann auf einem kleinen Server oder Single-Board-Computer laufen, wenn die Last zur Größe der Werkstatt passt. Beim Wachstum können Runtime, Microservices und Storage-Gruppen getrennt werden, um mehr CPU-Kerne zu nutzen, schwere Aufgaben zu isolieren und zu verhindern, dass ein Engpass das ganze System stoppt.

Die Plattform verspricht keine unendliche Leistung „out of the box“. Engpässe hängen von Ausrüstung, Dateivolumen, Auftragszahl, KI-Anbietern und Integrationen ab. Die Architektur von Converged erlaubt es, kompakt zu starten und nur die Teile zu skalieren, die wirklich heiß werden.
