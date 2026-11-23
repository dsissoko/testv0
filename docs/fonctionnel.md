# World Data MCP — Spécification fonctionnelle

**Statut :** cadrage MVP.

## Acteurs
- **Visiteur** : parcourt et recherche les sources publiques sans compte.
- **Agent/client MCP** : découvre les outils/sources et exécute des requêtes via le processus local.
- **Administrateur** : authentifié, édite les gisements, contrats, publications et lance des vérifications.
- **Planificateur** : contrôle périodiquement les sources et conserve les résultats.

## Parcours prioritaires
1. Visiter le portail, filtrer par gisement, ouvrir une source et consulter endpoint, provenance, auth, dernière vérification et limites.
2. Installer le MCP avec `npx`, déclarer stdio dans Claude Desktop/OpenCode, rechercher une source et effectuer un appel direct à une API publique.
3. Fournir localement une clé API fournisseur, interroger la source sans envoyer le secret au service central.
4. Redémarrer après mise à jour du catalogue; récupérer la nouvelle révision sans réinstaller npm.
5. Couper temporairement l'API centrale; consulter les métadonnées du dernier catalogue validé, avec avertissement sur leur ancienneté.
6. Administrer un gisement, vérifier un contrat puis publier une révision; la validation et la publication sont distinctes.

## Critères MVP
- Portail et MCP présentent des identifiants de source cohérents.
- Réponses bornées, timeouts, erreurs explicites et cache avec TTL.
- Contrats validés avant exécution; domaine de destination contrôlé, protection SSRF/redirections.
- Tests bout en bout pour une source sans clé, une source avec clé locale et le mode hors ligne.
- Instructions prêtes à copier pour Claude Desktop et OpenCode, installation et désinstallation.
