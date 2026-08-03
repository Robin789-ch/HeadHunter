# Typst pour la génération reproductible de CV et lettres

## Conclusion

Typst convient à la **dernière étape de composition** du workflow : il peut charger un dossier de candidature structuré, le rendre avec des modèles réutilisables et produire des PDF localement par CLI. Il ne doit pas être la base de données ni le moteur qui choisit ou invente le contenu. Le contrat recommandé est donc : données canoniques structurées → sélection éditoriale validée → rendu Typst → contrôles automatiques → validation humaine.

La reproductibilité n'est pas acquise par le seul format `.typ`. Elle exige de figer le compilateur, les dépendances, les polices, la racine de projet et les métadonnées temporelles. Cette conclusion est une inférence d'architecture fondée sur les mécanismes officiels détaillés ci-dessous.

## Capacités officielles utiles

### Données structurées

Typst sait charger directement JSON, YAML, TOML et CSV, en convertissant les objets et séquences en dictionnaires et tableaux Typst. Les nombres, chaînes, tableaux et dictionnaires composés de ces types sont les valeurs dont la conversion est fiable ; les types plus riches peuvent subir une conversion avec perte. Pour une candidature, un fichier JSON ou YAML contenant uniquement des valeurs simples est donc un bon contrat d'entrée. Sources : [Data Loading](https://typst.app/docs/reference/data-loading/), [JSON](https://typst.app/docs/reference/data-loading/json/), [YAML](https://typst.app/docs/reference/data-loading/yaml/).

