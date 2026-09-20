# Catalogue des modules

Cet index est généré à partir du registre des modules Converged. Chaque entrée renvoie à la documentation propre à ce module ; les dépendances sont tirées du manifeste du paquet workspace correspondant, et l'appartenance aux solutions provient de `modules/solutions`.

## Accès et sécurité

### [lm-secrets](/en/docs/modules/lm-secrets)

Fournit le contrat de service pour le stockage, la récupération et la suppression des valeurs secrètes nommées.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-access](/en/docs/modules/rp-access)

rp-access est un dépôt dans le domaine sequrity. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth est un dépôt dans le domaine sequrity. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-environment](/en/docs/modules/rp-environment)

Stocke et récupère la configuration d'environnement associée aux utilisateurs de la plateforme.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity est un dépôt dans le domaine sequrity. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth est un dépôt dans le domaine sequrity. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth est une surface dans le domaine sequrity. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Fournit l'interface d'administration pour créer, afficher, mettre à jour et supprimer les enregistrements secrets nommés.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-team](/en/docs/modules/sf-team)

sf-team est une surface dans le domaine sequrity. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

## IA et agents

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant est un dépôt dans le domaine ai. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Fournit le stockage et la récupération des contextes IA nommés, y compris leurs variantes linguistiques.

- Dépendances directes : aucune
- Solutions : `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants est une surface dans le domaine ai. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : `sf-requests`
- Solutions : `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Fournit l'espace de travail IA pour répertorier, modifier et enregistrer les contextes nommés en plusieurs langues.

- Dépendances directes : aucune
- Solutions : `ai`

## Analytique et télémétrie

### [rp-counters](/en/docs/modules/rp-counters)

Stocke les configurations de compteurs analytiques externes par tenant (identifiants de suivi, extraits d'en-tête) pour l'injection SSR.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Stocke les épingles d'indicateurs du tableau de bord personnel : les widgets épinglés par l'utilisateur, leur ordre et leurs métadonnées d'affichage.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs est un dépôt dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry est un dépôt dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage est un dépôt dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards est une surface dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs est une surface dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry est une surface dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage est une surface dans le domaine analytics. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `analitycs`

## Automatisation et orchestration

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Intègre l'automatisation de la plateforme aux ressources Kubernetes via un client dédié et un contrat de service.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag est un dépôt dans le domaine automation. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `automation`, `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller est un dépôt dans le domaine automation. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `automation`

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks est un dépôt dans le domaine automation. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `automation`

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation est une surface dans le domaine automation. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `automation`

## Domaine métier

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `billing`

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [rp-events](/en/docs/modules/rp-events)

Fournit la création, le stockage et la récupération des événements métier.

- Dépendances directes : aucune
- Solutions : `production`

### [rp-finance](/en/docs/modules/rp-finance)

Fournit les opérations financières pour les transactions, les résumés de période, la trésorerie, les créances et les dettes.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-invoices](/en/docs/modules/rp-invoices)

rp-invoices est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `billing`

### [rp-metering](/en/docs/modules/rp-metering)

rp-metering est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `billing`

### [rp-orders](/en/docs/modules/rp-orders)

Fournit le contrat de service pour la création, la mise à jour, la liste et le suivi des commandes métier.

- Dépendances directes : aucune
- Solutions : `production`

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff est un dépôt dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [sf-equipment](/en/docs/modules/sf-equipment)

sf-equipment est une surface dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [sf-orders](/en/docs/modules/sf-orders)

Fournit l'interface commerciale pour les listes de commandes et de demandes, les détails des commandes, le filtrage par statut et les tableaux de bord opérationnels.

- Dépendances directes : aucune
- Solutions : `production`

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests est une surface dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [sf-reviews](/en/docs/modules/sf-reviews)

sf-reviews est une surface dans le domaine business. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

