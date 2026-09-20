# rp-notify

## Scopo

Il singolo fan-out di notifiche dell'ecosistema: qualsiasi dominio dice una sola volta «informa l'utente» e questo modulo sceglie canali, policy e tentativi. I domini non accedono mai direttamente alle API SMTP/SMS/push.

## Modello mentale

Il dominio emette un intento di notifica (chi, cosa, modello, urgenza) → notify risolve canali e policy di recapito → gli adapter dei provider esterni eseguono l'invio effettivo. Tentativi e fallback di canale vivono qui, il significato del messaggio vive nel dominio.

## Valore per l'ecosistema

Un unico archivio «informa l'utente»:

- Modelli, canali, profilo e record di invio dietro un'unica API.
- Qualsiasi dominio conserva i propri testi di notifica e record di recapito in un unico luogo.

## Non obiettivi

- Non il recapito stesso dei messaggi — solo modelli, canali e record di invio.
- Non i thread di dialogo.

## Confine di responsabilità

Possiede l'orchestrazione delle notifiche e la policy di recapito; non possiede gli adapter di invio specifici del provider di basso livello né la logica di attivazione del dominio.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- Non incluso in una soluzione predefinita

## Origine

`modules/repositories/communications/rp-notify`