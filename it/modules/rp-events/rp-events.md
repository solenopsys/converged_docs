# rp-events

## Scopo

Il journal condiviso del bus di eventi di business: qualsiasi dominio pubblica qui “cosa è successo” senza conoscere i suoi consumatori. Ordini, richieste, apparecchiature, pagamenti — parlano tutti un unico linguaggio di eventi.

## Modello mentale

Il producer emette un evento tipizzato (kind, entity, time, payload) → arriva sul feed condiviso. I consumer (trigger di workflow, notificatori, analisi) si iscrivono per tipo e reagiscono. Il publisher non chiama mai direttamente il consumer.

## Valore nell'ecosistema

Punto di disaccoppiamento per i cambi di stato:

- Eventi di business tipizzati pubblicati una volta ed elencati di nuovo tramite un'unica API.
- Qualsiasi dominio registra “cosa è successo” senza conoscere i suoi lettori.

## Non obiettivi

- Non il nastro di log grezzo.
- Non contatori o aggregati.
- Non l'esecuzione del workflow stessa.
## Confine di responsabilità

Possiede creazione, archiviazione e recupero degli eventi; non possiede l'elaborazione business lato consumer né l'esecuzione dei workflow.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Origine

`modules/repositories/business/rp-events`