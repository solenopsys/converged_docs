# Plan de contrôle Ptah

Ptah transforme une description de plateforme Converged en ressources Kubernetes en fonctionnement.
Il constitue le plan de contrôle du système : il détermine ce qui doit exister pour une plateforme,
quelles solutions sont actives et comment les charges de travail et le stockage des tenants sont placés.

## Modèle de plateforme souhaité

Le modèle de déploiement comporte trois couches :

| Ressource | Signification |
| --- | --- |
| Plateforme | Environnement d’exécution partagé, routage, profil de stockage, applications et carte des modules. |
| Solution | Ensemble de modules métier, de workflows et de processeurs ajouté à une plateforme. |
| Tenant | Site isolé avec sa propre portée, ses routes et, si nécessaire, son fragment de stockage. |

Ptah observe ces ressources et produit l’ensemble complet souhaité de
déploiements, services, volumes, configurations et routes. Kubernetes fait ensuite
converger le cluster vers cette description.

```text
Plateforme + Solution + Tenant
              |
              v
             Ptah
              |
              v
Charges de travail, stockage et routes Kubernetes
```

## Politique et mécanisme

Ptah sépare les mécanismes du cluster de la politique produit. Le contrôleur natif
observe Kubernetes, applique les ressources, enregistre l’état et supprime les
objets obsolètes. Une couche de politique pure convertit les données observées de
la plateforme en un résultat souhaité sans effectuer d’appels réseau ni modifier le cluster lui-même.

La même politique peut donc être évaluée avant le déploiement. Cela rend les
décisions de placement et de cycle de vie inspectables sans les reproduire dans
un second générateur de configuration.

## Profils de déploiement

Les profils modifient le placement du stockage sans modifier les images des applications :

- `mono` exécute une seule instance de stockage pour une plateforme compacte ;
- `multi` répartit les portées entre plusieurs fragments de stockage ;
- `cloud` attribue à chaque tenant une instance de stockage isolée et une limite de routage.

La règle de propriété des volumes reste la même dans chaque profil : chaque microservice
possède son propre volume de stockage. Ptah détermine quelle instance de Behemoth monte ces
volumes et publie la correspondance portée-stockage utilisée par les charges de travail sans état.

## Modules et déploiement progressif

Les solutions nomment les modules au lieu d’intégrer leurs octets. Ptah distribue une
carte de modules adressée par contenu et fournit le contenu immuable des modules par
l’intermédiaire d’un cache partagé. Les consommateurs reçoivent exactement le condensat qu’ils doivent charger.

Lorsque le condensat sélectionné change, la description de la charge de travail change également et
Kubernetes effectue le déploiement progressif. Un pod en fonctionnement enregistre donc le contenu
exact du module avec lequel il a démarré, et une restauration consiste à sélectionner à nouveau le condensat précédent.

## Réconciliation sûre

Ptah applique un ensemble complet souhaité et élague les ressources qui ne lui appartiennent plus.
Les ressources contenant des données sont conservées, sauf si leur suppression est explicitement
 demandée. Une entrée incomplète ou un échec de politique bloque l’élagage, empêchant qu’un problème
temporaire de dépendance soit interprété comme une demande de supprimer la plateforme.

## Place dans le système

Ptah n’est pas un pair sur le bus de messages Fujin et ne traite pas le trafic métier. Il crée et
configure les pairs, le stockage et les routes qui constituent l’environnement d’exécution. Une fois
qu’ils sont en fonctionnement, Fujin, Behemoth, Centimanus et Resonus effectuent leur travail indépendamment
du plan de contrôle.
