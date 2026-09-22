# Behemoth-Speicher

Behemoth ist die native Speichergrundlage von Converged. Es stellt mehrere
Datenmodelle über eine kompakte Laufzeitumgebung bereit und bewahrt dabei für
jeden Microservice eine separate physische Speichergrenze.

## Speicher für modulare Services

Jeder Domänenservice besitzt seine Daten. Er teilt weder Tabellen noch Indizes
mit unabhängigen Services und muss keinen separaten Datenbank-Stack betreiben.
Behemoth stellt die isolierten Roots aus einem gemeinsamen nativen Prozess
bereit und leitet jede Anfrage an den richtigen Speicher weiter.

```text
orders service  -> orders volume  -> SQL and files
calls service   -> calls volume   -> key-value and audio fragments
search service  -> search volume  -> vector index
```

Die Trennung ist physisch und keine reine Namenskonvention. Wenn ein Service-Root
nicht eingebunden und deklariert ist, verweigert Behemoth die Erstellung seines
Speichers. Ein Bereitstellungsfehler wird dadurch sofort sichtbar, anstatt Daten
in ein temporäres Container-Dateisystem zu schreiben.

## Mehrere Datenmodelle

Unterschiedliche Workloads benötigen unterschiedliche Strukturen. Behemoth
kombiniert relationale, Schlüssel-Wert-, spaltenbasierte, Vektor-, Graph- und
Dateispeicherung hinter derselben Laufzeitgrenze. Ein Service wählt den Speicher,
der zu seinen Daten passt, ohne der Plattform ein neues externes
Datenbankprodukt hinzuzufügen.

Die Engines bleiben intern spezialisiert. Die vereinheitlichte Schicht ist für
Lebenszyklus, Isolation, Transport und Metadaten zuständig, nicht dafür,
vorzutäuschen, dass sich alle Datenmodelle gleich verhalten.

## Platzierung und Skalierung

Die Speicherplatzierung ist unabhängig vom Anwendungscode. Eine einzelne
Edge-Installation kann einen einzigen Behemoth-Prozess verwenden. Größere
Bereitstellungen können Bereiche auf mehrere Instanzen aufteilen, während ein
Cloud-Profil jedem Mandanten eine eigene Speicherinstanz zuweisen kann.

Jeder Microservice behält in jedem Profil sein eigenes Volume. Das Verschieben
eines Bereichs oder eines Services auf eine andere Behemoth-Instanz ändert die
Bereitstellungskonfiguration, während Aufrufer weiterhin dieselbe logische
Speicheridentität verwenden.

## Fehler- und Wiederherstellungsgrenzen

Kleine, serviceeigene Speicher reduzieren die Auswirkungen von Beschädigungen,
Migrationen und Sicherungsvorgängen. Ein Problem in einem Speicher erfordert
keine Wiederherstellung einer gemeinsam genutzten Datenbank für die gesamte
Plattform. Dumps und Wiederherstellungen können für die betroffene Servicegrenze
behandelt werden, während unabhängige Services weiterarbeiten.

## Rolle im System

Speicheranfragen erreichen Behemoth über Fujin wie Anfragen an jeden anderen
Laufzeit-Peer. Ptah stellt das Volume-Layout und die Einbindungskonfiguration
bereit. Behemoth führt Speicheroperationen aus, koordiniert jedoch keine
Geschäftsabläufe, wählt keine Mandanten aus und definiert nicht, welche Services
eine Lösung enthält.
