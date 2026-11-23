# World Data MCP — Gestion des données

**Statut :** contrat initial, aucune migration appliquée.

## Classes de données
1. **Schéma** : migrations SQL ordonnées, versionnées et non destructives par défaut.
2. **Référentiel** : gisements et sources initiales en fichiers versionnés (CSV ou JSON), clés métier stables, provenance et licence.
3. **Fixtures preview** : jeux de test isolés, jamais importés en production.
4. **Données d'exploitation** : vérifications horodatées, publications et journal d'administration, non écrasées par import.

## Entités envisagées
`gisement`, `source`, `access_contract`, `verification_run`, `catalog_revision`, `catalog_entry`, `audit_event`.

## Contrat d'import
Validation structurelle déterministe; dry-run, détection des différences, upsert idempotent, transaction, journal de provenance, vérification des contraintes et réexécution sans doublons. Pas de réinitialisation silencieuse.

## Contrats publics
Schéma JSON versionné, validation stricte, champs obligatoires d'endpoint/paramètres/auth, aucun secret et aucun script arbitraire. Publier seulement des révisions validées.

## Environnements
Neon production séparé des branches PR; previews avec schéma et fixtures approuvées, pas de données sensibles copiées. Aucun provisionnement ou import production sans autorisation.
