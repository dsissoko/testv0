# ADR-0001 — Fondations validées de World Data MCP V1

- **Date :** 2026-11-23
- **Statut :** accepté (arbitrage utilisateur)
- **Contexte :** revue du cadrage de la PR #1, clarification du modèle métier, initialisation CSV et contraintes d'exploitation.

## Décisions
1. **Taxonomie :** les 13 gisements de `data/reference/v1/gisements.csv` sont approuvés dès la V1; l'enrichissement ultérieur concerne sources, ressources et connecteurs.
2. **Authentification :** l'espace administrateur utilise une authentification **applicative**, avec vérification de session et autorisation côté serveur. La protection globale Vercel ne doit pas rendre le catalogue public privé.
3. **Planification :** les contrôles quotidiens utilisent **Vercel Cron Hobby** avec traitement par lots, état persistant, anti-chevauchement, reprise et respect des quotas. Une heure exacte n'est pas garantie.
4. **Fournisseur pilote :** **World Bank API**, API publique sans clé, pour le premier parcours CSV → API catalogue → MCP local → API fournisseur directe.

## Conséquences
- Documenter et tester la source et la ressource World Bank précises avant implémentation.
- Ne pas confondre choix d'authentification applicative et sélection d'un fournisseur d'identité : ce dernier reste ouvert.
- Garder GitHub Actions/scheduler externe comme plan de repli si les limites Hobby sont incompatibles avec la charge réelle.
- Ne pas modifier le template agentique, ne pas fusionner la PR #1 ni implémenter l'application sans autorisation distincte.

## Références
- [PR #1](https://github.com/dsissoko/testv0/pull/1)
- [Backlog #2–#8](https://github.com/dsissoko/testv0/issues)
- [Vercel Hobby](../research/vercel-hobby.md)
- [Modèle métier](../metier.md)
