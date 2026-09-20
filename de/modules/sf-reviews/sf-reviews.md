# sf-reviews

## Zweck

Das Bewertungssystem als ein Arbeitsbereich: was Kunden über die Arbeit gesagt haben,
welche davon auf der Website zu sehen sind, was der Shop darauf geantwortet hat und
wie weit die Anfrage kommt — wie viele Links verschickt wurden, wie viele geöffnet
wurden und wie viele zurückkamen.

## Aufbau

Die Oberfläche definiert zwei `setOf`-Ansichten — Bewertungen und die Einladungen,
die danach gefragt haben — welche der Arbeitsbereich in die dauerhaften Schaltflächen
dieses Tabs verwandelt, sowie eine `objectOf`-Ansicht für eine Bewertung. Moderations-
warteschlange, veröffentlichte Wand und abgelehnte Sammlung sind Voreinstellungen
für die Bewertungstabelle und keine drei Typen: Es handelt sich um eine Liste, die auf
drei Arten gelesen wird. Das Öffnen einer Bewertung öffnet daher einen Untertab
*innerhalb* der Bewertungen, statt davon wegzunavigieren. Wenn nichts ausgewählt ist,
zeigt die Oberfläche ihren eigenen Bildschirm, `ReviewsDashboardView`.

## Verantwortungsgrenze

Liest aus `rp-reviews` und schreibt dorthin. Liest `rp-orders` für den Vorgang, um den
es bei einer Bewertung geht — direkt aus dem Browser, denn genau dort gehört eine
Zusammenstellung aus zwei Aufrufen hin; kein Repository kennt das andere.

Das Versenden erfolgt nicht von hier aus. `wf-order-review-request` erstellt und
versendet den persönlichen Link, und `wf-order-review-followup` verfolgt ihn nach,
denn einen Auftrag und eine Bewertung in einem Prozess zu erreichen, ist genau der
Zweck eines Workflows. „Um eine Bewertung bitten“ auf dieser Oberfläche erstellt den
Link und überlässt das Versenden diesem Ablauf, sodass es weiterhin einen einzigen
Absender und eine einzige Spur gibt.

## Bewertungssteuerung

Das öffentliche Formular zeigt allen die externen Plattformen. Der Schwellenwert des
Shops verschiebt den *Schwerpunkt* — einem zufriedenen Kunden werden zuerst die
Plattformen angeboten, einem unzufriedenen zuerst ein Gespräch mit dem Shop — und
niemals die Verfügbarkeit der Links, denn den Weg zu einer öffentlichen Bewertung nur
zufriedenen Kunden zu zeigen, ist etwas, das Google und mehrere andere Plattformen
verbieten. Die Karte zeigt, in welche Richtung sich das Formular bei einer bestimmten
Bewertung geneigt hat; sie schränkt nichts ein.

## Direkte Modulabhängigkeiten

- `g-reviews`
- `g-orders`

## Zugehörigkeit zur Lösung

- `production`

## Quelle

`modules/surfaces/business/sf-reviews`
