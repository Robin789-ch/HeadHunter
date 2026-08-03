# Automations Codex pour un workflow local quotidien

_Recherche effectuée le 3 août 2026 à partir du manuel Codex officiel actualisé et de ses pages sources OpenAI._

## Conclusion

Une tâche planifiée Codex convient à la recherche d'emploi quotidienne, à condition d'accepter qu'un run **local** dépend de la machine : l'ordinateur doit être allumé, l'application desktop doit tourner et le dossier sélectionné doit toujours être disponible. Le mode cloud continue sans la machine, mais ne peut pas travailler directement dans un dossier local. Il faut donc choisir explicitement entre **état local canonique** et **exécution indépendante de la machine** ; la documentation ne décrit pas de synchronisation automatique entre ces deux modes. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) · [Get started with ChatGPT Work](https://learn.chatgpt.com/docs/get-started-with-work)

Pour le système envisagé, le choix cohérent est une tâche locale quotidienne, en `workspace-write`, limitée au dossier du workflow, qui recherche, déduplique, classe et écrit un brief — sans envoyer de candidature ni d'email. La recherche doit être conçue comme idempotente et rattraper plusieurs jours, car la documentation officielle consultée ne promet ni exécution de rattrapage après extinction de la machine, ni heure de déclenchement exacte, ni politique publique de retry.

## Capacités établies

| Capacité | Ce que documente OpenAI | Conséquence pour le workflow |
|---|---|---|
| Planification | Les tâches peuvent être récurrentes ; des cadences personnalisées et des règles RFC 5545 `RRULE` sont prises en charge. Une tâche liée à un chat accepte notamment des rythmes quotidiens ou hebdomadaires. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) | Programmer un run quotidien à une heure choisie ; ne pas interpréter cette cadence comme une garantie de SLA. |
| Périmètre local | Dans l'app desktop, un run peut travailler dans le projet local ou, pour un dépôt Git, dans un worktree isolé. Un projet non versionné est modifié directement dans son dossier. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) | Si le dossier du workflow n'est pas un dépôt Git, la tâche écrira directement dans sa base de profil et son historique ; sauvegardes et écritures atomiques deviennent importantes. |
| Contexte de run | Une tâche autonome crée un nouveau chat à chaque run ; une tâche planifiée dans un chat reprend le contexte existant. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) | Préférer un run autonome si les fichiers sont la source de vérité. Cela évite que l'état métier dépende d'un historique conversationnel opaque. |
| Méthode réutilisable | Les tâches planifiées peuvent utiliser des skills et des plugins. Le prompt peut invoquer explicitement un skill avec `$skill-name`. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) | Mettre la logique stable — lecture du profil, recherche, normalisation, classement, déduplication, écriture du brief — dans un skill ; laisser à la tâche uniquement le calendrier et les paramètres du run. |
| Modèle | Le modèle et l'effort de raisonnement peuvent rester aux valeurs par défaut ou être choisis explicitement. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) | Épingler ces paramètres seulement si les tests montrent qu'ils sont nécessaires à la reproductibilité ou au coût. |
| Exploitation | La vue **Scheduled** montre les tâches actives, en pause ou terminées et leurs runs récents ; elle permet d'inspecter et d'archiver les runs. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) | Utiliser cette vue pour contrôler les premiers runs et les échecs, sans en faire la base de suivi des candidatures. |

## Conditions de disponibilité et d'exécution

