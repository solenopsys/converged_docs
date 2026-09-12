# sf-equipment

## Scopo

Il reparto produttivo come un'unica area di lavoro: quali macchine esistono, in
quale stato si trova ciascuna, quale lavoro sta eseguendo, cosa indicano in
questo momento i suoi dati di telemetria, cosa le è accaduto e cosa è
programmato su di essa.

## Struttura

La superficie dichiara tre viste `setOf` — macchine, giornale, pianificazione — che
l'area di lavoro trasforma nei pulsanti permanenti di questa scheda, e una vista
`objectOf` per una macchina. L'apertura di una stampante apre quindi una
sottoscheda *all'interno* dell'attrezzatura anziché allontanarsi da essa. Quando
non è selezionato nulla, la superficie mostra la propria schermata,
`EquipmentDashboardView`.

## Confine di responsabilità

Legge e scrive `rp-equipment`. Legge `rp-orders` per il lavoro che una macchina
sta eseguendo e `rp-telemetry` per i suoi parametri in tempo reale — entrambi
direttamente dal browser, che è il punto in cui appartiene una composizione a
due chiamate; nessuno dei due repository conosce l'altro.

Lo stato della macchina viene scritto da qui perché, finché un ponte di
telemetria non lo segnala, l'operatore accanto alla macchina è la sua unica
fonte di verità.

## Dipendenze dirette del modulo

- `g-equipment`
- `g-orders`
- `g-telemetry`

## Appartenenza alla soluzione

- `production`

## Sorgente

`modules/surfaces/business/sf-equipment`
