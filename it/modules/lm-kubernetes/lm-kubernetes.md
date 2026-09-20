# lm-kubernetes

## Scopo

Bridge di operatori Kubernetes stateless: applica gli intenti di automazione della piattaforma alle risorse del cluster (deployment, job) tramite un client dedicato. Nessuno stato persistente; i segreti vengono risolti tramite lm-secrets.

## Confine di responsabilità

Responsabile della traduzione dell'API del cluster e delle letture di apply/stato; non responsabile dell'orchestrazione dei flussi di lavoro, della pianificazione o dell'archiviazione dei segreti.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Fonte

`modules/lambdas/automation/lm-kubernetes`