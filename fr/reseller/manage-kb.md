---
title: "Gérer la base de connaissances CloudOps"
slug: gerer-kb
---


<!-- Need to add information about inheritance and branding. -->

La base de connaissances de CloudOps est la source d'informations relatives au fonctionnement et à l'administration du système CloudOps. Il est conçu pour être hautement personnalisable pour les besoins de chaque entreprise. Des articles, des catégories et des langues peuvent être ajoutés ou supprimés selon vos besoins.

La base de connaissances est accessible depuis l'interface utilisateur en allant dans le menu Aide et en cliquant sur Centre d'aide. L'authentification n'est pas nécessaire pour accéder au Centre d'aide, qui est également accessible directement via son URL.

Le contenu est stocké dans un dépôt Git et est récupéré manuellement pour le stockage local par CloudOps. Tous les articles sont rédigés au format Markdown standard et peuvent inclure des images, des références à d'autres articles de la base de connaissances, des liens externes et d'autres fonctionnalités. Une catégorie donnée peut être marquée comme **en vedette** (*featured*, en anglais) et aura une icône plus grande et sera disposée au-dessus des autres catégories dans le Centre d'aide.

Les revendeurs et administrateurs travaillant avec la base de connaissances CloudOps auront besoin d'une connaissance de base des outils Git et du format Markdown.

La gestion de la base de connaissances nécessite le rôle **Revendeur** ou le rôle **Administrateur** avec le rôle *Base de connaissances: Gérer* appliqué.

Pour gérer la base de connaissances, cliquez sur *Administration* dans la barre latérale à gauche, puis cliquez sur *Base de connaissances*.

### Démarrage rapide

1. Git clone le dépôt de base de connaissances standard CloudOps sur votre poste de travail local :  https://github.com/cloudops/cloudmc-standard-kb <!-- Rephrase this in v2 -->
1. Explorez la structure de répertoires de niveau supérieur:
    - Le répertoire `assets` contient toutes les images.
    - Chaque langue prise en charge a un répertoire, par exemple `fr` pour le contenu en français et `en` pour l'anglais.
    - Le fichier `layout.yaml` définit les catégories et les articles contenus dans chaque catégorie.
1. Effectuez les personnalisations souhaitées dans la base de connaissances et enregistrez vos validations.
1. Créez un nouveau dépôt public vide et transférez le dépôt de la base de connaissances de votre poste de travail vers le nouveau dépôt.
1. Vérifiez que votre dépôt est accessible au public et que le contenu du dépôt apparaît comme prévu.
1. Accédez à la page *Base de connaissances*.
1. Cliquez sur le bouton *Créer une nouvelle base de connaissances*.
1. Une boîte de dialogue apparaîtra, demandant l'URL du dépôt à utiliser pour la base de connaissances. Entrez-le dans le champ de texte et cliquez sur *Valider*.
1. CloudOps récupérera le contenu du dépôt et toutes les catégories et tous les articles seront répertoriés. Le contenu peut maintenant être consulté dans le Centre d'aide.

### La structure du dépôt de la base de connaissances

Le dépôt de la base de connaissances a la structure suivante:

```
/				(Top directory)
|- README.md
|- layout.yaml  		(Defines categories)
|- assets/  			(Contains all graphics)
|- en/				(English language)
   |- category1/		(Category directory)
      |- category1.md	        (Category file)
      |- article1.md	        (Article file)
      |- article2.md
   |- category2/		
      |- category2.md
      |- article3.md
|- fr/				(French language)
   |- category1/
      |- category1.md
      |- article1.md
      |- article2.md
   |- category2/
      |- category2.md
      |- article3.md
   |- ...                       (And so on)
```

Le fichier `README.md` est une exigence de l'outil Git. Il peut s'agir d'un fichier vide de zéro octet.

#### Le répertoire ≪ assets ≫

CloudOps recherchera dans le répertoire `assets` les images référencées à partir des fichiers d'article. Les formats d'image pris en charge incluent JPEG, GIF et PNG.

#### Langues

CloudOps peut être configuré pour la prise en charge de plusieurs langues via la page [Brand Management](../administration/brand.md). Pour chaque langue activée, un répertoire de niveau supérieur peut être créé dans le dépôt de la base de connaissances pour le contenu dans cette langue. Le nom du répertoire doit être le code ISO 639-1 de la langue, en lettres minuscules, par exemple `fr` pour le français, `en` pour l'anglais, ou `es` pour l'espagnol.

Si une langue activée n'a pas de répertoire de niveau supérieur dans le dépôt, le contenu n'apparaîtra pas pour cette langue dans le Centre d'aide.

