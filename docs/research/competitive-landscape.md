# Étude comparative — World Data MCP (23 novembre 2026)

**Périmètre :** solutions vérifiables de découverte de données, fédération de sources et registres MCP. La comparaison porte sur les capacités documentées, pas sur une validation expérimentale.

| Solution | Couverture / proposition | Proximité avec World Data MCP | Limite/différence observée |
| --- | --- | --- | --- |
| [Data Commons](https://docs.datacommons.org/api/) | Graphe de connaissances et statistiques agrégées de nombreux fournisseurs, API REST | Forte sur fédération et interrogation de statistiques | Modèle harmonisé orienté statistiques; pas équivalent documenté à un catalogue général de contrats fournisseurs exécutés localement par un MCP |
| [Google Dataset Search](https://datasetsearch.research.google.com/) | Moteur de découverte de jeux de données | Forte sur découverte de datasets | Découverte ≠ exécution contractuelle générique des APIs fournisseurs |
| [OpenDataSoft](https://help.opendatasoft.com/apis/ods-search-v2/) | Portails, catalogues et API de recherche/exposition de datasets | Forte sur catalogage/API | Plateforme de publication/gestion de données; architecture distincte du MCP npm local |
| [CKAN](https://docs.ckan.org/en/latest/api/) | Catalogue open source, métadonnées et API | Forte sur catalogue et API | Pas de moteur MCP universel d'exécution directe des contrats par défaut |
| [OpenAlex](https://docs.openalex.org/) | Catalogue/API de travaux et entités scientifiques | Fournisseur/source candidat | Domaine scientifique spécialisé |
| [Wikidata](https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service) | Graphe de connaissances interrogeable en SPARQL | Source et langage d'accès candidat | Domaine graphe, non catalogue de connecteurs universel |
| [MCP Registry officiel](https://github.com/modelcontextprotocol/registry/blob/main/docs/modelcontextprotocol-io/about.mdx) | Registre de métadonnées de serveurs MCP et installations | Fort sur découverte de serveurs MCP | Répertorie des **serveurs**, pas directement un catalogue de ressources et contrats d'APIs fournisseurs |

## Positionnement proposé
**Différenciation à vérifier par prototype :** catalogue transversal de 13 familles, structuré en gisement/fournisseur/source/ressource, contrats déclaratifs vérifiés et versionnés, serveur MCP local universel installable via npx, appels directs aux fournisseurs et secrets conservés localement. Ne pas prétendre qu'aucun concurrent n'offre une combinaison similaire sans enquête exhaustive.

## Opportunités d'interopérabilité
- Import de métadonnées standardisées : [DCAT 3 (W3C)](https://www.w3.org/TR/vocab-dcat-3/), schema.org/Dataset.
- Contrats d'API : [OpenAPI](https://spec.openapis.org/oas/latest.html), SPARQL, REST/GraphQL selon source.
- Conformité : [Model Context Protocol](https://modelcontextprotocol.io/specification/).
- Publication du MCP dans le registre officiel après stabilisation.

## Risques et validations à mener
Licences de métadonnées et quotas; API à clé; source non interrogeable sans adaptation; couverture initiale des 13 familles sans promettre 13 connecteurs. L'étude est documentaire, pas un benchmark technique mesuré.
