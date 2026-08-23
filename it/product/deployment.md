## Distribuzione

Converged supporta diversi scenari di installazione: dalla piccola officina al deployment di produzione nell’infrastruttura aziendale. La piattaforma base viene distribuita sopra **k3s**, una distribuzione Kubernetes leggera adatta a dispositivi edge, server locali e ambienti cloud.

I profili principali sono due:

- **Mono** — UI, Runtime, microservizi, storage e cache sono impacchettati in modo compatto. È la modalità per sviluppo, prototipi, demo e piccole installazioni dove conta soprattutto la semplicità di avvio.
- **Multi** — UI, gruppi Runtime, gruppi di microservizi per dominio, storage e cache sono separati. È il profilo standard di produzione quando servono isolamento, scalabilità e controllo più preciso del carico.

Entrambi i profili usano lo stesso codice. Cambiano solo la topologia dei container e la configurazione. Un’azienda può iniziare con un’installazione compatta e poi spostare lo stesso sistema in un’infrastruttura più seria senza riscrivere il prodotto.

Negli scenari self-hosted, il cliente controlla installazione, rete, backup, aggiornamenti e posizione fisica dei dati. Questo è adatto ad aziende con requisiti interni di sicurezza o con il desiderio di mantenere la produzione completamente dalla propria parte. La consegna cloud elimina il lavoro operativo: la piattaforma viene distribuita e aggiornata dal team del servizio, mentre il cliente riceve un ambiente pronto.

È possibile anche un’opzione ibrida: dati sensibili e attrezzature restano localmente, mentre il cloud viene usato per aggiornamenti, accesso esterno, coordinamento di team distribuiti o singole funzioni IA. Il principio importante è non vincolare il cliente a un solo modello di consegna.
