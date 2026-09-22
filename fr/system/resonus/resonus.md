# Passerelle média et IA de Resonus

Resonus connecte les conversations en temps réel à la plateforme Converged. Il gère
l’audio du navigateur, les appels téléphoniques, la transcription et les sessions d’IA,
tout en conservant les actions métier qui en résultent dans le même modèle
d’autorisations et de workflows que le reste du système.

## Une seule limite de session

Le transport média et l’interaction avec l’IA partagent l’état de l’appel, le
calendrier et le contexte. Les conserver dans un même processus natif évite de faire
passer une conversation en direct par plusieurs passerelles indépendantes avant
qu’elle n’atteigne un modèle ou un opérateur humain.

```text
browser or phone
       |
       v
    Resonus ---- AI session
       |
       +-------- human transfer
       |
       +-------- platform services and workflows
```

Une politique de déploiement détermine la manière dont un appel entrant est traité :
par une session d’IA, par une destination humaine, par un chemin de transfert ou par
un rejet. Le transport et l’exécution média restent natifs, tandis que la politique
reste une petite couche de décision remplaçable.

## Intégration à la plateforme

Resonus utilise les services de la plateforme pour le contexte des appels et les
enregistrements métier. Des fragments audio peuvent transiter par le cache d’exécution
avant que le service propriétaire ne les stocke. Les appels peuvent déclencher des
workflows ou des opérations de service sans donner à la passerelle la responsabilité
de ces domaines.

La transcription transforme la voix en un type d’entrée structurée identique à celui
disponible pour les autres interfaces. Ainsi, un opérateur ou un client peut interagir
naturellement, tandis que l’action qui en résulte respecte toujours les contrats de
service et les chemins d’audit habituels.

## Contexte de locataire approuvé

Pour le trafic arrivant via Fujin, Resonus accepte la portée du locataire fournie par
l’enveloppe de message approuvée. Il ne déduit pas cette portée d’un numéro de
téléphone, d’un libellé utilisateur ou d’une charge utile de modèle. La portée est
conservée pour la session et transmise aux services de la plateforme utilisés par
celle-ci.

Les chemins d’entrée qui ne peuvent pas établir une portée approuvée doivent être
isolés jusqu’à ce que le déploiement les lie à une portée. Cela empêche un identifiant
média pratique de devenir silencieusement une décision d’autorisation.

## Limite avec les fournisseurs

Les fournisseurs d’IA se trouvent derrière une limite commune de session et de
politique. Le choix du fournisseur, la sélection du modèle, la voix et le comportement
de transfert sont des décisions de déploiement plutôt que des hypothèses intégrées
partout dans les modules métier. La passerelle peut faire évoluer ses adaptateurs de
fournisseurs sans modifier la manière dont le reste de Converged traite un appel
aidé par l’IA.

## Place dans le système

Resonus prend en charge l’exécution des médias en temps réel et des sessions d’IA. Il
ne prend pas en charge les fiches clients, l’historique des appels, les définitions de
workflows, la sélection du locataire ni le routage général des messages. Ces
responsabilités restent dévolues aux services de domaine, à Centimanus, au périmètre
approuvé et à Fujin.
