## Performance

Converged est conçu pour des sites de production qui ne disposent pas toujours d’un grand parc serveur. Le système évite donc le poids inutile : Bun réduit l’overhead des processus backend, Runtime reste stateless, et les microservices peuvent être groupés par type de charge au lieu de lancer des centaines de conteneurs séparés.

La performance vient de l’architecture, pas d’une seule astuce. Les données ne traversent pas de couches inutiles, les services possèdent leurs stores, Runtime parallélise les workflows et tâches cron, et les adaptateurs natifs sont utilisés là où HTTP ou une couche JS classique ajouterait trop d’overhead.

Une installation compacte peut fonctionner sur un petit serveur ou un single-board computer si la charge correspond à l’échelle de l’atelier. En grandissant, on peut séparer Runtime, microservices et groupes de storage pour utiliser plus de cœurs CPU, isoler les tâches lourdes et éviter qu’un goulot d’étranglement arrête tout le système.

La plateforme ne promet pas une performance infinie « out of the box ». Les goulots dépendent des équipements, du volume de fichiers, du nombre de commandes, des fournisseurs IA et des intégrations. L’architecture de Converged permet de commencer compact et de scaler uniquement les parties qui deviennent réellement chaudes.
