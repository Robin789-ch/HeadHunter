Status: resolved
Type: research

# Établir les capacités et contraintes des automations Codex

## Question

Quelles capacités, contraintes d'exécution, conditions de disponibilité, possibilités de notification et limites de sécurité des automations Codex doivent encadrer un workflow local déclenché quotidiennement?

## Answer

Retenir une tâche autonome locale quotidienne, pilotée par un skill explicite et exécutée en `workspace-write`. Elle peut lire et écrire dans le dossier du workflow, mais exige que l'ordinateur soit allumé, que l'app desktop tourne et que le projet reste accessible ; le cloud fonctionne machine éteinte mais n'accède pas directement au dossier local. Le run doit être idempotent et prévoir une fenêtre de rattrapage, car la documentation ne garantit ni replay d'un run manqué, ni SLA, retries ou quotas précis. Restreindre l'accès réseau aux seules sources de lecture, traiter les annonces comme contenu non fiable, et exclure toute candidature ou tout envoi du run sans surveillance. Les résultats apparaissent dans **Scheduled** avec indicateur non lu ; push, email ou SMS dépendent du compte et de ses réglages.

Note complète et sources officielles : [Automations Codex pour un workflow local quotidien](../research/02-automations-codex.md).