- La fonctionnalité doit être activée pour le workspace. La création et la gestion se font sur le web ou dans l'app desktop ; ni le CLI Codex ni l'extension IDE n'offrent l'interface **Scheduled**. [Scheduled tasks](https://learn.chatgpt.com/docs/automations)
- Un run ayant besoin de fichiers locaux exige que l'ordinateur reste allumé, que l'app desktop soit en cours d'exécution et que le projet reste disponible sur disque. [Scheduled tasks](https://learn.chatgpt.com/docs/automations)
- Une tâche web peut utiliser du contexte uploadé, des outils connectés, des skills et des plugins, mais ne conserve pas l'accès à un dossier ou worktree local entre les runs. [Scheduled tasks](https://learn.chatgpt.com/docs/automations)
- Le cloud est l'alternative documentée lorsqu'un travail doit continuer après fermeture de l'app ou extinction de l'ordinateur ; il ne répond donc pas, sans autre stockage synchronisé, à l'exigence d'une base locale canonique. [Get started with ChatGPT Work](https://learn.chatgpt.com/docs/get-started-with-work)
- OpenAI conseille de tester d'abord le prompt dans un chat normal, puis d'inspecter les premiers runs et d'ajuster le prompt, les outils ou la cadence. [Scheduled tasks](https://learn.chatgpt.com/docs/automations)

### Incertitudes à ne pas transformer en hypothèses

La documentation officielle consultée ne spécifie pas :

- si un run manqué pendant l'extinction de la machine est rejoué ;
- la précision temporelle ou le délai maximal du déclenchement ;
- le nombre de tentatives et le backoff après erreur ;
- les quotas ou la concurrence maximale propres aux tâches planifiées.

En conséquence, chaque run devrait lire un `last_successful_scan_at`, rechercher depuis cette date avec une marge, produire un identifiant de run, dédupliquer par identifiant canonique d'offre et n'avancer le curseur qu'après une écriture réussie. C'est une recommandation de robustesse, pas une capacité promise par OpenAI.

## Notifications et supervision

- La vue **Scheduled** agit comme une boîte de réception : les résultats y apparaissent et un indicateur non lu signale qu'un run demande de l'attention. [Scheduled tasks](https://learn.chatgpt.com/docs/automations)
- Dans l'app desktop, les alertes de fin de tour peuvent être désactivées, affichées seulement lorsque l'app est en arrière-plan ou toujours affichées. Les notifications de permissions et de questions ont des réglages séparés, et l'autorisation du système d'exploitation peut être requise. [Notifications](https://learn.chatgpt.com/docs/notifications)
- Sur le web, les canaux disponibles dépendent de la catégorie et du compte ; ils **peuvent** inclure push, email ou SMS. Il ne faut donc pas promettre l'email ou le SMS sans vérifier le compte concerné. [Notifications](https://learn.chatgpt.com/docs/notifications)

Pour ce workflow, un run réussi devrait rester sobre : déposer le brief dans le dossier et signaler « N nouvelles offres pertinentes ». Un échec devrait laisser un statut local explicite et une notification demandant une intervention. Le workflow ne doit pas dépendre d'un canal externe particulier pour garantir l'intégrité de son état.

## Sécurité et permissions

Les tâches planifiées s'exécutent sans surveillance avec les paramètres de sandbox par défaut. OpenAI recommande le périmètre le plus étroit possible. Lorsque la politique d'organisation le permet, elles utilisent `approval_policy = "never"`; si une politique administrateur l'interdit, elles retombent sur le comportement d'approbation du mode de permission choisi. [Scheduled tasks](https://learn.chatgpt.com/docs/automations)

Conséquences par mode :

- `read-only` ne suffit pas : les écritures, l'accès réseau et les apps locales nécessaires échouent.
- `workspace-write` autorise la lecture, les commandes et les écritures dans le workspace, mais bloque les écritures extérieures, le réseau et les apps locales sauf configuration explicite.
- `danger-full-access` augmente fortement le risque d'une tâche en arrière-plan, car elle peut modifier des fichiers, exécuter des commandes et accéder au réseau sans demander. OpenAI recommande plutôt `workspace-write` et des exceptions ciblées. [Scheduled tasks](https://learn.chatgpt.com/docs/automations) · [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security)

L'accès réseau local est désactivé par défaut en `workspace-write`. Lorsqu'il est nécessaire pour des commandes, il peut être activé puis restreint par une politique de destinations avec `network_proxy`; les règles sont orientées allowlist et les destinations locales/privées restent bloquées par défaut. [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security)

Les annonces sont du contenu externe non fiable. OpenAI cite explicitement le risque d'injection de prompt, d'exfiltration de secrets, de téléchargement malveillant et recommande de limiter les destinations et de contrôler les résultats. [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access)

### Garde-fous recommandés pour la recherche d'emploi

1. Exécuter le daily en `workspace-write`, avec le seul dossier du workflow comme racine inscriptible.
2. Accorder uniquement les lectures nécessaires aux sources d'offres ; pour le trafic de commandes, limiter les domaines et, lorsque possible, les méthodes à la lecture. Les plugins/connecteurs doivent eux aussi être limités aux capacités de lecture utiles.
3. Traiter le texte des annonces comme des **données** : ne jamais exécuter leurs instructions, scripts, liens d'upload ou demandes de secrets.
4. N'exposer au run quotidien aucun secret d'envoi et aucune capacité de candidature, d'email ou de modification externe. Ce run doit seulement lire, scorer et écrire localement.
5. Réserver toute transition `Postuler`, toute génération finale et tout envoi à une tâche interactive distincte avec validation humaine. Cela correspond aussi à la contrainte produit : un workflow planifié en `approval_policy = "never"` ne doit pas dépendre d'une approbation live.
6. Journaliser les sources consultées, les décisions de classement, les erreurs et le statut de chaque run, sans copier plus de données personnelles que nécessaire.

## Architecture opérationnelle recommandée

**Une tâche autonome locale quotidienne** :

1. invoque explicitement le skill de recherche d'emploi ;
2. lit le profil, les pistes et le curseur du dernier succès ;
3. recherche sur une fenêtre de rattrapage ;
4. normalise et déduplique les offres ;
5. classe sans modifier le profil confirmé ;
6. écrit un brief et le journal du run dans le workspace ;
7. notifie seulement le nombre de nouveautés, l'absence de résultat ou l'échec.

Le micro-grilling, la génération Typst, l'approche spontanée et l'envoi restent hors du run planifié : ils démarrent dans une session interactive après l'action humaine **Intéressé/Postuler**.

## Sources officielles

- OpenAI, [Scheduled tasks](https://learn.chatgpt.com/docs/automations)
- OpenAI, [Notifications](https://learn.chatgpt.com/docs/notifications)
- OpenAI, [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security)
- OpenAI, [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access)
- OpenAI, [Get started with ChatGPT Work](https://learn.chatgpt.com/docs/get-started-with-work)
