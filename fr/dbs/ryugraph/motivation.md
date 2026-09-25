## Pourquoi le stockage en graphe convient aux agents IA

La valeur d’une base de données graphe dans un système conçu en priorité pour l’IA ne se limite pas à accélérer le parcours des relations. Son avantage principal est qu’un graphe représente les informations sous une forme naturellement facile à comprendre et à explorer pour un agent LLM.

Une base de données relationnelle repose sur des tables, des colonnes, des clés étrangères et des jointures prédéfinies. Cela fonctionne extrêmement bien lorsque la structure de la requête est connue à l’avance. Un agent, en revanche, fonctionne souvent différemment. Il peut commencer par une demande incomplète, trouver un objet pertinent, examiner son environnement, suivre une relation utile et continuer jusqu’à avoir recueilli suffisamment de contexte.

Un graphe prend directement en charge ce style de fonctionnement.

Par exemple, une entreprise de production peut posséder des objets tels qu’une entreprise, un employé, un fil d’e-mails, une pièce jointe, une pièce, un matériau, une demande de devis, un devis, une commande et une machine. Ces objets peuvent être reliés par des relations porteuses de sens :

```text
John Smith → WORKS_AT → Acme CNC
Message → SENT_BY → John Smith
Message → HAS_FILE → housing_revC.step
housing_revC.step → REVISION_OF → Housing
RFQ → REQUESTS → Housing
Quote → ANSWERS → RFQ
Order → BASED_ON → Quote
```

Pour un LLM, cette structure est déjà informative. `Acme CNC`, `Housing`, `REVISION_OF`, `SENT_BY` et `BASED_ON` ne sont pas des clés de base de données opaques. Leurs noms portent une signification sémantique. Le graphe agit donc non seulement comme un espace de stockage, mais aussi comme une description compacte du domaine métier.

Cela change la manière dont l’agent peut fonctionner.

Supposons qu’un utilisateur demande :

> Trouve ce que le client voulait dans cette commande de boîtiers Acme.

L’agent n’a pas besoin de construire immédiatement une requête volumineuse. Il peut d’abord trouver `Acme CNC`, examiner les commandes associées, identifier la commande de boîtiers pertinente, examiner ses fils de discussion, puis récupérer uniquement les quelques messages qui comptent.

Une exploration typique peut ressembler à ceci :

```text
Acme CNC
  ↓
Commandes
  ↓
Commande de boîtiers
  ↓
Fils de discussion
  ↓
Messages
  ↓
Pièces jointes
```

À chaque étape, l’agent ne reçoit qu’une petite vue locale du graphe. Par exemple :

```json
{
  "id": "order_551",
  "type": "Order",
  "name": "Housing batch",
  "relations": {
    "CUSTOMER": 1,
    "THREAD": 3,
    "FILE": 11,
    "PART": 2,
    "QUOTE": 2
  }
}
```

Cela suffit au modèle pour comprendre le type d’objet qu’il examine et la direction dans laquelle il est utile de poursuivre l’exploration.

La conséquence importante est que l’agent n’a pas besoin d’avoir l’intégralité du schéma de la base de données dans son contexte. Il n’a pas à mémoriser des dizaines de tables, de clés étrangères, de tables de jointure ou d’expressions SQL récursives. Il lui suffit de disposer de l’objet courant et d’une petite description de ses relations locales.

Cela rend l’exploration récursive à la fois économique et robuste.

Les contenus volumineux n’ont pas non plus besoin d’être stockés dans le graphe. Les corps des e-mails, les fichiers PDF, les modèles CAO, les images et autres objets lourds peuvent rester dans KVS ou dans un stockage d’objets. Le graphe ne conserve que des métadonnées compactes, des identifiants d’objets, des clés de stockage et des relations.

L’architecture sépare donc la structure du contenu :

```text
Graphe
    → objets, relations, métadonnées, clés de stockage

KVS / Stockage d’objets
    → corps des e-mails, PDF, STEP, STL, DXF, images

Agent LLM
    → explore d’abord le graphe
    → récupère le contenu volumineux uniquement lorsque cela est nécessaire
```

Cela est particulièrement important lorsqu’on travaille avec plusieurs années d’historique d’entreprise. Des centaines de gigaoctets d’e-mails et de pièces jointes peuvent être représentés par un graphe beaucoup plus petit contenant les entreprises, les personnes, les fils de discussion, les fichiers, les commandes, les pièces et leurs relations.

L’agent peut effectuer dix ou vingt petites opérations sur le graphe tout en ne consommant que quelques kilo-octets de contexte structuré. À la fin de cette exploration, il peut déjà savoir quelle entreprise est concernée, quelles commandes sont pertinentes, quelles personnes ont participé, quels fichiers appartiennent au dossier et où se trouvent les conversations importantes. Ce n’est qu’à ce moment-là qu’il charge les corps des messages ou les fichiers réellement nécessaires pour répondre à la question.

Le graphe est également naturellement extensible. Un système peut initialement ne contenir que `Company`, `Person`, `Message`, `File` et `Order`. Plus tard, il peut intégrer `Part`, `Revision`, `Material`, `Machine`, `Job`, `Supplier` ou `Contract`, ainsi que de nouvelles relations telles que `REVISION_OF`, `USES_MATERIAL`, `MANUFACTURED_ON` ou `SUPPLIED_BY`.

L’interface de l’agent n’a pas besoin d’être fondamentalement modifiée. Elle peut continuer à utiliser le même petit ensemble d’opérations :

```text
find
inspect
follow
expand
search
fetch
```

Il s’agit d’une différence importante par rapport à un système où chaque nouvelle relation métier finit par créer un nouvel ensemble de jointures SQL, de méthodes d’API et de logiques spécifiques aux requêtes.

Un exemple pratique illustre bien cet avantage.

L’utilisateur demande :

> Trouve le contrat de l’entreprise pour laquelle nous avons imprimé des pièces en nylon l’année dernière.

L’utilisateur ne se souvient ni du nom de l’entreprise, ni du numéro de commande, ni de l’objet de l’e-mail, ni du nom du fichier.

L’agent peut partir du concept qu’il connaît :

```text
Nylon
  ↓
Travaux
  ↓
Commandes
  ↓
Entreprises
  ↓
Documents
  ↓
Contrat
```

Une autre demande pourrait être :

> Trouve le fichier CAO que le client a envoyé avant que nous recalculions le devis.

Là encore, l’agent peut naviguer à travers les relations et la chronologie jusqu’à trouver la pièce jointe pertinente, sans que l’utilisateur ait besoin de savoir comment les données sous-jacentes sont organisées.

C’est la principale raison architecturale d’utiliser un graphe avec un agent LLM.

Le graphe n’est pas simplement un remplacement plus rapide des jointures SQL. Il s’agit d’une représentation sémantique compacte du domaine, que le modèle peut lire, comprendre et explorer progressivement.

Dans cette architecture, le graphe devient une mémoire structurelle, le stockage d’objets contient le contenu volumineux et le LLM devient l’explorateur sémantique qui se déplace dans la structure.

Le principe central est simple :

> **Le graphe est un modèle de données natif pour les agents.**

Il fournit à l’agent une forme de données compacte, porteuse de sens, extensible et naturellement adaptée à l’exploration récursive.