Les noms de tous les fichiers et répertoires sont en anglais, quelle que soit la langue du contenu. Ceci est arbitraire et peut être modifié à volonté. La seule exigence est que les noms de fichier et de répertoire soient les mêmes pour toutes les langues, conformément à leur spécification dans le fichier `layout.yaml`.

#### Les catégories

Chaque catégorie a son propre répertoire dans un répertoire de langue. Le nom de ce répertoire doit correspondre au nom de la catégorie dans `layout.yaml`.

À l'intérieur de chaque répertoire de catégorie se trouve un fichier de catégorie. Le nom du fichier de catégorie doit être le nom de la catégorie avec l'extension `.md`. Le fichier de catégorie est un fichier au format YAML qui contient une ligne qui définit le titre de la catégorie à afficher dans la base de connaissances pour la langue donnée:

![Exemple d'un en-tête d'une catégorie](../../assets/manage-kb-1.png)
Parce que chaque catégorie dans chaque langue a son propre fichier de catégorie, le titre de la catégorie dans cette langue est spécifié ici.

**Avis :** Le nom de chaque répertoire de catégorie *doit* être identique dans toutes les langues, comme spécifié dans `layout.yaml` (voir ci-dessous). Le nom de la catégorie affichée dans l'interface utilisateur sera extrait du contenu du fichier de catégorie.

#### Le fichier layout.yaml

Le fichier `layout.yaml` est une liste de catégories au format YAML. Chaque bloc du fichier spécifie une catégorie et ses détails. La connaissance de YAML n'est pas nécessaire, mais il est essentiel de conserver la structure d'origine et l'indentation dans le fichier lors de l'ajout de nouvelles catégories ou articles.
    - `category`: Le nom du répertoire où résident un fichier de catégorie et les articles de cette catégorie.
    - `icon`: Le nom de l'icône Font Awesome à utiliser pour la catégorie. Consultez la section Liens externes pour une liste des icônes Font Awesome disponibles pour utilisation dans le Centre d'aide.
    - `featured`: Le valeur **true** ou **false** (*vrai* ou *faux*) pour indiquer si une catégorie doit être mise en surbrillance dans le Centre d'aide. Ce champ peut être omis, la valeur par défaut est **false** (*faux*).
    - `articles`: une liste indentée des noms des fichiers article à inclure dans cette catégorie.

#### Les articles

Les fichiers d'article ont un court en-tête YAML :

![Exemple d'un en-tête d'un article](../../assets/manage-kb-2.png)

   - Le champ `title` définit le texte qui apparaît dans les listes de catégories et sur la première ligne de chaque article.
   - Le champ `slug` définit le chemin qui s'affichera dans l'URL dans la barre d'adresse du navigateur.

Après l'en-tête YAML, le corps de l'article suit et utilise le Markdown standard. Les images peuvent être référencées dans une référence régulière en utilisant le chemin `/assets/nom-du-fichier` :

![Exemple d'une référence à une image en Markdown](../../assets/manage-kb-3.png)

D'autres articles de la base de connaissances peuvent être référencés sous forme de lien régulier. Utilisez un chemin relatif pour référencer un article dans une autre catégorie :

![Exemple d'une référence à une article dans une autre catégorie](../../assets/manage-kb-4.png)

Les liens vers le contenu externe ainsi que les commentaires HTML fonctionnent comme prévu (le texte du commentaire n'apparaîtra pas dans le Centre d'aide):

![Exemples d'une référence à contenu externe et aussi d'une commentaire HTML](../../assets/manage-kb-5.png)

**Avis :** Le nom de chaque fichier article *doit* être identique dans toutes les langues, comme spécifié dans `layout.yaml`. Le nom de l'article affiché dans l'interface utilisateur sera extrait du contenu du fichier article.

### Synchronisation avec un dépôt

Lorsque des modifications ont été validées dans la branche `master` de votre dépôt, une synchronisation est nécessaire pour rendre les modifications disponibles dans le Centre d'aide. Sachez que bien qu'un dépôt donné puisse avoir plusieurs branches de travail, CloudOps extrait exclusivement de la branche `master`.

1. Accédez à la page *Base de connaissances*.
1. Cliquez sur le bouton *Synchroniser à partir du dépôt*.
1. Une notification s'affiche lorsque la synchronisation est terminée. De plus, le champ **Dernière synchronisation** sera mis à jour. Le contenu nouvellement mis à jour apparaîtra désormais dans le Centre d'aide.

### Voir aussi

[Brand Management](../administration/branding.md)

### Liens externes

[Git version control system](https://git-scm.com/)

[Markdown guide](https://www.markdownguide.org/)

[Font Awesome icons](https://fontawesome.com/v4.7.0/icons/)

[List of ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
