# Faisabilité Vercel Hobby — 23 novembre 2026

## Authentification administrateur
- [Vercel changelog du 9 septembre 2026](https://vercel.com/changelog/protect-production-deployments-for-free-on-every-plan) : Vercel Authentication peut protéger **tous les déploiements**, production comprise, sur tous les plans. Les anciennes pages de documentation peuvent être contradictoires.
- Protéger **tout** le déploiement rendrait aussi le catalogue public inaccessible sans compte Vercel : ce n'est pas la solution d'authentification pour un portail public avec `/admin` privé.
- Prévoir une authentification applicative avec sessions sécurisées, vérification d'identité, allowlist/RBAC côté serveur et protection CSRF pour les écritures. Choix fournisseur d'identité à arbitrer; ne pas supposer qu'une simple URL /admin est privée.
- [Documentation Deployment Protection](https://vercel.com/docs/deployment-protection) ; [Vercel Authentication](https://vercel.com/docs/deployment-protection/methods-to-protect-deployments/vercel-authentication).

## Tâches quotidiennes
- [Changelog Vercel du 20 janvier 2026](https://vercel.com/changelog/cron-jobs-now-support-100-per-project-on-every-plan) : jusqu'à **100 cron jobs par projet** sur tous les plans.
- Sur Hobby, la fréquence minimale est quotidienne et l'heure d'exécution peut varier dans l'heure; planification UTC. Référence : [guide des limites Hobby](https://vercel.com/docs/cron-jobs/usage-and-pricing).
- Un cron déclenche une route de fonction, pas un worker permanent. Exécuter les vérifications en lots bornés, conserver curseur/état et rejouer les échecs; prévoir un secret de cron et un mécanisme anti-chevauchement.
- Les contrôles d'un grand nombre de sources ne doivent pas dépendre d'une seule fonction longue; vérifier limites effectives de durée, quotas, concurrence et coûts. Alternative à arbitrer : GitHub Actions planifié ou scheduler externe.

## Décisions du 23 novembre 2026
- **Retenu :** authentification applicative dédiée pour `/admin`, sans bloquer le catalogue public.
- **Retenu :** Vercel Cron Hobby pour les contrôles quotidiens, avec lots, état persistant, reprise et verrouillage.
- **À définir :** fournisseur d'identité/bibliothèque de session; seuils de lot, métriques et garde-fous selon les quotas réels.
- GitHub Actions/scheduler externe reste un plan de repli technique, **pas le choix actuel**.

## Conditions et décisions
- [Plan Hobby](https://vercel.com/docs/plans/hobby) : vérifier l'adéquation avec la nature et l'usage réel du projet avant déploiement (notamment conditions d'usage non commercial).
- Recommandation : Vercel pour portail/API, auth applicative dédiée; cron quotidien uniquement si le volume réel et les limites de fonctions le permettent. Un service de vérification séparé reste une option.
- Aucune configuration Vercel ni connexion Neon n'a été modifiée lors de cette étude.
