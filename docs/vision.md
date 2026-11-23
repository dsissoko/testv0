# World Data MCP — Vision produit

**Statut :** cadrage V1, PR #1.

## Besoin
Permettre aux agents de découvrir, comprendre et interroger des données ouvertes ou accessibles par API sans multiplier les connecteurs spécifiques. Le produit référence la provenance, la licence, la couverture et la qualité observée.

## Livrables
- **Portail + API centrale** : catalogue public des 13 familles de gisements, fournisseurs, sources, ressources et contrats; administration protégée; vérifications et historique.
- **MCP npm local** : installation `npx -y <nom-package>`, stdio, découverte/description/interrogation, appels HTTPS directs aux fournisseurs, secrets et cache locaux.

## Invariants V1
- 13 gisements présents dès l'initialisation par CSV versionnés.
- Une famille peut être initialement sans source opérationnelle; l'enrichissement concerne les sources, ressources et connecteurs.
- Catalogue actualisé indépendamment des versions npm.
- Aucun compte central pour les fonctions publiques, aucun secret fournisseur envoyé au central.
- Exécution Windows/Linux/macOS sans Docker côté utilisateur.

## Premier parcours vérifiable
Catalogue CSV → import contrôlé → API et portail → recherche MCP → description de contrat → interrogation d'une source publique sans clé. Ensuite clé locale, cache, dégradation et publication npm contrôlée.

## Non-objectifs initiaux
Proxy des données, copie générale des datasets, marketplace payante, hébergement d'un MCP par utilisateur.

## Risques à arbitrer
Choix des sources pilotes, licence des données, solution d'authentification administrateur, planification et quotas Hobby, nom npm.
