# Modulkatalog

Dieser Index wird aus dem Converged-Modulregister generiert. Jeder Eintrag verweist auf die von diesem Modul verwaltete Dokumentation; Abhängigkeiten werden aus seinem Workspace-Paketmanifest übernommen, und die Lösungszugehörigkeit stammt aus `modules/solutions`.

## Zugriff und Sicherheit

### [lm-secrets](/en/docs/modules/lm-secrets)

Stellt den Servicevertrag zum Speichern, Abrufen und Löschen benannter Geheimniswerte bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-access](/en/docs/modules/rp-access)

rp-access ist ein Repository in der Domäne sequrity. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth ist ein Repository in der Domäne sequrity. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `security`

### [rp-environment](/en/docs/modules/rp-environment)

Speichert und ruft Umgebungskonfigurationen ab, die Plattformbenutzern zugeordnet sind.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity ist ein Repository in der Domäne sequrity. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth ist ein Repository in der Domäne sequrity. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth ist eine Oberfläche in der Domäne sequrity. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Stellt die Administrationsoberfläche zum Erstellen, Anzeigen, Aktualisieren und Löschen benannter Geheimnisdatensätze bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

## KI und Agenten

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant ist ein Repository in der KI-Domäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Stellt die Speicherung und den Abruf benannter KI-Kontexte einschließlich ihrer Sprachvarianten bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants ist eine Oberfläche in der KI-Domäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: `sf-requests`
- Lösungen: `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Stellt den KI-Arbeitsbereich zum Auflisten, Bearbeiten und Speichern benannter Kontexte in mehreren Sprachen bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

## Analysen und Telemetrie

### [rp-counters](/en/docs/modules/rp-counters)

Stellt den Servicevertrag zum Erfassen und Abfragen analytischer Zähler bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Stellt Dashboarddaten und analytische Ansichten für Plattformmetriken bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs ist ein Repository in der Analytics-Domäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry ist ein Repository in der Analytics-Domäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage ist ein Repository in der Analytics-Domäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards ist eine Oberfläche in der Analytics-Domäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs ist eine Oberfläche in der Analytics-Domäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry ist eine Oberfläche in der Analytics-Domäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage ist eine Oberfläche in der Analytics-Domäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `analitycs`

## Automatisierung und Orchestrierung

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Integriert Plattformautomatisierung über einen dedizierten Client und Servicevertrag mit Kubernetes-Ressourcen.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag ist ein Repository in der Automatisierungsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller ist ein Repository in der Automatisierungsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks ist ein Repository in der Automatisierungsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation ist die Oberfläche in der Automatisierungsdomäne für Workflows, Zeitpläne, Webhook-Endpunkte und deren Ausführungshistorie.

- Direkte Abhängigkeiten: keine
- Lösungen: `automation`

## Geschäftsdomäne

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing ist ein Repository in der Geschäftsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment ist ein Repository in der Geschäftsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-events](/en/docs/modules/rp-events)

Stellt die Erstellung, Speicherung und den Abruf von Geschäftsereignissen bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-finance](/en/docs/modules/rp-finance)

Stellt Finanzvorgänge für Transaktionen, Periodenzusammenfassungen, Cashflow, Forderungen und Verbindlichkeiten bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-orders](/en/docs/modules/rp-orders)

Stellt den Servicevertrag zum Erstellen, Aktualisieren, Auflisten und Nachverfolgen von Geschäftsaufträgen bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests ist ein Repository in der Geschäftsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews ist ein Repository in der Geschäftsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales ist ein Repository in der Geschäftsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff ist ein Repository in der Geschäftsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-orders](/en/docs/modules/sf-orders)

Stellt die Vertriebsoberfläche für Auftrags- und Anfragelisten, Auftragsdetails, Statusfilter und operative Dashboards bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests ist eine Oberfläche in der Geschäftsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

## Kommunikation

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls ist ein Repository in der Kommunikationsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats ist ein Repository in der Kommunikationsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-community](/en/docs/modules/rp-community)

rp-community ist ein Repository in der Kommunikationsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify ist ein Repository in der Kommunikationsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-resonus](/en/docs/modules/rp-resonus)

Stellt Kommunikationskonfigurationen für verwaltete Telefonnummern und LLM-Gateway-Einstellungen bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads ist ein Repository in der Kommunikationsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls ist eine Oberfläche in der Kommunikationsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats ist eine Oberfläche in der Kommunikationsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-community](/en/docs/modules/sf-community)

sf-community ist eine Oberfläche in der Kommunikationsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads ist eine Oberfläche in der Kommunikationsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `ai`

## Inhalte und Dokumente

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier ist ein Repository in der Inhaltsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery ist ein Repository in der Inhaltsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown ist ein Repository in der Inhaltsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Stellt Speicheroperationen für Skriptdateien bereit, einschließlich Lesen, Speichern, Hashing und Löschen.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-static](/en/docs/modules/rp-static)

Stellt den Servicevertrag für statische Inhalte und SSR-Cache-Metadaten bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct ist ein Repository in der Inhaltsdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Stellt die Klassifikatorschnittstelle zum Navigieren durch Entitäten, Zuordnungen und Baumstrukturen bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs ist eine Oberfläche in der Inhaltsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery ist eine Oberfläche in der Inhaltsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing ist eine Oberfläche in der Inhaltsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown ist eine Oberfläche in der Inhaltsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-static](/en/docs/modules/sf-static)

Stellt die Operationsschnittstelle zum Prüfen und Löschen statischer SSR-Cache-Einträge bereit.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct ist eine Oberfläche in der Inhaltsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

## Dateien und Speicher

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors ist eine Lambda-Funktion in der Datendomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps ist ein Repository in der Datendomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [rp-files](/en/docs/modules/rp-files)

rp-files ist ein Repository in der Datendomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store ist ein Repository in der Datendomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps ist eine Oberfläche in der Datendomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [sf-files](/en/docs/modules/sf-files)

sf-files ist eine Oberfläche in der Datendomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

## Anbieter für Nachrichtenübermittlung

### [lm-push](/en/docs/modules/lm-push)

lm-push ist eine Lambda-Funktion in der Anbieterdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses ist eine Lambda-Funktion in der Anbieterdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms ist eine Lambda-Funktion in der Anbieterdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp ist eine Lambda-Funktion in der Anbieterdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

## Modellkonvertierung

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor ist eine Lambda-Funktion in der Konvertierungsdomäne. Ihr detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

## Workflows

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Fasst unverarbeitete Chat- und Anrufdialoge mit einem LLM zusammen und speichert anschließend Titel, Beschreibungen und eine Rauschklassifizierung.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analysiert eine gespeicherte Datei, die kein Archiv ist, und erzeugt, sofern unterstützt, Modellvorschauen sowie CNC- oder 3D-Druck-Schätzungen.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Entpackt ein hochgeladenes Archiv in eine Sammlung gespeicherter Dateien für die anschließende Analyse.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze ist ein Workflow in der Plattformdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Verarbeitet hochgeladene Dateien stapelweise: Es entpackt Archive, identifiziert Modelldateien und erstellt daraus eine Fertigungsanfrage.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze ist ein Workflow in der Plattformdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: `requests`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import ist ein Workflow in der Plattformdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach ist ein Workflow in der Plattformdomäne. Sein detaillierter Zweck wird zusammen mit dem Modulquelltext gepflegt.

- Direkte Abhängigkeiten: keine
- Lösungen: keine

## Lösungsabhängigkeiten

- `ai`: `security`
- `analitycs`: `security`
- `content`: `security`
- `requests`: keine Lösungsabhängigkeiten
- `security`: keine Lösungsabhängigkeiten
