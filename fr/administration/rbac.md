---
title: "Contrôle d'accès à base de rôles"
slug: controle-d-acces-a-base-de-roles
---


Le contrôle d'accès dans CloudMC est obtenu par un modèle flexible et multi-locataire qui fournit une manière simple pour gérer les permissions à tous les niveaux d'une hiérarchie d'organisations et d'environnements.  La fonctionnalité du contrôle d'accès à base de rôles de CloudMC permet un niveaux de contrôle précis sur les permissions qui sont accordées aux utilisateurs.

## Définitions
- **Permission :** Une autorisation pour exécuter une tâche.  **Les permissions de système** régissent l'accès à la fonctionalité de la console de CloudMC, **les permissions d'environnement** régissent l'accès aux ressources d'un service.

- **Rôle système :** Une collection composée de permissions de système à l'intérieur d'une organisation.  CloudMC vient avec des **rôles fixes** qui ne peuvent être modifiés, et permet la création de **rôles personnalisés**.  Généralement, les rôles système sont simplement nommés ≪les rôles≫.

- **Portée :**  L'organisation ou les organisations auxquelles un rôle système s'applique.

- **Organisation :**  Un regroupement d'utilisateurs et de ressources connexes. Une organisation peut contenir des sous-organisations.  Une nouvelle installation de CloudMC vient avec l'organisation **System**.

- **Utilisateur :**  Le compte utilisateur est la façon de se connecter au portal CloudMC.  Un utilisateur est toujours assigné un rôle primaire dans l'organisation où son compte est créé.  Un utilisateur peut avoir des rôles additionels assignés, qui peuvent avoir une porté à une ou plusieurs organisation.

- **Environnement :** Un regroupement logique et sécurisé au sein d'une organisation, utilisée pour isoler et grouper des ressources sûrement.  L'accès est contrôlé par une combinaison de rôles d'environnement et des contrôles d'accès de l'organisation.

- **Membre :**  Les membres sont des utilisateurs qui ont obtenu l'accès à un environnement donné. Un utilisateur d'une organisation n'est pas nécessairement membre des environnements de cette organisation.

- **Rôle d'environnement :**  Une collection de permissions d'environnement qui s'applique aux membres d'un environnement.

![user access control chart](/assets/rbac-roles-chart-fr.png)

## Les rôles systèmes

La fonctionnalité d'un rôle système permet de controller l'accès à la fonctionnalité de CloudMC d'un façon simple et standard.  Un rôle système peut être assigné aux utilisateurs dans une organisation, et peut aussi permettre la collaboration à travers d'autres organisations.  Le rôles système sont appliqués dans l'interface Web autant que dans l'API CloudMC.  Les rôles personnalisés peuvent être définis avec des permissions qui sont alignées avec les règles d'affaires.

Tous les rôles système ont une portée définie, qui peut être une des celles-ci :
- Toutes les organisations dans CloudMC.
- Toutes les organisations de premier niveau.
- Une organisation spécifique, sans ses sous-organisations.
- Une organisation avec toutes ses sous-organisations.
- Seulement les sous-organisations d'une organisation spécifique.
- Toutes les organisations avec un étiquette specifique.

En utilisant les étiquettes, la portée d'un rôle assigné peut être augmentée automatiquement aux organisations qui reçoivent l'étiquette, et retiré lorsque l'éttiquette est supprimée.  Cette fonctionnalité rend possible les scénarios où la portée d'un rôle se change dynamiquement selon les règles d'affaires.

### Les rôles fixes
Les rôles fixes incorporés dans CloudMC s'appliquent à un vaste gamme de cas d'utilisation.  Ils peut être assignés au rôle primaire d'un utilisateur, ou comme un rôle additionel.

Voici un sommaire de chaque rôle fixe quand il est appliqué au rôle primaire :

- **Invité :**  Un rôle en lecture seule.  Pas capable d'énumérer les environnements auxquels cet utilisateur n'est pas assigné.
- **Utilisateur :**  Peut créer des nouveaux environnements avec des connexions de service existantes.  Pas capable de voir les environnements existantes tant que l'utilisateur n'y a pas été ajouté.
- **Administrateur :**  Peut gérer l'organisation.  Peut gérer les utilsateurs, les rôles, et tous les environnements dans toutes les connexions de service, et accéder aux donnés d'utilisation.  Pas capable ni de voir les sous-organisations ni de créer des nouvelles sous-organisiations.
- **Revendeur :** Peut gérer l'image de marque et la tarification pour l'organisation et ses sous-organisations, et peut créer des nouvelles sous-organisations dans l'organisation.  Pas capable de créer des nouvelles organsiations.
- **Opérateur :** Peut créer des organisations et des sous-organisations, gérer les connexions de service, les quotas, les engagements, et a l'accès complet à toutes les autres organisations, ressources et paramètres du système.

