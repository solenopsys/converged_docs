# Gateway multimediale e AI di Resonus

Resonus collega le conversazioni in tempo reale alla piattaforma Converged. Gestisce
audio del browser, chiamate telefoniche, trascrizione e sessioni AI, mantenendo
le azioni aziendali risultanti all'interno dello stesso modello di autorizzazioni
e flussi di lavoro utilizzato dal resto del sistema.

## Un unico confine di sessione

Il trasporto multimediale e l'interazione con l'AI condividono lo stato della
chiamata, la temporizzazione e il contesto. Mantenerli in un unico processo
nativo evita di far passare una conversazione in corso attraverso diversi
gateway indipendenti prima che possa raggiungere un modello o un operatore umano.

```text
browser o telefono
       |
       v
    Resonus ---- sessione AI
       |
       +-------- trasferimento a un operatore umano
       |
       +-------- servizi e flussi di lavoro della piattaforma
```

Una policy di deployment sceglie come gestire una chiamata in arrivo: tramite una
sessione AI, una destinazione umana, un percorso di trasferimento o un rifiuto.
L'esecuzione del trasporto e dei contenuti multimediali rimane nativa, mentre la
policy resta un piccolo livello decisionale sostituibile.

## Integrazione con la piattaforma

Resonus utilizza i servizi della piattaforma per il contesto delle chiamate e i
record aziendali. I frammenti audio possono passare attraverso la cache di
runtime prima che il servizio proprietario li memorizzi. Le chiamate possono
attivare flussi di lavoro o operazioni dei servizi senza assegnare al gateway la
proprietà di tali domini.

La trascrizione trasforma la voce nello stesso tipo di input strutturato
disponibile per le altre interfacce. Questo consente a un operatore o a un
cliente di interagire naturalmente, mentre l'azione risultante segue comunque i
normali contratti dei servizi e i percorsi di audit.

## Contesto affidabile del tenant

Per il traffico che arriva tramite Fujin, Resonus accetta l'ambito del tenant
dall'envelope di messaggio affidabile. Non deduce l'ambito da un numero di
telefono, da un'etichetta utente o dal payload del modello. L'ambito viene
mantenuto per la sessione e inoltrato ai servizi della piattaforma utilizzati da
quella sessione.

I percorsi di ingresso che non possono stabilire un ambito affidabile devono
essere isolati finché il deployment non li associa a uno. Questo impedisce che
un identificatore multimediale comodo diventi silenziosamente una decisione di
autorizzazione.

## Confine del provider

I provider AI risiedono dietro un confine comune di sessione e policy. La scelta
del provider, la selezione del modello, la voce e il comportamento di
trasferimento sono decisioni di deployment, non presupposti incorporati nei
moduli aziendali. Il gateway può far evolvere i propri adapter dei provider
senza modificare il modo in cui il resto di Converged gestisce una chiamata
assistita dall'AI.

## Collocazione nel sistema

Resonus gestisce i contenuti multimediali in tempo reale e l'esecuzione delle
sessioni AI. Non gestisce i record dei clienti, la cronologia delle chiamate, le
definizioni dei flussi di lavoro, la selezione del tenant o l'instradamento
generale dei messaggi. Tali responsabilità restano ai servizi di dominio,
a Centimanus, all'edge affidabile e a Fujin.
