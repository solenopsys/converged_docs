# lm-kubernetes

## Zweck

Zustandslose Kubernetes-Operator-Brücke: wendet Automatisierungsabsichten der Plattform auf Clusterressourcen (Deployments, Jobs) über einen dedizierten Client an. Kein persistenter Zustand; Secrets werden über lm-secrets aufgelöst.

## Verantwortungsbereich

Verantwortlich für Cluster-API-Übersetzung und Apply-/Status-Lesevorgänge; nicht verantwortlich für Workflow-Orchestrierung, Zeitplanung oder Secret-Speicherung.

## Direkte Modulabhängigkeiten

- Keine

## Lösungszugehörigkeit

- Nicht in einer vordefinierten Lösung enthalten

## Quelle

`modules/lambdas/automation/lm-kubernetes`