# Recherche d'emploi agentique

Ce contexte décrit le langage partagé du système qui construit un profil professionnel fidèle et l'utilise pour préparer des candidatures ciblées.

## Language

**Profil professionnel**:
Référentiel structuré canonique, compact et actuel des expériences, compétences et contraintes personnelles globales qui décrivent fidèlement la personne, indépendamment d'une recherche particulière. Maintenu par l'agent à partir d'informations confirmées, il relie les détails, preuves et documents professionnels sources utiles sans copier ces documents ni conserver la transcription brute des entretiens.
_Avoid_: Profil définitif, profil complet, copie des documents sources, transcription d'entretien

**Grilling initial**:
Entretien obligatoire, reprenable et sans relance automatique qui précède le démarrage de la recherche quotidienne. À partir des documents professionnels facultativement désignés et d'un questionnement adaptatif, il construit et fait valider le socle du profil professionnel, puis aide la personne à faire émerger au moins une piste activable. Il s'achève par une confirmation explicite que le profil est assez fidèle pour commencer, sans prétendre être exhaustif.
_Avoid_: Profilage facultatif après démarrage, simple formulaire d'inscription, profil exhaustif

**Présentation professionnelle**:
Vue narrative dérivée du profil professionnel pour un usage donné, sans devenir elle-même une source de vérité canonique.
_Avoid_: Biographie canonique, résumé dupliqué

**Profil psychologique et comportemental**:
Section distincte du profil consacrée aux traits de fonctionnement et compétences comportementales confirmés, utilisable pour le rapprochement et les présentations narratives sans constituer un diagnostic psychologique.
_Avoid_: Diagnostic psychologique, personnalité déduite

**Identité de candidature**:
Ensemble minimal des données d'identité et de contact nécessaires aux documents et échanges approuvés, tenu hors du profil professionnel utilisé pour le raisonnement. Elle n'est mobilisée qu'après une action humaine explicite liée à une candidature précise.
_Avoid_: Identité chargée par défaut, coordonnées dans le profil

**Information personnelle protégée**:
Information personnelle exclue du profil professionnel parce qu'elle est sensible ou inutile au raisonnement courant. Elle n'est conservée séparément que si la personne la fournit volontairement pour un besoin professionnel précis, sans jamais être déduite ni servir de signal général de rapprochement.
_Avoid_: Attribut sensible du profil, donnée personnelle déduite

**Proposition de profil**:
Modification sémantique temporaire suggérée par l'agent ou issue d'un import, tenue hors du profil professionnel jusqu'à ce que la personne l'accepte, la corrige ou la refuse.
_Avoid_: Mise à jour silencieuse

**Mémoire de refus**:
Trace minimale, sans expiration automatique, d'une proposition de profil rejetée et de son éventuelle clarification. Elle empêche de répéter la suggestion ou la question à cause du temps, d'une nouvelle offre ou d'un bilan de recherche; le sujet ne revient qu'à l'initiative de la personne, après un changement pertinent de son contexte ou face à une nouvelle preuve qui contredit matériellement le motif du refus.
_Avoid_: Affirmation négative dans le profil, historique de conversation

**Affirmation professionnelle**:
Énoncé atomique sur le parcours ou les aptitudes de la personne, conservé dans son état courant et relié, lorsque nécessaire, à sa provenance, à ses preuves et à sa validation.
_Avoid_: Historique exhaustif, métadonnées systématiques

**Admissibilité à la candidature**:
Propriété d'une affirmation professionnelle dérivée séparément de son origine, de sa validation humaine, de ses preuves et de sa validité temporelle. Une affirmation seulement déduite ou rejetée n'est jamais admissible; une contradiction matérielle non résolue suspend uniquement son usage dans la candidature concernée jusqu'à clarification humaine, sans modifier automatiquement le profil ni les autres usages non concernés.
_Avoid_: Niveau de confiance unique, score de vérité

**Provenance d'affirmation**:
Trace minimale de l'acquisition d'une affirmation professionnelle : mode d'acquisition, date et, lorsqu'il existe, pointeur vers le document ou l'entretien d'origine. Elle ne conserve pas la conversation brute après le traitement des propositions qui en proviennent.
_Avoid_: Dossier documentaire dupliqué

