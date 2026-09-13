## Aggiungere un modulo

I passaggi sono gli stessi per la piattaforma di base e per un livello di prodotto.

1. **Crea la directory** secondo la convenzione: `modules/microservices/<domain>/ms-<name>` per un servizio, `modules/surfaces/<domain>/sf-<name>` per una schermata, `modules/workflows/wf-<name>` per un processo.
2. **Dichiara il contratto** in `modules/types/<domain>/` e genera i client con `bun run gen`. Il client apparirà come pacchetto `g-<name>`, utilizzabile dal browser, da un altro processo sul bus e dall'interno di un workflow.
3. **Scrivi il README** con una sezione `## Purpose` e una sezione sui confini di responsabilità. Il primo paragrafo di ciascuna finirà nel registro sul sito: scrivili per un lettore, non per te stesso.
4. **Aggiungi il modulo a una soluzione** se non viene distribuito da solo: inserisci il suo nome breve in `modules/solutions/solutions.json` e dichiara le sue dipendenze.
5. **Ricostruisci la documentazione**: `bun run build:doc` dalla radice del repository. Il modulo apparirà nel registro e i contatori nella pagina dell'ecosistema verranno ricalcolati automaticamente.

Cosa non devi fare: modificare gli elenchi dei moduli nei dati del sito, ripetere la descrizione nella landing page o registrare il modulo altrove. La generazione procede in una sola direzione, dalle sorgenti ai dati, mai al contrario. Tutto ciò che si trova sotto `data/` viene sovrascritto dalla compilazione successiva.

Cosa verifica la revisione di un modulo: non accede allo storage di un altro modulo, non aggira il bus con chiamate dirette, dichiara solo i permessi che utilizza effettivamente e non amplia silenziosamente la propria area di responsabilità.
