# rp-billing

## Scopo

Lato monetario della piattaforma: piani, addebiti e stato di fatturazione. Legge gli aggregati di consumo da rp-usage; l’esecuzione dei pagamenti resta dietro gateway esterni.

## Confine di responsabilità

Possiede flussi di lavoro e record di fatturazione; non possiede i meccanismi interni dei gateway di pagamento esterni né la misurazione dell’utilizzo.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Fonte

`modules/repositories/business/rp-billing`