**Preuve professionnelle**:
Élément précis qui étaye ou contredit une affirmation professionnelle, comme un passage, un artefact, un résultat mesuré ou un exemple concret confirmé.
_Avoid_: Source entière non localisée

**Document professionnel source**:
Fichier personnel — ancien CV, certificat, diplôme ou élément de portfolio — que la personne gère directement et que l'agent consulte à sa demande. Le workflow ne l'importe, ne le copie, ne le surveille et ne le supprime pas; la personne demande séparément la correction d'une provenance devenue caduque.
_Avoid_: Document géré par le workflow, copie documentaire canonique

**Temporalité professionnelle**:
Date ou période, éventuellement partielle ou approximative, portée uniquement par un fait dont le sens dépend du temps.
_Avoid_: Horodatage systématique, fausse précision

**Signal de revérification**:
Indication temporaire qu'une affirmation actuelle mérite une nouvelle confirmation en raison de sa date, d'une contradiction ou d'un changement de contexte. Il ne rend jamais l'affirmation obsolète, ne modifie pas seul son admissibilité et disparaît après traitement.
_Avoid_: Expiration automatique, état canonique Obsolète

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
Exigence ou compétence utile à une offre qui n'est pas démontrée par le profil professionnel mais reste plausible au regard des éléments déjà confirmés. Un écart de profil n'est pas automatiquement éliminatoire: l'agent juge la plausibilité globale en tenant compte du fait qu'une annonce peut décrire un idéal irréaliste plutôt qu'un seuil réel, puis rend l'écart visible.
_Avoid_: Critère employeur automatiquement éliminatoire, compétence possédée par déduction

**Entretien ciblé**:
Séquence adaptative de questions proposée après le passage d'une offre à Retenue ou Postuler uniquement lorsqu'une information manquante ou ambiguë peut changer matériellement l'analyse ou la fidélité de la candidature. Elle annonce son objectif, pose une question à la fois et s'arrête lorsque l'information suffit; la personne peut passer, reporter ou interrompre, et choisit explicitement de continuer si l'échange dépasse le besoin initial. Elle reste facultative en Retenue, mais devient bloquante en Postuler lorsque l'information est indispensable à la préparation d'un dossier fidèle.
_Avoid_: Interrogatoire automatique, micro-profiling

**Bilan de recherche**:
Point périodique facultatif centré sur l'état et l'efficacité de la recherche d'emploi. Il sert à comprendre les difficultés ou l'absence de résultats et à chercher avec la personne d'autres solutions susceptibles de mener à un emploi satisfaisant; ce n'est pas un entretien général sur le profil professionnel.
_Avoid_: Entretien mensuel du profil, grilling périodique obligatoire

**Profiling continu**:
Évolution événementielle du profil professionnel à partir d'un changement signalé, d'un document désigné, d'une contradiction détectée ou d'une information utile apparue pendant le workflow. Il produit des propositions de profil soumises à validation et ne constitue pas un entretien général périodique.
_Avoid_: Grilling mensuel, mise à jour silencieuse, profilage permanent

**Contrainte personnelle globale**:
Limite non négociable qui s'applique à toutes les pistes de recherche. Une piste peut la renforcer mais ne peut pas l'assouplir sans modification validée de la contrainte globale.
_Avoid_: Préférence de recherche, critère dupliqué

**Piste de recherche**:
Mandat cohérent et indépendant qui porte exactement une intention de recherche et ses critères propres. Plusieurs pistes partagent le même profil professionnel sans partager leurs cibles, préférences, contraintes contextuelles ni critères éliminatoires. Une piste est Brouillon, Active ou En pause selon qu'elle est incomplète, participe à la recherche quotidienne ou en est temporairement exclue.
_Avoid_: Recherche globale, profil de recherche

**Intention de recherche**:
Expression, précise ou ouverte, du travail recherché dans une piste; elle peut désigner des métiers, des activités, un domaine ou une ouverture large compatible avec les contraintes de la personne.
_Avoid_: Intitulé obligatoire, rôle cible exhaustif

**Périmètre de recherche**:
Cadre minimal indiquant où ou dans quelles conditions chercher les offres d'une piste, par exemple une zone géographique ou le travail à distance depuis un lieu donné.
_Avoid_: Marché implicite, localisation du poste uniquement

**Langue de travail**:
Langue requise ou pratiquée dans l'activité professionnelle visée, distincte de la langue dans laquelle l'annonce est rédigée.
_Avoid_: Langue de l'annonce

