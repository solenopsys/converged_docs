## Le registre des modules

Le registre n’est ni un document séparé ni une base de données. C’est l’arborescence des sources elle-même.

```text
modules/
├── microservices/<domain>/ms-<name>    un domaine de données et son API
├── surfaces/<domain>/sf-<name>   un écran monté à l’exécution
├── workflows/wf-<name>                 un processus pour le moteur DAG
├── types/<domain>/                     des contrats NRPC
└── solutions/                          les modules livrés ensemble
```

Un module existe parce que son répertoire existe. Il appartient à un domaine parce qu’il se trouve dans le dossier de ce domaine. Il appartient à une solution parce que `solutions/solutions.json` le nomme. Il n’existe pas de quatrième endroit où tout cela devrait être répété — c’est pourquoi la page de l’écosystème du site est produite en parcourant l’arborescence plutôt qu’en modifiant une liste.

Le but d’un module est tiré de son `README.md` : le premier paragraphe sous `## Purpose` (pour les surfaces, `## UI Purpose`) et le paragraphe sous le titre délimitant la responsabilité. Ces deux paragraphes constituent le contrat du module en langage courant, et chaque module les doit.

Une couche produit au-dessus de la base — `club`, par exemple — est structurée de la même manière et peut supprimer le niveau de domaine : ses modules se trouvent directement dans `modules/microservices/ms-<name>`. La compilation comprend les deux structures.
