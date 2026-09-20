# rp-telemetry

## Scopo

Il feed tecnico condiviso sullo stato di salute: i servizi segnalano “come stanno” (latenza, errori, segnali di risorse) qui invece di essere interrogati singolarmente da ogni strumento ops. Acquisizione normalizzata, un’unica superficie di interrogazione per lo stato di salute.

## Modello mentale

Il servizio invia eventi di salute (origine, segnale, tempo, payload) → la telemetria li normalizza in una forma uniforme. I consumatori ops (dashboard, flussi di incident) leggono lo stato di salute per servizio nel tempo. Il significato di business è attribuito dal lettore, non dall’archivio.

## Valore per l’ecosistema

Un unico journal di campioni numerici:

- Qualsiasi producer scrive righe (dispositivo, parametro, valore, unità, tempo) negli store hot/cold.
- Un’unica timeline per numeri di qualsiasi origine — sensori delle apparecchiature o altro.

## Non obiettivi

- Non archiviazione di log testuali.
- Non record di utilizzo.
- Non policy di allertamento o risoluzione degli incident.
## Limite di responsabilità

Responsabile dell’acquisizione e normalizzazione degli eventi di telemetria; non responsabile delle definizioni di analytics di prodotto, dell’allertamento o della remediation.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-telemetry`