## Communications

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls est un dépôt dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats est un dépôt dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`

### [rp-community](/en/docs/modules/rp-community)

rp-community est un dépôt dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify est un dépôt dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [rp-resonus](/en/docs/modules/rp-resonus)

Fournit la configuration de communication pour les numéros de téléphone gérés et les paramètres de passerelle LLM.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-support](/en/docs/modules/rp-support)

rp-support est un dépôt dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads est un dépôt dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `ai`, `communications`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls est une surface dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats est une surface dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`

### [sf-community](/en/docs/modules/sf-community)

sf-community est une surface dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`

### [sf-support](/en/docs/modules/sf-support)

sf-support est une surface dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads est une surface dans le domaine communications. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `ai`, `communications`

## Contenu et documents

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier est un dépôt dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery est un dépôt dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown est un dépôt dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Fournit les opérations de stockage pour les fichiers de script, y compris la lecture, l'enregistrement, le hachage et la suppression.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-static](/en/docs/modules/rp-static)

Fournit le contrat de service pour le contenu statique et les métadonnées du cache SSR.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct est un dépôt dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Fournit l'interface du classificateur pour naviguer dans les entités, les mappages et les structures arborescentes.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs est une surface dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery est une surface dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing est une surface dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown est une surface dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-static](/en/docs/modules/sf-static)

Fournit l'interface d'exploitation pour inspecter et vider les entrées du cache SSR statique.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct est une surface dans le domaine content. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

## Fichiers et stockage

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors est un lambda dans le domaine data. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps est un dépôt dans le domaine data. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [rp-files](/en/docs/modules/rp-files)

rp-files est un dépôt dans le domaine data. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `communications`, `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store est un dépôt dans le domaine data. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps est une surface dans le domaine data. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [sf-files](/en/docs/modules/sf-files)

sf-files est une surface dans le domaine data. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

## Fournisseurs de distribution de messages

### [lm-lemonsqueezy](/en/docs/modules/lm-lemonsqueezy)

lm-lemonsqueezy est un lambda dans le domaine providers. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `billing`

### [lm-push](/en/docs/modules/lm-push)

lm-push est un lambda dans le domaine providers. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses est un lambda dans le domaine providers. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms est un lambda dans le domaine providers. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp est un lambda dans le domaine providers. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

## Conversion de modèles

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor est un lambda dans le domaine convertors. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

## Flux de travail

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Résume les dialogues de chat et d'appel non traités avec un LLM, puis stocke les titres, les descriptions et la classification du bruit.

- Dépendances directes : aucune
- Solutions : aucune

### [wf-equipment-incident](/en/docs/modules/wf-equipment-incident)

wf-equipment-incident est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analyse un fichier stocké non archivé, produisant des aperçus de modèle et des estimations CNC ou d'impression 3D lorsque c'est pris en charge.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Développe une archive téléchargée en une collection de fichiers stockés pour une analyse ultérieure.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Traite les fichiers téléchargés par lots : il développe les archives, identifie les fichiers de modèle et crée à partir d'eux une demande de fabrication.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-order-review-followup](/en/docs/modules/wf-order-review-followup)

wf-order-review-followup est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [wf-order-review-request](/en/docs/modules/wf-order-review-request)

wf-order-review-request est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [wf-payment-settle](/en/docs/modules/wf-payment-settle)

wf-payment-settle est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `billing`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `requests`

### [wf-request-to-order](/en/docs/modules/wf-request-to-order)

wf-request-to-order est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : aucune

### [wf-team-invite](/en/docs/modules/wf-team-invite)

wf-team-invite est un flux de travail dans le domaine platform. Son objet détaillé est conservé avec la source du module.

- Dépendances directes : aucune
- Solutions : `production`

## Dépendances des solutions

- `ai`: `security`
- `analitycs`: `security`
- `automation`: `security`
- `billing`: `security`
- `communications`: `security`
- `content`: `security`
- `production`: `security`, `analitycs`, `requests`
- `requests`: aucune dépendance de solution
- `security`: aucune dépendance de solution
