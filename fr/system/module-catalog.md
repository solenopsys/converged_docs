# Catalogue des modules

Cet index est généré à partir du registre des modules Converged. Chaque entrée renvoie vers la documentation détenue par ce module ; les dépendances sont tirées du manifeste de paquet de son espace de travail, et l’appartenance aux solutions provient de `modules/solutions`.

## Accès et sécurité

### [lm-secrets](/en/docs/modules/lm-secrets)

Fournit le contrat de service pour stocker, récupérer et supprimer des valeurs secrètes nommées.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-access](/en/docs/modules/rp-access)

rp-access est un dépôt du domaine sequrity. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth est un dépôt du domaine sequrity. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-environment](/en/docs/modules/rp-environment)

Stocke et récupère la configuration d’environnement associée aux utilisateurs de la plateforme.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity est un dépôt du domaine sequrity. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth est un dépôt du domaine sequrity. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth est une surface du domaine sequrity. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Fournit l’interface d’administration permettant de créer, consulter, mettre à jour et supprimer des enregistrements de secrets nommés.

- Dépendances directes : aucune
- Solutions : aucune

## IA et agents

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant est un dépôt du domaine de l’IA. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Fournit le stockage et la récupération de contextes d’IA nommés, y compris leurs variantes linguistiques.

- Dépendances directes : aucune
- Solutions : `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants est une surface du domaine de l’IA. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : `sf-requests`
- Solutions : `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Fournit l’espace de travail d’IA permettant de répertorier, modifier et enregistrer des contextes nommés dans plusieurs langues.

- Dépendances directes : aucune
- Solutions : `ai`

## Analytique et télémétrie

### [rp-counters](/en/docs/modules/rp-counters)

Fournit le contrat de service pour collecter et interroger des compteurs analytiques.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Fournit les données de tableaux de bord et les vues analytiques des métriques de la plateforme.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs est un dépôt du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry est un dépôt du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage est un dépôt du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards est une surface du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs est une surface du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry est une surface du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage est une surface du domaine de l’analytique. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

## Automatisation et orchestration

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Intègre l’automatisation de la plateforme aux ressources Kubernetes grâce à un client dédié et à un contrat de service.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag est un dépôt du domaine de l’automatisation. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller est un dépôt du domaine de l’automatisation. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks est un dépôt du domaine de l’automatisation. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation est la surface du domaine de l’automatisation dédiée aux workflows, aux planifications, aux points de terminaison webhook et à leur historique d’exécution.

- Dépendances directes : aucune
- Solutions : `automation`

## Domaine métier

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing est un dépôt du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment est un dépôt du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-events](/en/docs/modules/rp-events)

Fournit la création, le stockage et la récupération d’événements métier.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-finance](/en/docs/modules/rp-finance)

Fournit les opérations financières pour les transactions, les synthèses périodiques, la trésorerie, les créances et les dettes.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-orders](/en/docs/modules/rp-orders)

Fournit le contrat de service pour créer, mettre à jour, répertorier et suivre les commandes métier.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests est un dépôt du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews est un dépôt du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales est un dépôt du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff est un dépôt du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-orders](/en/docs/modules/sf-orders)

Fournit l’interface commerciale pour les listes de commandes et de demandes, les détails des commandes, le filtrage par statut et les tableaux de bord opérationnels.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests est une surface du domaine métier. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

## Communications

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls est un dépôt du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats est un dépôt du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-community](/en/docs/modules/rp-community)

rp-community est un dépôt du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify est un dépôt du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-resonus](/en/docs/modules/rp-resonus)

Fournit la configuration des communications pour les numéros de téléphone gérés et les paramètres de passerelle LLM.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads est un dépôt du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls est une surface du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats est une surface du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-community](/en/docs/modules/sf-community)

sf-community est une surface du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads est une surface du domaine des communications. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `ai`

## Contenu et documents

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier est un dépôt du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery est un dépôt du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown est un dépôt du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Fournit les opérations de stockage des fichiers de scripts, notamment la lecture, l’enregistrement, le hachage et la suppression.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-static](/en/docs/modules/rp-static)

Fournit le contrat de service pour le contenu statique et les métadonnées du cache SSR.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct est un dépôt du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Fournit l’interface de classification pour parcourir les entités, les correspondances et les structures arborescentes.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs est une surface du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery est une surface du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing est une surface du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown est une surface du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-static](/en/docs/modules/sf-static)

Fournit l’interface des opérations permettant d’inspecter et de vider les entrées du cache SSR statique.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct est une surface du domaine du contenu. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

## Fichiers et stockage

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors est une lambda du domaine des données. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps est un dépôt du domaine des données. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-files](/en/docs/modules/rp-files)

rp-files est un dépôt du domaine des données. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store est un dépôt du domaine des données. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps est une surface du domaine des données. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-files](/en/docs/modules/sf-files)

sf-files est une surface du domaine des données. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

## Fournisseurs de distribution de messages

### [lm-push](/en/docs/modules/lm-push)

lm-push est une lambda du domaine des fournisseurs. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses est une lambda du domaine des fournisseurs. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms est une lambda du domaine des fournisseurs. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp est une lambda du domaine des fournisseurs. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

## Conversion de modèles

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor est une lambda du domaine des convertisseurs. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

## Workflows

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Résume les dialogues non traités issus des chats et des appels à l’aide d’un LLM, puis enregistre les titres, les descriptions et la classification du bruit.

- Dépendances directes : aucune
- Solutions : aucune

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analyse un fichier stocké non archiv é, en produisant des aperçus de modèles et des estimations CNC ou d’impression 3D lorsque cela est pris en charge.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Décompresse une archive téléversée en une collection de fichiers stockés destinés à une analyse ultérieure.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze est un workflow du domaine de la plateforme. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Traite les fichiers téléversés par lots : il décompresse les archives, identifie les fichiers de modèles et crée une demande de fabrication à partir de ceux-ci.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze est un workflow du domaine de la plateforme. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import est un workflow du domaine de la plateforme. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach est un workflow du domaine de la plateforme. Son objectif détaillé est maintenu avec le code source du module.

- Dépendances directes : aucune
- Solutions : aucune

## Dépendances des solutions

- `ai` : `security`
- `analitycs` : `security`
- `content` : `security`
- `requests` : aucune dépendance de solution
- `security` : aucune dépendance de solution
