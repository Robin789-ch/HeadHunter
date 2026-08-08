Status: resolved
Type: grilling

# Définir les frontières de confidentialité, consentement et rétention

## Question

Quelles données personnelles peuvent être stockées, transmises ou supprimées, selon quelles durées et quels consentements, et quelles informations doivent être exclues ou protégées séparément?

## Answer

Le workflow reste personnel, local-first et volontairement simple. Codex peut traiter le profil professionnel et les fichiers que la personne lui désigne, mais l'automation quotidienne ne transmet aucune donnée personnelle aux sources d'offres. L'identité de candidature, les coordonnées et les informations personnelles protégées restent séparées du profil chargé pour le raisonnement courant; elles ne sont mobilisées qu'après une action humaine explicite liée à une candidature précise.

Le profil exclut diagnostic médical, religion, opinion politique, orientation sexuelle, situation familiale, identifiants officiels, données bancaires et secrets d'accès. Une capacité professionnelle factuelle nécessaire — droit de travailler, permis de conduire ou besoin d'aménagement déclaré — peut être conservée séparément si la personne la fournit volontairement; elle n'est ni déduite ni utilisée comme signal général de rapprochement.

Les documents professionnels personnels — anciens CV, certificats, diplômes et portfolio — restent des fichiers entièrement gérés par la personne. Le workflow ne les importe, ne les copie, ne les surveille et ne les supprime pas. L'agent les consulte sur demande et la personne lui demande de corriger la base lorsqu'une source disparaît ou qu'une donnée doit changer. Les affirmations structurées confirmées, le profil, l'identité et les pistes n'expirent pas automatiquement; ils restent jusqu'à une demande de correction ou de suppression adressée à l'agent. Le système ne requiert donc ni gestionnaire documentaire ni moteur générique de suppression en cascade.

Le consentement est porté par les actions métier. Désigner un fichier autorise sa consultation pour le besoin demandé; connecter une source autorise un accès révocable à cette seule source; Postuler autorise l'utilisation des données confirmées et de l'identité nécessaires pour préparer ce dossier précis. Aucune de ces actions n'autorise un envoi externe, qui reste humain. Révoquer un connecteur coupe immédiatement son accès et supprime ses secrets, sans effacer les opportunités ou candidatures déjà enregistrées; leur suppression se demande séparément à l'agent.

Les mots de passe, cookies, jetons OAuth et clés API ne résident jamais dans le workspace ni dans le contexte du modèle. Ils restent dans le trousseau système ou le stockage sécurisé du connecteur et disparaissent à sa révocation. Les données personnelles d'exécution restent hors de Git; le workflow ne crée pas de sauvegarde durable cachée et ne peut garantir l'effacement de copies réalisées séparément par l'utilisateur ou son système de sauvegarde.

La rétention automatique se limite aux données produites ou gérées par le workflow:

- le contenu complet d'une offre ignorée est supprimé après 7 jours, mais une empreinte minimale sans coordonnées ni texte intégral reste afin que la décision Ignorer demeure effective;
- le dossier, les échanges et les coordonnées d'une candidature terminée sont conservés 3 mois après son résultat final, sauf prolongation explicite; le résultat minimal et les apprentissages déjà confirmés subsistent;
- le journal minimal des consentements et actions sensibles est conservé 3 mois, sans contenu métier;
- les journaux techniques expurgés de données personnelles sont supprimés après 7 jours.

Les coordonnées professionnelles publiquement fournies et le rôle d'un interlocuteur font partie de l'opportunité, jamais d'un profil personnel global. Ils suivent sa rétention: 7 jours après Ignorer ou 3 mois après le résultat d'une candidature. Aucun contact privé, enrichissement personnel ou attribut déduit n'est conservé.
