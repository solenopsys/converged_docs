# Accès aux objets

## Deux couches, et non une seule

L’accès aux méthodes et l’accès aux objets répondent à des questions différentes,
et aucun ne remplace l’autre.

**Accès aux méthodes** — cet acteur peut-il appeler `rp/community/listTopics` ? Il
est défini dans l’arbre des permissions, émis par `rp-access` et appliqué par la
garde nrpc avant l’exécution du gestionnaire. Sans lui, n’importe qui peut
appeler `deleteTopic`.

**Accès aux objets** — quels sujets `listTopics` renvoie-t-il ? C’est l’objet de
ce document. Sans lui, un acteur autorisé à appeler `listTopics` reçoit tous les
sujets du magasin.

L’accès aux objets réutilise le transport d’accès aux méthodes au lieu d’ajouter
un deuxième système : une balise est une autorisation ordinaire sous le type
`tg`, transportée par le même JWT et émise par les mêmes appels.

## Le mécanisme

Deux éléments, tous deux locaux au service qui possède les données.

Une table par magasin, servant tous les types d’objets qu’il contient :

```sql
CREATE TABLE access_tags (
  objectId TEXT NOT NULL,
  tag      TEXT NOT NULL,
  PRIMARY KEY (tag, objectId)
);
CREATE INDEX access_tags_object ON access_tags (objectId);
```

Et les balises par lesquelles un acteur est mis en correspondance. Il n’y a pas
de colonne de type d’objet : la jointure avec la table propriétaire effectue ce
filtrage, puisqu’un identifiant appartenant à un autre type n’y est pas trouvé.

## Balises

**Balises de groupe** — `team-support`, `moderator`. Stockées par utilisateur
dans le magasin KV `access` de `rp-access`, à l’intérieur de l’arbre des
permissions existant sous la forme `tg/<tag>/*(mode)`, et transportées dans le
JWT. Accordées avec `addTagToUser`.

**La balise personnelle** — `u-<userId>`. Jamais stockée et jamais émise : elle
est dérivée du sujet du jeton, que tout jeton vérifié contient déjà. Un objet
ouvert à une personne est marqué avec la balise de cette personne ; une
autorisation individuelle ne coûte donc qu’une ligne et rien dans le jeton.

**Balises connues** — `public` (tout le monde, y compris les appelants anonymes)
et `authenticated` (tout acteur vérifié). La visibilité correspond à celle de
ces balises avec lesquelles un objet est écrit, et non à une colonne, ce qui
permet à chaque sélection de rester une recherche par balise.

Ainsi, propriété, partage individuel, accès de groupe et visibilité publique
forment un seul mécanisme avec quatre types de balises, et non quatre mécanismes.

## Sélection

Une sélection doit partir de la table des balises et effectuer une jointure avec
les objets. `visibleFrom` dans `back-core/access` s’en charge :

```ts
import { listVisible, visibleFrom } from "back-core";

const page = await listVisible<Topic>(this.store.db, "topics", { limit: 50 });

const custom = await visibleFrom(this.store.db, "topics")
  .selectAll("obj")
  .where("obj.status", "=", "open")
  .orderBy("obj.id")
  .limit(50)
  .execute();
```

La direction n’est pas une question de style. Écrite à plat —
`access_tags JOIN topics ... WHERE tag IN (...) ORDER BY topics.id` — SQLite
préfère parcourir la table des objets dans l’ordre de la clé primaire pour
satisfaire le tri. Sur une table d’un million de lignes dont dix sont visibles,
cela a mesuré **363 ms** pour une page de cinquante éléments. Avec la sous-requête
construite par `visibleFrom`, la même page a mesuré **0.28 ms**. Les deux
renvoient des résultats identiques, raison pour laquelle la forme fait l’objet
d’un test qui vérifie le plan de requête plutôt que la sortie.

Ne filtrez jamais après la requête, en dehors de la base de données, et ne placez
jamais les balises dans une colonne de liste vérifiée pour chaque ligne : dans
les deux cas, toute la table est lue.

`listVisible` renvoie `totalCount`, calculé avec le même filtrage que la page.
Compter sans ce filtrage révèle combien d’objets sont masqués.

## Attribution