Chaque rôle fixe a une portée par défaut :
- Invité, Utilisateur, et Administrateur :  Seulement l'organisation dans laquelle l'utilisateur est créé.
- Revendeur : L'organisation dans laquelle l'utilisateur est créé et toutes ses sous-organisations.
- Opérateur : Toutes les organisations.

Comme l'illustre le diagramme ci-dessous, en montant dans le hiérarchie, chaque rôle reçoit toutes les privilèges de ceux qui précèdent :

![permissions chart](/assets/rbac-permissions-fr.png)

### Les rôles personnalisés

CloudMC permet à un utilisateur avec le rôle *Administrateur* et plus élevé (ou un utilisateaur avec un rôle personnalisé incluyant la permission *Rôles : Gérer*, expliqué dans cette section) à créer des nouveaux rôles avec les permissions qui sont alignées avec les règles d'affiares.  L'administrateur peut sélectionner permissions individuelles et sauvegarder le rôle, et après appliquer ce rôle aux utilisateurs dans l'organisation.  Les permissions effectives d'un utilisateur sont régies par l'union de toutes le permissions et la portée du rôle primarire avec toutes les rôles additionels.  Il faut que le rôle primaire de l'utilisateur soit un des rôles fixes incorporés, jamais un rôle personnalisé.

**Avis :** Lorsque une organisation est supprimée, tous le rôles personnalisés définis dans cette organisation seront aussi supprimés.

#### Créer un rôle personnalisé
Tous les rôles système et rôles personnalisés dans l'organisation sont énumérés à la page *Administration -> Rôles*.  Pour ajouter un rôle personnalisé, cliquer sur le bouton *Créer un rôle personnalisé* en haut à droit de la page.  Dans la page *Créer un rôle personnalisé*, saiser le nom pour le nouveau rôle dans le champ saisie, et une description facultative, et puis sélectionner les permissions souhaitées pour assigner au nouveau rôle.  Les permissions sont nommés avec le format *Charactéristique : Opération* et sont groupées selon le rôle système dont elles sont assignées par défaut.

![add custom role page](/assets/rbac-add_custom_role-en.png)

## Les rôles d'environnement
Pour contrôler l'accès aux ressources dans un environnement, CloudMC conçoit le *rôle d'environnement*.  En ajouter un membre nouveau à un environnement, il faut assigner un rôle d'environnment à l'utilisateur, qui régit le niveau d'accès accordé à l'utilisateur à l'intérieur de l'environnement.  La plupart des modules d'extension sont livrés avec le rôles d'environnment standards celles-ci :

- **Observateur :**  Accès en lecture seule à l'environnement.
- **Éditeur :**  Peut lire, écrire, et provisionner des ressources dans l'environnement, mais ne peut pas modifier les paramètres de l'environnement ni de gérer les utilisateurs.
- **Propriétaire :**  Cela ajoute les fonctions de changer les paramètres de l'environnement et de gérer les utilisateurs.

## Comment assigner les rôles

CloudMC permet à un utilisateur avec le rôle *Administrateur* et plus élevé (ou un utilisateur avec un rôle personnalisé incluyant la permission *Utilisateurs : Gérer*) à assigner des rôles fixes et personnalisés aux utilisateurs.  L'administrateur n'est pas permis à accorder une permission à un autre utilisateur sans déjà avoir cette même permission.  Ce modèle de sécurité empêche un utilisateur d'augmenter son propre accès sans autorisation (élévation des privilèges).

Les rôles primaires sont assignés à l'utilisateur de la page *Modifier l'utilisateur*.

![edit user page, primary role](/assets/rbac-select_primary_role-fr.png)

Les rôles additionels sont assignés à l'utilisateur en aller à la page *Modifier l'utilisateur* et cliquer sur *Rôles additionels* dans l'encadré.

![additional roles page](/assets/rbac-additional_roles-fr.png)

Les rôles d'environnment sont assignés à l'utilisateur lorsque ajouter des membres à un environnement :
1. Naviguer au service souhaité.
1. Cliquer en le menu de trois points à la droite de l'environnement souhaitée.
1. Sélectionner *Gérer les membres*.
1. Dans la page suivante, saisir le nom de l'utilisateur à ajouter dans le champ *Ajouter un membre à l'environnement*.

![edit environment members page](/assets/rbac-list_of_env_roles-fr.png)

---
[Cas pratiques - Basiques](rbac-use-cases-basic.md)

[Cas pratiques - Avancés](rbac-use-cases-advanced.md)
