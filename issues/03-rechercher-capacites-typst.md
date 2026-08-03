Status: resolved
Type: research

# Établir les capacités et contraintes de Typst pour les candidatures

## Question

Quelles capacités et contraintes officielles de Typst faut-il intégrer pour générer de manière reproductible des CV et lettres PDF à partir de données structurées, avec modèles réutilisables, variantes et contrôle qualité?

## Answer

Typst convient comme couche finale de composition : un snapshot JSON validé alimente des templates paramétrés distincts pour CV et lettre. La spécification devra figer version du compilateur, dépendances, polices, racine de projet et timestamp, puis imposer assertions de données et de pagination, export PDF balisé/PDF-UA, aperçus PNG, contrôles d'extraction et validation humaine. Typst ne remplace ni la base de profil, ni l'orchestration, ni la production ou l'envoi des emails. Voir la [note de recherche détaillée](../research/03-typst.md).
