## Il registro dei moduli

Il registro non è un documento separato né un database. È l'albero delle sorgenti stesso.

```text
modules/
├── microservices/<domain>/ms-<name>    un dominio dati e la sua API
├── surfaces/<domain>/sf-<name>   una schermata montata a runtime
├── workflows/wf-<name>                 un processo per il runtime DAG
├── types/<domain>/                     contratti NRPC
└── solutions/                          quali moduli vengono distribuiti insieme
```

Un modulo esiste perché esiste la sua directory. Appartiene a un dominio perché si trova nella cartella di quel dominio. Appartiene a una soluzione perché `solutions/solutions.json` lo nomina. Non esiste un quarto luogo in cui tutto questo debba essere ripetuto: per questo la pagina dell'ecosistema sul sito viene prodotta attraversando l'albero invece di modificare un elenco.

Lo scopo di un modulo viene preso dal suo `README.md`: il primo paragrafo sotto `## Purpose` (per le superfici, `## UI Purpose`) e il paragrafo sotto l'intestazione dei confini di responsabilità. Questi due paragrafi sono il contratto del modulo in linguaggio semplice e ogni modulo è tenuto a fornirli.

Un livello di prodotto sopra la base — `club`, per esempio — è organizzato allo stesso modo e può omettere il livello del dominio: i suoi moduli si trovano direttamente in `modules/microservices/ms-<name>`. La compilazione comprende entrambi i layout.
