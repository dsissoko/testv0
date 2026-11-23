# World Data MCP — Parcours et critères V1

**Statut :** cadrage corrigé.

## Acteurs
Visiteur public; client agentique; administrateur authentifié; opérateur de vérification planifiée.

## Parcours
1. Parcourir **les 13 gisements**, y compris ceux sans source; afficher le nombre de sources et l'état de couverture.
2. Explorer fournisseurs → sources → ressources et consulter provenance, licence, fraîcheur, contrats et derniers tests.
3. Installer `npx -y <package>`, déclarer le serveur stdio dans Claude Desktop ou OpenCode.
4. Exécuter `discover_sources`, `describe_source`, `query_source`; requête directe à l'API fournisseur.
5. Configurer une clé fournisseur localement; aucun secret vers l'API centrale.
6. Rafraîchir le catalogue sans mise à jour npm; consulter les métadonnées mises en cache lors d'une panne centrale.
7. Administrer une entrée, conserver les modifications manuelles lors d'un réimport CSV, vérifier puis publier une révision.

## Acceptation
- 13 catégories initialisées par CSV, relations valides, import répété sans doublon ni perte d'overrides.
- Contrats déclaratifs stricts, limites de durée/taille, destinations contrôlées, erreurs explicites.
- Test E2E sans clé, avec clé, offline, redémarrage, mise à jour de catalogue, deux clients MCP.
- Contrôles quotidiens horodatés, échecs visibles et rejouables; pas de garantie d'heure précise sur Hobby.
- API publique sans compte, admin protégé par authentification **et** autorisation serveur.
