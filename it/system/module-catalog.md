# Catalogo dei moduli

Questo indice è generato dal registro dei moduli Converged. Ogni voce collega alla documentazione di quel modulo; le dipendenze sono tratte dal manifest del pacchetto workspace e l'appartenenza alle soluzioni proviene da `modules/solutions`.

## Accesso e sicurezza

### [lm-secrets](/en/docs/modules/lm-secrets)

Fornisce il contratto di servizio per l'archiviazione, il recupero e l'eliminazione di valori segreti denominati.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-access](/en/docs/modules/rp-access)

rp-access è un repository nel dominio sequrity. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth è un repository nel dominio sequrity. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [rp-environment](/en/docs/modules/rp-environment)

Archivia e recupera la configurazione dell'ambiente associata agli utenti della piattaforma.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity è un repository nel dominio sequrity. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth è un repository nel dominio sequrity. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth è una surface nel dominio sequrity. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Fornisce l'interfaccia di amministrazione per creare, visualizzare, aggiornare ed eliminare record segreti denominati.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-team](/en/docs/modules/sf-team)

sf-team è una surface nel dominio sequrity. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

## IA e agenti

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant è un repository nel dominio ai. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Fornisce l'archiviazione e il recupero di contesti IA denominati, incluse le relative varianti linguistiche.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants è una surface nel dominio ai. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: `sf-requests`
- Soluzioni: `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Fornisce l'area di lavoro IA per elencare, modificare e salvare contesti denominati in più lingue.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`

## Analisi e telemetria

### [rp-counters](/en/docs/modules/rp-counters)

Archivia le configurazioni dei contatori analitici esterni per tenant (tracking id, snippet head) per l'iniezione SSR.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Archivia i pin degli indicatori della dashboard personale: quali widget un utente ha fissato, il loro ordine e i metadati di visualizzazione.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs è un repository nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry è un repository nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage è un repository nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards è una surface nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs è una surface nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry è una surface nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage è una surface nel dominio analytics. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `analitycs`

## Automazione e orchestrazione

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Integra l'automazione della piattaforma con le risorse Kubernetes tramite un client dedicato e un contratto di servizio.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag è un repository nel dominio automation. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `automation`, `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller è un repository nel dominio automation. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `automation`

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks è un repository nel dominio automation. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `automation`

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation è una surface nel dominio automation. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `automation`

## Dominio business

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `billing`

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [rp-events](/en/docs/modules/rp-events)

Fornisce la creazione, l'archiviazione e il recupero degli eventi aziendali.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [rp-finance](/en/docs/modules/rp-finance)

Fornisce operazioni finanziarie per transazioni, riepiloghi di periodo, flusso di cassa, crediti e debiti.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-invoices](/en/docs/modules/rp-invoices)

rp-invoices è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `billing`

### [rp-metering](/en/docs/modules/rp-metering)

rp-metering è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `billing`

### [rp-orders](/en/docs/modules/rp-orders)

Fornisce il contratto di servizio per creare, aggiornare, elencare e tracciare gli ordini aziendali.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff è un repository nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [sf-equipment](/en/docs/modules/sf-equipment)

sf-equipment è una surface nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [sf-orders](/en/docs/modules/sf-orders)

Fornisce l'interfaccia di vendita per elenchi di ordini e richieste, dettagli degli ordini, filtraggio per stato e dashboard operative.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests è una surface nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [sf-reviews](/en/docs/modules/sf-reviews)

sf-reviews è una surface nel dominio business. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

## Comunicazioni

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls è un repository nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats è un repository nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`

### [rp-community](/en/docs/modules/rp-community)

rp-community è un repository nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify è un repository nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [rp-resonus](/en/docs/modules/rp-resonus)

Fornisce la configurazione delle comunicazioni per numeri di telefono gestiti e impostazioni del gateway LLM.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-support](/en/docs/modules/rp-support)

rp-support è un repository nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads è un repository nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`, `communications`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls è una surface nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats è una surface nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`

### [sf-community](/en/docs/modules/sf-community)

sf-community è una surface nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`

### [sf-support](/en/docs/modules/sf-support)

sf-support è una surface nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads è una surface nel dominio communications. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `ai`, `communications`

## Contenuti e documenti

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier è un repository nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery è un repository nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown è un repository nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Fornisce operazioni di archiviazione per file di script, incluse lettura, salvataggio, hashing ed eliminazione.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-static](/en/docs/modules/rp-static)

Fornisce il contratto di servizio per contenuti statici e metadati della cache SSR.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct è un repository nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Fornisce l'interfaccia del classificatore per navigare tra entità, mappature e strutture ad albero.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs è una surface nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery è una surface nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing è una surface nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown è una surface nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-static](/en/docs/modules/sf-static)

Fornisce l'interfaccia operativa per ispezionare e cancellare le voci statiche della cache SSR.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct è una surface nel dominio content. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

## File e archiviazione

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors è una lambda nel dominio data. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps è un repository nel dominio data. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [rp-files](/en/docs/modules/rp-files)

rp-files è un repository nel dominio data. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `communications`, `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store è un repository nel dominio data. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps è una surface nel dominio data. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [sf-files](/en/docs/modules/sf-files)

sf-files è una surface nel dominio data. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

## Provider di recapito dei messaggi

### [lm-lemonsqueezy](/en/docs/modules/lm-lemonsqueezy)

lm-lemonsqueezy è una lambda nel dominio providers. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `billing`

### [lm-push](/en/docs/modules/lm-push)

lm-push è una lambda nel dominio providers. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses è una lambda nel dominio providers. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms è una lambda nel dominio providers. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp è una lambda nel dominio providers. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

## Conversione dei modelli

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor è una lambda nel dominio convertors. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

## Flussi di lavoro

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Riassume con un LLM i dialoghi non elaborati di chat e chiamate, quindi archivia titoli, descrizioni e classificazione del rumore.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [wf-equipment-incident](/en/docs/modules/wf-equipment-incident)

wf-equipment-incident è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analizza un singolo file archiviato non compresso, producendo anteprime del modello e stime CNC o di stampa 3D quando supportate.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Espande un archivio caricato in una raccolta di file archiviati per l'analisi successiva.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Elabora i file caricati in batch: espande gli archivi, identifica i file di modello e crea a partire da essi una richiesta di produzione.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [wf-order-review-followup](/en/docs/modules/wf-order-review-followup)

wf-order-review-followup è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [wf-order-review-request](/en/docs/modules/wf-order-review-request)

wf-order-review-request è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [wf-payment-settle](/en/docs/modules/wf-payment-settle)

wf-payment-settle è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `billing`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `requests`

### [wf-request-to-order](/en/docs/modules/wf-request-to-order)

wf-request-to-order è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: nessuna

### [wf-team-invite](/en/docs/modules/wf-team-invite)

wf-team-invite è un workflow nel dominio platform. Il suo scopo dettagliato è mantenuto con il sorgente del modulo.

- Dipendenze dirette: nessuna
- Soluzioni: `production`

## Dipendenze delle soluzioni

- `ai`: `security`
- `analitycs`: `security`
- `automation`: `security`
- `billing`: `security`
- `communications`: `security`
- `content`: `security`
- `production`: `security`, `analitycs`, `requests`
- `requests`: nessuna dipendenza da soluzioni
- `security`: nessuna dipendenza da soluzioni