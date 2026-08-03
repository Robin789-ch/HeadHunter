# Recherche d'emploi agentique

Ce contexte décrit le langage partagé du système qui construit un profil professionnel fidèle et l'utilise pour préparer des candidatures ciblées.

## Language

**Profil professionnel**:
Vue canonique compacte et actuelle des expériences, compétences et contraintes personnelles globales qui décrivent fidèlement la personne, indépendamment d'une recherche particulière. Ses détails et preuves sont consultés à la demande.
_Avoid_: Profil définitif, profil complet

**Présentation professionnelle**:
Vue narrative dérivée du profil professionnel pour un usage donné, sans devenir elle-même une source de vérité canonique.
_Avoid_: Biographie canonique, résumé dupliqué

**Profil psychologique et comportemental**:
Section distincte du profil consacrée aux traits de fonctionnement et compétences comportementales confirmés, utilisable pour le rapprochement et les présentations narratives sans constituer un diagnostic psychologique.
_Avoid_: Diagnostic psychologique, personnalité déduite

**Identité de candidature**:
Ensemble minimal des données d'identité et de contact nécessaires aux documents et échanges approuvés, tenu hors du profil professionnel utilisé pour le raisonnement.
_Avoid_: Identité chargée par défaut, coordonnées dans le profil

**Proposition de profil**:
Modification sémantique temporaire suggérée par l'agent ou issue d'un import, tenue hors du profil professionnel jusqu'à ce que la personne l'accepte, la corrige ou la refuse.
_Avoid_: Mise à jour silencieuse

**Mémoire de refus**:
Trace minimale d'une proposition de profil rejetée et de son éventuelle clarification, consultée uniquement avant de produire ou d'approfondir une nouvelle proposition afin d'éviter de répéter la suggestion ou la question.
_Avoid_: Affirmation négative dans le profil, historique de conversation

**Affirmation professionnelle**:
Énoncé atomique sur le parcours ou les aptitudes de la personne, conservé dans son état courant et relié, lorsque nécessaire, à sa provenance, à ses preuves et à sa validation.
_Avoid_: Historique exhaustif, métadonnées systématiques

**Admissibilité à la candidature**:
Propriété d'une affirmation professionnelle dérivée séparément de son origine, de sa validation humaine, de ses preuves et de sa validité temporelle. Une affirmation seulement déduite ou rejetée n'est jamais admissible.
_Avoid_: Niveau de confiance unique, score de vérité

**Provenance d'affirmation**:
Trace minimale de l'acquisition d'une affirmation professionnelle : mode d'acquisition, date et, lorsqu'il existe, pointeur vers le document ou l'entretien d'origine.
_Avoid_: Dossier documentaire dupliqué

**Preuve professionnelle**:
Élément précis qui étaye ou contredit une affirmation professionnelle, comme un passage, un artefact, un résultat mesuré ou un exemple concret confirmé.
_Avoid_: Source entière non localisée

**Temporalité professionnelle**:
Date ou période, éventuellement partielle ou approximative, portée uniquement par un fait dont le sens dépend du temps.
_Avoid_: Horodatage systématique, fausse précision

**Élément de parcours**:
Activité significative du parcours — emploi, mission, projet, formation ou autre — caractérisée par plusieurs facettes cumulables plutôt que rangée dans une catégorie unique et fermée.
_Avoid_: Type de parcours fermé, catégorie unique

**Facette de parcours**:
Caractéristique cumulable d'un élément de parcours, exprimée par un axe structuré ou par un qualificatif extensible confirmé par la personne.
_Avoid_: Type exclusif, étiquette imposée

**Contribution professionnelle**:
Affirmation professionnelle atomique décrivant une responsabilité, une action ou un résultat de la personne, reliée aux éléments de parcours, compétences, parties concernées et preuves qui la contextualisent.
_Avoid_: Puce de CV, description d'emploi copiée

**Écart de profil**:
Compétence utile à une offre, absente du profil professionnel mais plausible au regard des éléments déjà confirmés.

**Entretien ciblé**:
Courte séquence de questions déclenchée après qu'une offre a été marquée comme intéressante, afin de confirmer ou d'écarter un écart de profil avant de préparer la candidature.
_Avoid_: Interrogatoire automatique, micro-profiling

**Piste de recherche**:
Mandat de recherche cohérent et indépendant réunissant une famille de rôles et ses cibles, préférences, contraintes contextuelles et critères éliminatoires propres. Plusieurs pistes partagent le même profil professionnel sans partager leurs critères.
_Avoid_: Recherche globale, profil de recherche

**Brief quotidien**:
Sélection dédupliquée de nouvelles offres classées et expliquées, présentée pour décision humaine sans préparer automatiquement une candidature.
_Avoid_: Liste exhaustive, flux d'offres

**Offre**:
Opportunité d'emploi découverte et soumise au triage, qu'elle mène ou non à une candidature.
_Avoid_: Proposition, candidature

**Candidature**:
Démarche engagée après décision de postuler à une offre, suivie jusqu'à son résultat final.
_Avoid_: Offre acceptée, proposition acceptée

**Tableau de triage**:
Vue Kanban locale où les offres passent entre les décisions Ignorer, À surveiller, Intéressé et Postuler.

**Tableau de suivi**:
Vue locale qui synthétise l'état, les échéances, les relances et les résultats des candidatures engagées.
_Avoid_: Tableau de triage

**Email d'accompagnement**:
Message lié à une offre précise et destiné à accompagner une candidature.

**Approche spontanée**:
Prise de contact personnalisée avec une entreprise ou une personne en l'absence d'une offre précise.
_Avoid_: Email d'accompagnement

**Compétence**:
Savoir, savoir-faire, pratique, outil, technologie ou connaissance métier dont la pertinence dépend de ses contextes d'exercice et de ses relations avec d'autres compétences.
_Avoid_: Mot-clé isolé, score global de maîtrise, taxonomie fermée

**Relation de compétence**:
Lien extensible qui contextualise ou rapproche des compétences sans transférer à la personne la possession d'une compétence vers une autre.
_Avoid_: Héritage automatique de compétence

**Compétence documentée**:
Compétence étayée par une expérience, une formation, un projet, un portfolio ou un autre artefact consultable.

**Compétence déclarée et confirmée**:
Compétence, notamment autodidacte, déclarée par la personne puis confirmée durant l'entretien à l'aide d'exemples concrets, même sans justificatif formel.

**Compétence déduite**:
Compétence suggérée par l'agent à partir du parcours, mais pas encore confirmée par la personne; elle ne peut pas être utilisée dans une candidature.
