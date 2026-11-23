# World Data MCP — Vision produit

**Statut :** cadrage initial, à valider en PR.

## Problème et utilisateurs
Les agents ont besoin d'accéder à des sources de données fiables, hétérogènes et évolutives. Leurs utilisateurs doivent aujourd'hui découvrir les APIs, comprendre leurs contrats, configurer des connecteurs et surveiller leur disponibilité.

## Promesse
Un catalogue public de gisements et sources, maintenu et contrôlé régulièrement, accessible sur un portail et par un serveur MCP local universel. Les données sont interrogées **directement chez les fournisseurs**, sans transit par notre service.

## Deux livrables
1. **Portail et API centrale** : explorer les gisements/sources, consulter la documentation, l'état des tests et les contrats; espace d'administration protégé pour gérer le catalogue.
2. **Package MCP npm public** : démarrage par `npx -y <package>`, transport stdio, clients Claude Desktop/OpenCode, catalogue distant mis en cache, appels directs aux APIs fournisseurs.

## Principes
- Lecture publique sans compte World Data MCP; administration authentifiée.
- Secrets fournisseurs locaux, jamais transmis à l'API centrale.
- Catalogue mis à jour indépendamment des versions du package.
- Vérifications de disponibilité et de contrats horodatées; ne pas confondre test réussi et garantie de disponibilité.
- Source ouverte, installation Windows/Linux/macOS, pas de Docker requis côté utilisateur.

## Hors périmètre initial
Proxy des réponses fournisseurs, stockage des secrets des utilisateurs, hébergement d'un MCP individuel par utilisateur, paiement, garanties de disponibilité des fournisseurs.

## Premier résultat observable
Depuis un client MCP, rechercher une source du catalogue et interroger une API publique sans clé; le portail montre la même source et son dernier état vérifié. Puis démontrer clé locale et mode dégradé.

## Questions ouvertes
Nom npm disponible; choix de fournisseurs initiaux et licences; cadence/quotas des contrôles; hébergement et authentification admin Vercel Hobby à confirmer; concurrence à documenter.
