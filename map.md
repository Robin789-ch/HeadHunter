Label: wayfinder:map

# Concevoir le workflow agentique de recherche d'emploi

## Destination

Produire une spécification complète, cohérente et prête à être implémentée d'un système personnel agentique qui construit un profil professionnel fidèle, recherche quotidiennement des opportunités et prépare des candidatures ciblées avec validation humaine.

## Notes

- Domaine personnel et local-first, piloté par Codex dans un workspace dédié; le service cloud autonome est écarté.
- Consulter `grilling` et `domain-modeling` pour chaque décision HITL; employer `research` et `prototype` selon le type du ticket.
- La recherche et le classement quotidiens sont automatiques; toute préparation, tout envoi et toute prise de contact exigent une décision humaine explicite.
- Typst produit tous les CV et lettres rendus; les données structurées, l'orchestration et le suivi vivent hors de Typst.
- Le profil accepte les compétences documentées ainsi que les compétences autodidactes déclarées et confirmées; une compétence seulement déduite ne peut jamais alimenter une candidature.
- L'onboarding commence par un grilling approfondi. Le profil reste progressif grâce aux entretiens ciblés au passage « Retenue/Postuler »; un bilan de recherche mensuel distinct aide à réorienter une recherche difficile ou infructueuse vers d'autres solutions menant à un emploi satisfaisant.
- Le brief quotidien vise 5 à 10 offres dédupliquées, sélectionnées et expliquées sans classement; il peut en contenir moins ou davantage selon les résultats, qui arrivent dans Nouveau avec les actions Ignorer, En réserve, Retenue et Postuler.
- Postuler lance la préparation d'un dossier complet avec destination vérifiée; l'utilisateur est notifié lorsqu'il est prêt, l'envoie lui-même et confirme l'envoi avant son passage au dashboard de suivi et au calendrier des relances.
- Une interface web strictement locale fournit un tableau Kanban pour trier les offres et un dashboard distinct pour suivre les candidatures engagées.
- Un profil professionnel unique peut servir plusieurs pistes de recherche distinctes.
- L'email d'accompagnement et l'approche spontanée sont deux parcours distincts.
- Le suivi couvre la candidature jusqu'à son résultat et peut proposer des apprentissages sans modifier silencieusement le profil.
- Garder le workflow simple: les documents personnels restent gérés par l'utilisateur; l'agent gère les données structurées et les artefacts qu'il génère.

## Decisions so far

- [Établir les capacités et contraintes des automations Codex](issues/02-rechercher-contraintes-automations-codex.md) — Retenir un daily local autonome, idempotent et limité au workspace; il dépend de la machine et ne doit ni envoyer ni postuler sans surveillance.
- [Établir les capacités et contraintes de Typst pour les candidatures](issues/03-rechercher-capacites-typst.md) — Utiliser Typst comme couche de rendu de snapshots JSON validés, avec environnement figé, contrôles automatiques, aperçus et validation humaine.
- [Définir le modèle canonique du profil professionnel](issues/01-definir-modele-profil-professionnel.md) — Retenir un profil compact d'affirmations actuelles, enrichi à la demande et modifié uniquement par des propositions validées, avec parcours et compétences ouverts mais traçables.
- [Définir les pistes de recherche et le contrat de triage](issues/04-definir-pistes-recherche-triage.md) — Une piste active réunit une intention même large, un périmètre et des critères explicites; les offres dédupliquées passent de Nouveau à Ignorer, En réserve, Retenue ou Postuler, sans envoi par l'agent.
- [Définir les frontières de confidentialité, consentement et rétention](issues/05-definir-securite-confidentialite.md) — Retenir un traitement local-first sous consentement contextuel, avec identité et informations protégées séparées, documents personnels hors workflow et rétentions courtes pour les opportunités et candidatures.
- [Concevoir le grilling initial du profil](issues/06-concevoir-grilling-initial.md) — Imposer avant toute recherche un entretien reprenable, nourri de documents facultatifs consultés sans copie, validé par petits lots jusqu'à un socle fidèle et une première piste activable.
- [Définir les règles du profiling continu](issues/07-definir-profiling-continu.md) — Faire évoluer le profil seulement à partir d'événements concrets et de validations humaines, au moyen d'entretiens ciblés adaptatifs, tout en séparant le bilan mensuel de la recherche.

## Not yet specified

- Les connecteurs et méthodes d'acquisition précis ne pourront être choisis qu'après définition des marchés visés, des sources acceptables et des contraintes d'authentification.
- Les variantes visuelles, linguistiques et sectorielles des modèles Typst dépendront du contrat de génération des documents.
- Les jeux d'essai, métriques d'évaluation et critères d'acceptation de bout en bout dépendront des décisions de classement, de génération et de suivi.

## Out of scope

- Implémenter, déployer ou exploiter le workflow dans le cadre de cette carte.
- Envoyer automatiquement une candidature, un email ou une approche spontanée.
- Inventer, embellir ou utiliser une compétence non confirmée.
- Construire un service cloud autonome ou un produit multi-utilisateur.
- Héberger publiquement l'interface web ou permettre un accès distant lorsque l'ordinateur local est indisponible.
