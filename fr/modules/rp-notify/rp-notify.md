# rp-notify

## Objectif

Le point unique de diffusion des notifications de l'écosystème : n'importe quel domaine dit « informer l'utilisateur » une seule fois, et ce module choisit les canaux, la politique et les tentatives. Les domaines ne touchent jamais directement aux API SMTP/SMS/push.

## Modèle mental

Le domaine émet une intention de notification (qui, quoi, modèle, urgence) → notify résout les canaux et la politique de distribution → les adaptateurs de fournisseurs externes effectuent l'envoi réel. Les tentatives et le repli de canal vivent ici, le sens du message vit dans le domaine.

## Valeur pour l'écosystème

Un unique référentiel « informer l'utilisateur » :

- Modèles, canaux, profil et enregistrements d'envoi derrière une seule API.
- Chaque domaine conserve ses textes de notification et ses enregistrements de distribution au même endroit.

## Non-objectifs

- Pas la distribution des messages elle-même — uniquement modèles, canaux et enregistrements d'envoi.
- Pas les fils de dialogue.

## Périmètre de responsabilité

Possède l'orchestration des notifications et la politique de distribution ; ne possède pas les adaptateurs d'envoi spécifiques aux fournisseurs de bas niveau ni la logique de déclenchement du domaine.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/communications/rp-notify`