## Technologies

La partie serveur de Converged est construite sur **Bun** et **Elysia**. Bun lance rapidement JavaScript et TypeScript, consomme la mémoire efficacement et convient aux déploiements edge compacts. Elysia sert de couche HTTP pour les plugins backend et les microservices.

Les contrats entre services sont décrits avec des types. NRPC relie les interfaces TypeScript aux implémentations et génère des packages clients, afin que frontend, Runtime et backend travaillent avec les mêmes contrats plutôt qu’avec des API textuelles dispersées.

Le stockage utilise un ensemble de stores légers selon les tâches : SQL, key-value, fichiers, données colonnes, index vectoriels et relations de graphe. La couche native Behemoth et les adaptateurs Zig couvrent les cas où le faible overhead, l’accès aux équipements, les sockets Unix ou le FFI sont importants.

Le frontend est une plateforme React avec micro-frontends. Le shell commun charge des modules UI séparés, et les scénarios produit peuvent évoluer indépendamment. C’est important pour une plateforme avec de nombreuses solutions : l’interface ne doit pas devenir un monolithe lourd.

L’orchestration et la livraison s’appuient sur k3s, Helm et des profils de configuration. Le même ensemble de composants peut être assemblé en profil mono compact ou séparé en groupes pour la production.
