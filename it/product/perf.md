## Prestazioni

Converged è progettato per siti produttivi che non sempre dispongono di un grande parco server. Per questo il sistema evita peso inutile: Bun riduce l’overhead dei processi backend, Runtime resta stateless e i microservizi possono essere raggruppati per tipo di carico invece di eseguire centinaia di container separati.

Le prestazioni derivano dall’architettura, non da un singolo trucco. I dati non attraversano strati inutili, i servizi possiedono i propri store, Runtime parallelizza workflow e attività cron, e gli adattatori nativi vengono usati dove HTTP o un normale strato JS aggiungerebbero troppo overhead.

Un’installazione compatta può funzionare su un piccolo server o single-board computer se il carico corrisponde alla scala dell’officina. Con la crescita, Runtime, microservizi e gruppi storage possono essere separati per usare più core CPU, isolare attività pesanti ed evitare che un collo di bottiglia fermi tutto il sistema.

La piattaforma non promette prestazioni infinite “out of the box”. I colli di bottiglia dipendono da attrezzature, volume dei file, numero di ordini, provider IA e integrazioni. L’architettura di Converged permette di iniziare in modo compatto e scalare solo le parti che diventano realmente calde.
