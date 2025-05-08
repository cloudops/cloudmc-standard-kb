---
title: "AWS: Déployer RDS"
slug: aws-deployer-rds
---


## À propos de cette tâche

Cet article vous guidera à travers les étapes de déploiement de RDS et contient également les prérequis ainsi qu'une méthode de test.

## Avant de commencer

- Vous devez avoir un VPC dans l'environnement cible
- Il doit y avoir au moins deux sous-réseaux avec des CIDR non chevauchants dans le VPC
- Les sous-réseaux doivent être dans des zones de disponibilité distinctes
- Pour tester après le déploiement, vous devez avoir une instance dans le même sous-réseau que le point d'accès de la base de données

## Procédure

Créer un groupe de sous-réseaux de base de données

1. Accédez à l'environnement AWS cible et cliquez sur l'onglet **Bases de données**, puis cliquez sur l'élément **Groupes de sous-réseaux DBs**.

2. Cliquez sur le bouton **Ajouter un groupe de sous-réseaux DB**. La page **Ajouter un groupe de sous-réseaux DB** s'affiche.

3. Entrez un nom et une description pour le groupe de sous-réseaux.

4. Sélectionnez le VPC cible dans le menu contextuel **VPC**.

5. Sélectionnez les sous-réseaux cibles dans le menu contextuel **Sous-réseaux**. 

    Vous devez sélectionner au moins deux sous-réseaux avant de pouvoir continuer.

6. Cliquez sur le bouton **Valider** pour enregistrer le groupe de sous-réseaux de base de données.

Déployer l'instance de base de données

7. Cliquez sur l'élément **Bases de données**, puis cliquez sur le bouton **Ajouter une base de données**.

8. Lorsque l'assistant **Ajouter une base de données** s'affiche, sous la section **Paramètres généraux**, entrez un nom pour l'instance de base de données et sélectionnez un type de moteur de base de données. Cliquez sur **Suivant**.

9. Dans la section **Type d’instance**, sélectionnez le type d’instance sur lequel déployer la base de données, puis cliquez sur **Suivant**.

10. Lorsque la section **Stockage** apparaît, sélectionnez le type de volume et la taille à allouer pour le volume racine de l'instance. Vous pouvez également choisir d'activer la mise à l'échelle automatique du stockage, après quoi un champ de texte apparaîtra dans lequel vous pourrez saisir la taille maximale à laquelle mettre à l'échelle. Cliquez sur **Suivant**.

11. Dans la section **Réseau**, sélectionnez le groupe de sous-réseaux que vous avez créé précédemment. Cliquez sur **Suivant**.

12. La section **Identifiants** vous permet d'entrer un nom d'utilisateur et un mot de passe pour l'utilisateur principal dans la base de données. 

**Attention :**  Veuillez prendre en note le mot de passe dans un endroit sûr, car il ne peut pas être récupéré. Si vous perdez le mot de passe, vous devrez le réinitialiser.

13. Cliquez sur le bouton **Suivant**. Vérifiez les paramètres que vous avez sélectionnés dans toutes les sections.

14. Cliquez sur le bouton **Valider** pour créer l'instance de base de données. 

**Remarque :** le déploiement peut prendre plusieurs minutes.

Tester la connectivité

15. Une fois la base de données créée, allez à l'onglet **Bases de données**, cliquez sur la base de données pour voir ses détails et allez à la section **Point d'accès**. 

La section **Point d'accès** énumère le nom de domaine et le numéro de port que vous devez utiliser pour accéder à l'instance de base de données.

16. Utilisez le client de base de données approprié avec le nom d'utilisateur et le mot de passe que vous avez définis dans la section **Identifiants** pour vous connecter à l'instance de base de données.


## Résultats

- La nouvelle base de données RDS a été créée et apparaît dans l'onglet **Bases de données**.
- Vous avez vérifié la connectivité en vous connectant à l'instance avec le point d'accès et les identifants appropriés.
- L'instance de base de données est maintenant prête à être mise en service.