La CLI permet aussi de fournir des paramètres par `--input key=value`, accessibles dans `sys.inputs`, mais chaque valeur y est toujours une chaîne. Cette voie convient à des sélecteurs simples — langue, variante, identifiant de candidature — pas au profil complet ; pour celui-ci, il vaut mieux charger un fichier structuré. Source : [System Functions](https://typst.app/docs/reference/foundations/sys/).

Typst encapsule l'accès aux fichiers dans une racine de projet. Par défaut, il s'agit du dossier parent du fichier principal ; `--root` permet de la fixer explicitement. Cela rend possible un dossier autonome contenant données, modèles, polices et sorties, tout en empêchant un template de lire hors de cette racine. Source : [Path — Project root](https://typst.app/docs/reference/foundations/path/#roots).

### Modèles réutilisables et variantes

Un template Typst est une fonction qui enveloppe le document. Il peut recevoir des arguments nommés avec valeurs par défaut, appliquer des règles de style, puis être placé dans un fichier séparé et importé. La méthode `.with(...)` préremplit ses paramètres. Cela suffit pour exposer une API stable telle que `cv(data:, variant:, lang:, body:)` et `letter(data:, variant:, lang:, body:)`. Source : [Making a Template](https://typst.app/docs/tutorial/making-a-template/).

Le langage de script intégré fournit fonctions, tableaux, dictionnaires, boucles et conditions. Les variantes peuvent donc être des paramètres explicites qui sélectionnent une mise en page, un ordre de sections ou un thème, sans dupliquer toutes les sources. Les imports locaux séparent proprement composants, modèles et entrées. Source : [Scripting](https://typst.app/docs/reference/scripting/).

Les paquets Typst sont importés avec un triplet namespace/nom/**version** (`@preview/example:0.1.0`). Si un paquet externe est retenu, sa version doit rester explicite ; pour limiter les dépendances réseau et les changements tiers, des composants locaux ou vendoriés sont préférables pour ce workflow local-first. La seconde phrase est une recommandation d'architecture. Source : [Scripting — Packages](https://typst.app/docs/reference/scripting/#packages).

### Polices et langues

Le moteur accepte une famille ou une liste ordonnée de familles et cherche les glyphes dans l'ordre. Mais les polices disponibles diffèrent entre l'application web et une machine locale. En local, la CLI peut ajouter un dossier avec `--font-path`, ignorer les polices système avec `--ignore-system-fonts`, et lister les polices découvertes avec `typst fonts`; l'ordre de priorité est documenté. Pour obtenir la même pagination sur chaque exécution, il faut donc embarquer les fichiers `.ttf`/`.otf` autorisés dans le projet et compiler en ignorant les polices système. Source : [Text — Font](https://typst.app/docs/reference/text/text/#parameters-font).

`text` porte aussi `lang`, `region` et `hyphenate`; la langue influence notamment la césure et les conventions typographiques. Chaque document doit régler sa langue principale, et baliser les passages dans une autre langue. Source : [Text](https://typst.app/docs/reference/text/text/), complétée par le [guide d'accessibilité](https://typst.app/docs/guides/accessibility/#language).

Limitation à prévoir pour les dates écrites en toutes lettres : la documentation indique que les noms de mois et de jours produits par `datetime.display` ne sont actuellement disponibles qu'en anglais. Les libellés localisés doivent donc venir des données ou d'une fonction de localisation contrôlée. Source : [Datetime — Format](https://typst.app/docs/reference/foundations/datetime/#format).

### Compilation et PDF

`typst compile source.typ output.pdf` produit un PDF, format d'export par défaut. `typst watch` sert à l'itération locale mais l'automation doit utiliser `compile`. La CLI permet aussi de sélectionner un standard PDF; Typst produit du PDF 1.7 par défaut et écrit des PDF balisés par défaut. Sources : [dépôt officiel Typst — Usage](https://github.com/typst/typst#usage), [PDF — Exporting](https://typst.app/docs/reference/pdf/#exporting-as-pdf).

Pour un PDF octet-pour-octet reproductible, la date du document ne doit pas rester à `auto`, car ce défaut incorpore la date et l'heure courantes. Il faut régler `document(date: none)` ou une date explicite. `datetime.today()` peut aussi être figé via `--creation-timestamp` ou `SOURCE_DATE_EPOCH`. Sources : [Document — date](https://typst.app/docs/reference/model/document/#parameters-date), [Datetime — today](https://typst.app/docs/reference/foundations/datetime/#definitions-today).

Le compilateur expose sa version avec `sys.version`. En conséquence, le workflow doit épingler la version du binaire et peut ajouter une assertion de version dans le modèle afin d'échouer clairement en cas d'écart. La nécessité d'épingler est une inférence; le mécanisme de détection est officiel. Source : [System Functions](https://typst.app/docs/reference/foundations/sys/).

## Contrat de rendu recommandé

Pour chaque candidature validée, le générateur éditorial devrait écrire un `application.json` autonome contenant au minimum : métadonnées de l'offre, identité et coordonnées autorisées, expériences/compétences sélectionnées, formulations validées, langue, variante de CV, corps de lettre et contraintes attendues (`cv_max_pages`, `letter_max_pages`). Typst charge ce fichier et ne va pas rechercher lui-même des faits dans le profil global.

Organisation logique proposée :

```text
typst/
  templates/       # cv.typ, letter.typ, composants communs
  fonts/           # fichiers de polices figés et licences
applications/<id>/
  application.json # snapshot éditorial validé
  cv-main.typ
  letter-main.typ
  output/           # PDF et aperçus PNG
```

Les entrées `cv-main.typ` et `letter-main.typ` restent très minces : chargement des données, import du template, choix explicite de la variante et rendu. Le profil complet et ses preuves restent hors de l'entrée Typst; cette séparation réduit le risque d'inclure par accident une donnée non validée.

Une invocation reproductible doit conceptuellement fixer :

```sh
typst compile --root <workspace> \
  --ignore-system-fonts --font-path <workspace>/typst/fonts \
  --creation-timestamp <timestamp-fixe> \
  <source.typ> <output.pdf>
```

Le workflow doit en plus enregistrer avec l'artefact : version Typst, empreinte du fichier de données, variante, langue, empreintes des polices et commande de compilation. Cela permet d'expliquer et de reproduire un document même après évolution du profil.

## Contrôle qualité possible

1. **Validation des données avant mise en page.** `assert`, `assert.eq` et `assert.ne` font échouer la compilation quand une condition n'est pas satisfaite. Le template peut vérifier les champs obligatoires, les types attendus, l'absence de sections vides et les bornes de variante. Source : [Assert](https://typst.app/docs/reference/foundations/assert/).
2. **Budget de pages.** Le compteur de pages expose sa valeur finale dans un contexte. Le modèle peut donc faire échouer un CV dépassant sa limite, ou la pipeline peut interroger la valeur finale. Source : [Counter — final](https://typst.app/docs/reference/introspection/counter/#definitions-final).
3. **Métadonnées de test.** Des valeurs invisibles peuvent être exposées avec `metadata`, puis extraites en JSON avec `typst eval ... --in document.typ`. Cela permet de tester la variante rendue, l'identifiant de candidature ou la présence logique de sections sans analyser le PDF. Source : [Query — Command line queries](https://typst.app/docs/reference/introspection/query/#command-line-queries).
4. **Accessibilité et extraction.** Les PDF sont balisés par défaut. Une compilation avec `--pdf-standard ua-1` lance des vérifications supplémentaires et échoue sur certaines violations. Typst précise néanmoins que des règles essentielles — contraste, exactitude de la langue, usage non exclusif de la couleur — ne sont pas toutes vérifiables automatiquement. Il faut utiliser les éléments sémantiques Typst, définir le titre et la langue, et garder une vérification manuelle. Sources : [PDF — PDF/UA](https://typst.app/docs/reference/pdf/#pdfua), [Accessibility Guide — Testing](https://typst.app/docs/guides/accessibility/#testing-for-accessibility).
5. **Revue visuelle.** Typst peut rendre directement chaque page en PNG, avec PPI configurable et noms numérotés pour les documents multipages. La pipeline peut donc produire des aperçus pour comparaison visuelle ou validation humaine avant envoi. Source : [PNG — Exporting](https://typst.app/docs/reference/png/#exporting-as-png).
6. **Contrôles externes complémentaires.** Le guide officiel recommande notamment veraPDF pour vérifier les standards PDF déclarés et souligne que les outils automatiques ne fournissent qu'une base. Pour un CV, il faut en plus tester extraction/copier-coller, liens, lisibilité et ordre de lecture, puis conserver la validation humaine finale. Source : [Accessibility Guide — Testing for Accessibility](https://typst.app/docs/guides/accessibility/#testing-for-accessibility).

## Contraintes à inscrire dans la future spécification

- Typst rend exclusivement un snapshot éditorial déjà validé; il ne décide ni de la véracité ni de la pertinence des éléments du profil.
- Toute variante est nommée, bornée et testée; l'agent ne modifie pas librement les marges ou la taille de police pour faire entrer artificiellement le contenu.
- Le CV et la lettre ont chacun un budget de pages explicite; un dépassement bloque la livraison et renvoie vers l'étape éditoriale.
- Version du compilateur, imports de paquets, polices et timestamp sont figés. Toute mise à niveau déclenche une recompilation et une revue des jeux d'essai.
- Les polices sont embarquées avec leurs licences; la compilation automatisée ignore les polices système.
- Les données chargées restent constituées de chaînes, nombres, booléens, tableaux et dictionnaires. Le template évite d'évaluer comme code du contenu généré.
- Les fonctions d'introspection restent simples : Typst avertit que les requêtes qui influencent leur propre résultat peuvent ne jamais se stabiliser. Source : [Query — A word of caution](https://typst.app/docs/reference/introspection/query/#a-word-of-caution).
- Une compilation réussie n'est pas une approbation. Les PDF et emails restent soumis à la validation humaine définie par le workflow.

## Décision que ces faits permettent

La future spécification peut retenir Typst à 100 % pour les **CV et lettres rendus**, avec deux familles de templates paramétrés et quelques variantes explicites. Le moteur agentique produit d'abord un snapshot JSON validé, puis une pipeline locale et versionnée compile, contrôle et prévisualise le PDF. Les emails courts peuvent être conservés en texte/Markdown, car Typst n'apporte rien à leur envoi; s'il faut aussi un exemplaire PDF ou imprimable de l'email, le même mécanisme de template peut le rendre.
