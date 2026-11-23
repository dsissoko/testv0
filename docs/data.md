# World Data MCP — Référentiel CSV et données administrées

**Statut :** spécification initiale, aucune migration exécutée.

## Source de vérité de l'initialisation
Les CSV UTF-8, en-tête obligatoire, séparateur virgule, valeurs vides explicites, sont versionnés sous `data/reference/v1/`. **Pas d'initialisation à partir de données codées en dur ou d'un seed SQL divergent.**

| CSV | Colonnes requises | Clé et relations |
| --- | --- | --- |
| `gisements.csv` | `gisement_id,slug,name,description,status` | PK `gisement_id`, slug unique; exactement les 13 familles V1 |
| `providers.csv` | `provider_id,name,homepage_url,country_code,status` | PK `provider_id` |
| `sources.csv` | `source_id,provider_id,name,description,homepage_url,access_type,status` | PK `source_id`; FK `provider_id` |
| `source_gisements.csv` | `source_id,gisement_id` | PK composite; deux FK |
| `resources.csv` | `resource_id,source_id,name,resource_type,description,landing_url,status` | PK `resource_id`; FK `source_id` |
| `contracts.csv` | `contract_id,source_id,resource_id,schema_version,contract_path,status` | PK `contract_id`; FK source; FK ressource optionnelle et cohérente avec la source |
| `provenance.csv` | `resource_id,origin_url,license_id,observed_at,coverage,limitations` | FK ressource, unicité définie par ressource+origine |

Les contrats détaillés sont des JSON déclaratifs versionnés sous `data/reference/v1/contracts/`, référencés par `contract_path`; leur **inventaire et leurs relations sont exclusivement définis par les CSV**. Le format de contrat possède un `schemaVersion` indépendant du SemVer npm. Les CSV contiennent des identifiants stables, jamais des secrets.

## Validation déterministe
1. Parser strict (encodage, colonnes, valeurs, unicité, types, dates ISO, URL HTTPS).
2. Vérifier exactement 13 gisements, clés étrangères, cohérence source/ressource/contrat et absence de cycles ou doublons.
3. Valider JSON Schema des contrats, destinations autorisées, absence de code exécutable, politique SSRF/redirections.
4. Générer un rapport de diff et une empreinte SHA-256 du jeu; bloquer la publication si erreur.
5. Exécuter les tests de contrat et enregistrer leur résultat; un contrat non vérifié reste non publié.

## Import idempotent et protection des données
- Import `--dry-run` par défaut, `--apply` explicite, transaction atomique, upsert sur clés métier stables.
- Conserver un `reference_revision`, hash, date et compteurs d'insertion/modification/ignorés.
- Réimporter deux fois en QA : seconde exécution = zéro mutation.
- Séparer tables/champs **référentiel géré par Git**, **overrides administrateur** et **historique opérationnel**. Le rendu effectif applique des overrides explicites sans modifier les CSV.
- Pas de suppression implicite d'entrées absentes : signaler les suppressions proposées; retrait/archivage via procédure approuvée.
- Pas d'écrasement d'overrides, de vérifications, d'audits ou de données utilisateur; conflits signalés.
- En production : vérifier environnement, backup, approbation, migration compatible, puis comparer l'état réel après import.
- Préviews Neon isolées et sans données sensibles de production.

## Initialisation
`db:status`, `db:init`, `db:migrate`, `db:import`, `db:check` devront être implémentés et testés avant usage; aucune de ces commandes n'existe encore.
