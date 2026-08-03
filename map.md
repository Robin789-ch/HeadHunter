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
- L'onboarding commence par un grilling approfondi. Le profil reste progressif: entretien ciblé au passage « Intéressé/Postuler » et proposition mensuelle d'entretien général.
- Le brief quotidien contient 5 à 10 nouvelles offres dédupliquées, classées et expliquées, avec les actions Ignorer, À surveiller, Intéressé et Postuler.
- Une interface web strictement locale fournit un tableau Kanban pour trier les offres et un dashboard distinct pour suivre les candidatures engagées.
- Un profil professionnel unique peut servir plusieurs pistes de recherche distinctes.
- L'email d'accompagnement et l'approche spontanée sont deux parcours distincts.
- Le suivi couvre la candidature jusqu'à son résultat et peut proposer des apprentissages sans modifier silencieusement le profil.

## Decisions so far

- [Établir les capacités et contraintes des automations Codex](issues/02-rechercher-contraintes-automations-codex.md) — Retenir un daily local autonome, idempotent et limité au workspace; il dépend de la machine et ne doit ni envoyer ni postuler sans surveillance.
- [Établir les capacités et contraintes de Typst pour les candidatures](issues/03-rechercher-capacites-typst.md) — Utiliser Typst comme couche de rendu de snapshots JSON validés, avec environnement figé, contrôles automatiques, aperçus et validation humaine.
- [Définir le modèle canonique du profil professionnel](issues/01-definir-modele-profil-professionnel.md) — Retenir un profil compact d'affirmations actuelles, enrichi à la demande et modifié uniquement par des propositions validées, avec parcours et compétences ouverts mais traçables.

## Not yet specified

- Les connecteurs et méthodes d'acquisition précis ne pourront être choisis qu'après définition des marchés visés, des sources acceptables et des contraintes d'authentification.
- Le schéma physique, les formats de fichiers et la structure exacte du workspace dépendront du modèle d'information et des décisions de sécurité.
- Les variantes visuelles, linguistiques et sectorielles des modèles Typst dépendront du contrat de génération des documents.
- Les jeux d'essai, métriques d'évaluation et critères d'acceptation de bout en bout dépendront des décisions de classement, de génération et de suivi.

## Out of scope

- Implémenter, déployer ou exploiter le workflow dans le cadre de cette carte.
- Envoyer automatiquement une candidature, un email ou une approche spontanée.
- Inventer, embellir ou utiliser une compétence non confirmée.
- Construire un service cloud autonome ou un produit multi-utilisateur.
- Héberger publiquement l'interface web ou permettre un accès distant lorsque l'ordinateur local est indisponible.