**Langue de candidature**:
Langue dans laquelle la personne accepte de préparer et transmettre une candidature, indépendamment de la langue de travail.
_Avoid_: Langue de travail, langue de l'annonce

**Séniorité professionnelle**:
Niveau attendu ou visé dans un métier lorsque cette notion y est pertinente. Elle n'est ni obligatoire pour une piste ni déduite mécaniquement des années d'expérience.
_Avoid_: Âge, ancienneté brute

**Latitude de recherche**:
Degré d'ouverture d'une piste à des activités éloignées du parcours actuel. Le parcours peut motiver une proposition de latitude, mais seule la confirmation humaine la fixe.
_Avoid_: Séniorité, flexibilité déduite de l'âge

**Attente de rémunération**:
Critère facultatif exprimé dans l'unité pertinente pour la piste — heure, mois, année, mission ou autre — avec devise, période et base brute ou nette lorsqu'elles sont connues. Un minimum peut être éliminatoire et un objectif préférentiel; une attente qualitative reste possible.
_Avoid_: Salaire annuel obligatoire, montant sans unité

**Critère de recherche**:
Condition structurée et interprétable d'une piste, assortie d'un effet éliminatoire ou préférentiel. Une dimension peut réunir plusieurs critères indépendants; une note libre peut en expliquer l'intention mais ne détermine pas leur application.
_Avoid_: Consigne libre, filtre opaque

**Critère éliminatoire**:
Condition d'une piste dont la contradiction avérée rend une offre inadmissible pour cette piste. L'absence d'information crée une incertitude à signaler et peut réduire le classement, mais n'élimine pas l'offre.
_Avoid_: Préférence forte, pénalité

**Préférence de recherche**:
Condition souhaitable propre à une piste qui éclaire la sélection expliquée sans déterminer l'admissibilité ni produire de classement. Une offre fortement alignée avec l'intention peut être sélectionnée malgré des préférences non satisfaites, dont les écarts matériels sont alors rendus visibles.
_Avoid_: Critère obligatoire, préférence globale, points de classement

**Brief quotidien**:
Sélection dédupliquée de nouvelles offres admissibles et expliquées, présentée sans classement pour décision humaine et sans préparer automatiquement une candidature. Cinq à dix offres constituent une cible pour l'effort de recherche, jamais un minimum à remplir avec des offres inadmissibles ni un plafond qui masque des résultats admissibles.
_Avoid_: Quota garanti, liste exhaustive, flux d'offres

**Sélection expliquée**:
Choix raisonné d'offres admissibles dont l'agent peut défendre la correspondance réelle avec l'intention de la piste, accompagné séparément de leurs motifs favorables, écarts et incertitudes afin que la personne puisse comprendre et contester leur présence dans le brief. L'absence de contradiction ne suffit pas à sélectionner une offre; la sélection ne produit ni classement, ni niveau qualitatif, ni score composite global.
_Avoid_: Classement, note globale, pourcentage de compatibilité, score opaque

**Incertitude d'offre**:
Information absente, ambiguë ou insuffisamment fiable qui compte pour juger une offre. Elle n'équivaut pas à une contradiction et n'empêche la sélection que lorsqu'elle rend impossible une correspondance défendable avec l'intention; sinon elle est signalée avec la vérification nécessaire.
_Avoid_: Critère non satisfait, supposition silencieuse

**Fraîcheur d'offre**:
Signal favorable indiquant qu'une offre a été publiée, mise à jour ou vérifiée récemment et qu'une candidature a davantage de chances d'être encore opportune. Elle contribue au jugement de sélection sans constituer à elle seule un motif suffisant, un classement affiché ou une limite d'âge uniforme; une offre ancienne reste sélectionnable si elle est encore active et pertinente, avec son âge rendu visible.
_Avoid_: Bonus chiffré de récence, date couperet universelle, preuve que le poste est ouvert

**Diversité de recherche**:
Couverture volontaire de plusieurs interprétations plausibles d'une intention large pendant l'acquisition des offres. Elle ne crée aucun quota par catégorie, ne justifie jamais une offre faible et ne retire pas une bonne offre parce qu'une catégorie est déjà représentée.
_Avoid_: Quota de diversité, variété artificielle du brief

