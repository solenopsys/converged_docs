## Ajouter un module

Les étapes sont les mêmes pour la plateforme de base et pour une couche produit.

1. **Créez le répertoire** par convention : `modules/microservices/<domain>/ms-<name>` pour un service, `modules/surfaces/<domain>/sf-<name>` pour un écran, `modules/workflows/wf-<name>` pour un processus.
2. **Déclarez le contrat** dans `modules/types/<domain>/` et générez les clients avec `bun run gen`. Le client apparaît sous la forme d’un paquet `g-<name>`, utilisable depuis le navigateur, depuis un autre processus sur le bus et depuis l’intérieur d’un workflow.
3. **Rédigez le README** avec une section `## Purpose` et une section sur la limite de responsabilité. Le premier paragraphe de chacune se retrouve dans le registre du site — rédigez-les pour un lecteur, pas pour vous-même.
4. **Ajoutez le module à une solution** s’il n’est pas livré seul : placez son nom court dans `modules/solutions/solutions.json` et déclarez ses dépendances.
5. **Reconstruisez la documentation** : `bun run build:doc` à la racine du dépôt. Le module apparaît dans le registre et les compteurs de la page de l’écosystème se recalculent automatiquement.

Ce que vous n’avez pas à faire : modifier les listes de modules dans les données du site, répéter la description dans la page d’accueil ou enregistrer le module ailleurs. La génération se fait dans un seul sens — des sources vers les données, jamais en sens inverse. Tout ce qui se trouve sous `data/` est écrasé lors de la prochaine compilation.

Ce que la revue exige d’un module : il ne doit pas accéder au stockage d’un autre module, contourner le bus par des appels directs, déclarer autre chose que les permissions qu’il utilise réellement ni élargir discrètement son domaine de responsabilité.
