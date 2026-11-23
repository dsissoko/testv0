# Journal d'évaluation de v0 — World Data MCP

**Date :** 2026-11-23. **Agent :** ChatGPT GPT-6. **Support :** GitHub connector. **Cas :** initialisation d'un projet à partir du template agentique v0.

Ce fichier est un **journal de projet** ajouté sur la branche de PR #1. Il ne modifie ni `AGENTS.md`, ni les skills, ni le template d'évaluation existant.

| Écart constaté en relecture | Origine probable | Mesure corrective | Statut |
| --- | --- | --- | --- |
| Gisement confondu avec organisation | Modélisation prématurée à partir d'exemples INSEE/Eurostat; skill product non appliqué assez rigoureusement au vocabulaire | Quatre concepts et cardinalités distincts | Corrigé dans la PR |
| Initialisation CSV non obligatoire | Exigence de reproductibilité réduite à une proposition de fichiers CSV/JSON | Contrat CSV obligatoire, structure, clés, validation, upsert et overrides | Corrigé dans la PR |
| 13 familles absentes du périmètre V1 | Optimisation excessive vers un MVP vertical à une seule source | 13 gisements initiaux; distinguer taxonomie et connecteurs | Corrigé dans la PR |
| Étude de marché et Hobby différées | Séquencement trop rapide de l'implémentation; vérification documentaire non réalisée | Étude comparative sourcée et note Hobby | Documenté, validation opérationnelle à venir |
| Roadmap partiellement incohérente | Propagation incomplète des contraintes entre vision/métier/data/roadmap | Réalignement des six documents | Corrigé dans la PR |
| Absence de journal des écarts | Évaluation v0 non déclenchée à la première PR | Journal spécifique au projet, sans altérer le template | Ajouté |

## Observations sur le template
Le template **contient** les garde-fous nécessaires (vocabulaire métier avant schéma, data déterministe, sources d'autorité GitHub, phases d'approbation). Les écarts proviennent probablement de leur **application incomplète par l'agent**, non d'une absence de règles. Ne pas modifier le template sur la base de cette seule exécution.

## Vérification et limites
Évaluation qualitative sur une exécution; aucune mesure comparative inter-agents, aucun test d'application ni import Neon effectué. La correction documentaire doit être relue avant validation. Voir [scénarios d'acceptation v0](agent-evaluation.md).
