# rp-counters

## Scopo

Configurazione per tenant dei contatori di analisi esterni: memorizza gli ID di tracciamento (GA4, GTM, Yandex Metrika, Meta Pixel) o uno snippet head personalizzato, in modo che SSR possa iniettare gli script corretti per tenant.

## Modello mentale

L'operatore salva un contatore (tipo, ID di tracciamento o snippet, flag di abilitazione) → lo store conserva la configurazione. SSR legge i contatori abilitati per il tenant corrente ed esegue il rendering dei tag corrispondenti. Qui non vengono raccolti numeri, solo le impostazioni dei contatori.

## Valore per l'ecosistema

Un unico punto per l'integrazione delle analisi:

- I contatori esterni (GA4, GTM, Metrika, Pixel) e gli snippet personalizzati sono configurati per tenant invece di essere codificati per landing page.

## Non obiettivi

- Non archiviazione di eventi grezzi.
- Non diari di campioni numerici.
- Non record di utilizzo o fatturazione.
## Limite di responsabilità

Possiede le configurazioni dei contatori (tipo, ID di tracciamento o snippet, flag di abilitazione); non raccoglie metriche, non aggrega l'utilizzo e non si occupa di fatturazione.

## Dipendenze dirette dei moduli

- Nessuna

## Appartenenza alla soluzione

- `analitycs`

## Fonte

`modules/repositories/analytics/rp-counters`