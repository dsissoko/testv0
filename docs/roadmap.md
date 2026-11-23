# World Data MCP — Roadmap

**Statut :** proposition de jalons; pas de version npm implicite.

| Jalon | Résultat utilisateur | Critère de sortie |
| --- | --- | --- |
| M1 — Fondations | Catalogue minimal et contrat sûr | Architecture, schéma, seed versionné, API et vérifications reproductibles |
| M2 — Portail | Sources consultables et administrables | Recherche publique, fiche source, auth admin, contrôle et publication |
| M3 — MCP local | Agent interroge une API publique | npx, stdio, catalogue distant, cache, appel fournisseur direct |
| M4 — Robustesse & distribution | MCP réutilisable sur plusieurs clients | Clés locales, mode dégradé, E2E, CI, SemVer, release npm autorisée |
| M5 — Enrichissement | Catalogue diversifié et vérifié | Gisements supplémentaires, contrôles récurrents, historique et observabilité |

## Ordre de livraison
Commencer par un **vertical slice** M1+M2+M3 : une source sans clé, du référentiel à l'agent, puis compléter les cas avec clé, indisponibilité et distribution.

## Gouvernance
GitHub issues = backlog opérationnel; PRs = unités d'implémentation; approbation explicite du merge et de la release. Avant développement, valider concurrence, Vercel Hobby/auth/cron, fournisseur initial et nom npm.
