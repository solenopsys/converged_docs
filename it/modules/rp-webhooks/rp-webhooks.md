# rp-webhooks

## Scopo

L'unica porta di ingresso per il mondo esterno: i sistemi esterni chiamano un
endpoint webhook, e questo modulo convalida, normalizza e distribuisce gli eventi
verso l'interno. Nessun dominio espone un proprio schema di URL di callback.

## Modello mentale

POST del sistema esterno → il webhook convalida firma e struttura → normalizzato
l'evento viene registrato come consegna e instradato al topic configurato.
I tentativi di consegna e la convalida risiedono qui; la reazione di business avviene
a valle.

## Valore per l'ecosistema

Un unico ingresso per i callback esterni:

- Configurazioni degli endpoint e record di consegna dietro un'unica API.
- Qualsiasi sistema esterno ottiene la stessa forma di endpoint invece di un'infrastruttura dedicata per integrazione.

## Non obiettivi

- Nessuna esecuzione di workflow.
- Nessuna pubblicazione di eventi né invio di notifiche.
## Limite di responsabilità

Responsabile del trasporto webhook, della convalida e dei tentativi di consegna; non responsabile
dell'elaborazione di business del sistema di destinazione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alle soluzioni

- Non incluso in una soluzione predefinita

## Origine

`modules/repositories/automation/rp-webhooks`