# World Data MCP — Roadmap corrigée

**Statut :** proposition V1; jalons distincts du SemVer npm.

| Jalon | Résultat | Sortie vérifiable |
| --- | --- | --- |
| M1 — Catalogue V1 | Les 13 gisements existent dès l'initialisation | CSV versionnés, clés/relations, validations, import idempotent et protection des overrides |
| M2 — Service central | Catalogue public consultable et administrable | API, portail, auth admin, provenance, contrats et vérifications horodatées |
| M3 — MCP local | Agent interroge directement un fournisseur | npm/npx, stdio, découverte, contrat validé, API publique sans clé |
| M4 — Distribution fiable | Usage multi-client reproductible | clé locale, cache hors ligne, tests E2E, compatibilité, releases autorisées, npm OIDC |
| M5 — Enrichissement | Sources et connecteurs étendus dans les 13 familles | nouveaux fournisseurs/ressources/contrats, couverture et qualité mesurées |

## Tranche verticale prioritaire
Dès M1, créer les **13 familles approuvées**; valider en parallèle **World Bank API** comme première source publique sans clé de bout en bout (CSV → Neon → API → MCP). L'authentification de l'administration sera **applicative** et les contrôles quotidiens seront orchestrés par **Vercel Cron Hobby** (lots, reprise, limites documentées). Ne pas confondre couverture taxonomique et couverture opérationnelle.

## Gouvernance
Backlog GitHub, issues avec critères vérifiables, PR par lot cohérent, pas de merge ni release sans approbation. Étude concurrentielle et contraintes Hobby à documenter avant choix final de l'architecture.