**Justification d'offre**:
Explication courte et contestable de la présence d'une offre dans le brief, dont chaque motif important renvoie à un élément précis de l'annonce, de la piste ou du profil confirmé. Elle suit les rubriques « Pourquoi elle correspond », « Atouts confirmés », « Écarts importants », « Incertitudes à vérifier » et « Fraîcheur/échéance », en omettant celles qui sont vides; une compétence seulement déduite ne peut jamais constituer un motif favorable et reste un besoin éventuel de vérification.
_Avoid_: Argument générique, rapprochement invérifiable, compétence supposée

**Offre**:
Opportunité d'emploi découverte et soumise au triage, qu'elle mène ou non à une candidature. Une offre dédupliquée correspondant à plusieurs pistes est présentée sous une seule d'entre elles, sans signification particulière attachée à ce choix.
_Avoid_: Proposition, candidature

**Contact d'opportunité**:
Coordonnée professionnelle publiquement fournie et rôle d'un interlocuteur, conservés uniquement comme composantes d'une opportunité précise. Le contact n'existe pas comme profil personnel global et suit la rétention de l'opportunité.
_Avoid_: Profil de recruteur, contact privé, attribut personnel déduit

**Nouveau**:
État initial d'une offre découverte qui n'a encore reçu aucune décision humaine de triage. Elle reste visible dans le backlog mais ne reparaît pas comme nouvelle dans les briefs ultérieurs.
_Avoid_: À trier, non traitée

**Ignorer**:
Décision de triage qui écarte durablement une offre dans toutes les pistes. L'offre ne réapparaît pas automatiquement mais reste restaurable manuellement.
_Avoid_: Masquer temporairement, ignorer dans une seule piste

**En réserve**:
Décision de triage qui met une offre de côté tout en la gardant accessible. Elle ne déclenche aucune action de l'agent et ne redevient active que lorsque la personne la déplace explicitement vers une décision active.
_Avoid_: À surveiller, rappel automatique

**Retenue**:
Décision de triage par laquelle la personne sélectionne une offre pour autoriser l'analyse approfondie de son adéquation et, si nécessaire, un entretien ciblé qui aborde les contradictions avec les critères. Elle ne déclenche pas la génération de documents de candidature.
_Avoid_: Acceptée, Intéressé

**Postuler**:
Décision de triage qui autorise l'usage des données confirmées et de l'identité de candidature nécessaires pour préparer un dossier précis et sa destination vérifiée, avec ou sans passage préalable par Retenue. Elle vaut exception locale aux critères contradictoires sans les modifier; seule une correction confirmée séparément peut faire évoluer le profil ou la piste. Elle n'autorise ni l'envoi par l'agent ni le passage au suivi des candidatures envoyées.
_Avoid_: Envoyer, candidature envoyée

**Dossier de candidature**:
Ensemble préparé pour une offre retenue comprenant le CV, la lettre de motivation, l'email d'accompagnement et une destination vérifiée sous forme d'adresse email ou de lien de candidature.
_Avoid_: Candidature envoyée, dossier de postulation

**Candidature**:
Démarche engagée après décision de postuler à une offre. Son dossier est d'abord préparé et notifié à la personne; elle ne rejoint le tableau de suivi et le calendrier des relances qu'après confirmation humaine de son envoi, puis reste suivie jusqu'à son résultat final.
_Avoid_: Offre acceptée, proposition acceptée

**Tableau de triage**:
Vue Kanban locale où les offres arrivent dans Nouveau puis passent entre les décisions Ignorer, En réserve, Retenue et Postuler.

**Ignorer**:
Décision globale et durable d'écarter une offre du triage, même si elle correspond à plusieurs pistes. L'offre ne peut revenir que par une restauration humaine explicite.
_Avoid_: Masquer temporairement, ignorer pour une piste

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
Compétence étayée par une expérience, une formation, un projet, un portfolio ou un autre artefact consultable. Cette documentation est indépendante de la confirmation humaine et ne la remplace pas.

**Compétence déclarée et confirmée**:
Compétence, notamment autodidacte, déclarée par la personne puis confirmée durant l'entretien à l'aide d'exemples concrets, même sans justificatif formel.

**Compétence déduite**:
Compétence suggérée par l'agent à partir du parcours, mais pas encore confirmée par la personne. Elle reste une proposition de profil hors du profil professionnel canonique et ne peut pas être utilisée dans une candidature.