```ts
const access = new AccessTags(this.store);

await access.tagNew(id, { owner: actorId, visibility: "private" });
await access.grantToUser(id, otherUserId);   // effective immediately
await access.revokeFromUser(id, otherUserId);
await access.dropObject(id);                 // on delete; a leftover row would
                                             // later match a reused id
await access.requireRead(id);                // throws AccessDeniedError
```

L’appartenance à un groupe passe plutôt par `rp-access`, puisqu’elle vit dans le
jeton :

```ts
await access.addTagToUser(userId, "team-support");
await access.removeTagFromUser(userId, "team-support");
await access.getTagsOfUser(userId);
```

## Exigences

**Les identifiants doivent être uniques entre les tables couvertes par les
balises.** Une séquence partagée, un UUID ou un préfixe de type — selon ce que
le magasin utilise déjà. Les entités qui ne sont pas couvertes par les balises
ne sont pas concernées ; il ne s’agit pas d’un passage global de la plateforme
aux UUID.

**Les identifiants doivent être générés par le serveur.** En l’absence de colonne
de type d’objet, un identifiant que l’appelant peut choisir correspond à un objet
auquel il peut accéder. Des identifiants fournis par le client existent
actuellement dans `rp-sales`, `rp-classifier` et `rp-chats` et doivent être
supprimés avant que ces dépôts adoptent les balises.

**Les identifiants monotones sont un avantage, pas une exigence.** Une séquence
partagée ou UUIDv7 donne directement l’ordre de création depuis l’index des
balises. UUIDv4 ne le fait pas, et c’est la seule conséquence — utilisez plutôt
un `orderBy` explicite.

**L’ordre des octets doit correspondre à la signification.** Une séquence
numérique conservée dans une colonne texte nécessite un remplissage avec des
zéros, sinon `"10"` est trié avant `"9"`.

**Aucun `:` ni `;` dans les identifiants ou les balises.** Ils correspondent à
`KEY_SEPARATOR` et `RANGE_END_SUFFIX` dans `back-core` ; un séparateur à
l’intérieur d’une clé la rend ambiguë dans les magasins KV. `addTagToUser` refuse
de telles balises.

**`NRPC_ACCESS_MODE` doit être `required`.** Lorsque la garde est désactivée,
l’utilisateur du contexte se rabat sur l’enveloppe, que l’appelant écrit — la
balise personnelle serait alors dérivée d’un identifiant fourni par le client.
Il vaut `required` dans `confs/dev` et `confs/prod` ; la valeur par défaut du
code est `off` pour les exécutions locales et les tests.

## Magasins non SQL

KV : la même structure que les clés dans le même magasin — `tag:<tag>:<objectId>`
en avant, `obj:<objectId>:<tag>` en inverse. La lecture d’une liste est un
parcours par préfixe pour chaque balise, puis une fusion avec suppression des
doublons. Une pagination fiable nécessite un curseur dans `kvList`, qui renvoie
actuellement toute une plage ; en attendant, les listes KV sont limitées par ce
qui tient en mémoire.

Fichiers et JSON (`JsonStore` étend `FileStore`) : aucun index de balises propre.
Le nom du fichier est l’identifiant de l’objet, et l’accès à celui-ci est l’accès
à l’enregistrement qui le référence, lequel se trouve dans un magasin SQL ou KV
du même service.

Graphe : une balise comme nœud, une autorisation comme arête, et un parcours
commençant par la balise.

## Limites acceptées

**La suppression d’une balise de groupe attend la réémission du jeton** —
`DEFAULT_TTL_SECONDS` vaut 90 jours. Les autorisations et révocations
individuelles sont immédiates, car la table est lue à chaque requête. Un accès
qui doit changer immédiatement utilise la balise personnelle, et non un groupe.

**Un `totalCount` exact** nécessite la jointure ; avec plusieurs balises qui se
recouvrent, le décompte porte sur les identifiants distincts, ce qui coûte plus
cher à mesure que l’ensemble visible augmente.

**Le tri par un champ autre que l’identifiant** est peu coûteux tant que peu
d’objets correspondent à une balise. Si une balise couvre un jour des centaines
de milliers d’objets, cet ordre devra être dénormalisé dans la table des balises
ou supprimé.
