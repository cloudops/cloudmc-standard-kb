---
title: "AWS: Ajouter un instance"
slug: aws-ajouter-un-instance
---


## À propos de cette tâche

Cet article vous guidera tout au long du processus d'ajout d'une nouvelle instance à un environnement AWS. L'interface CloudMC fournit un assistant en plusieurs étapes pour sélectionner une configuration, et l'instance \(ou les instances\) sera créée après la dernière étape de l'assistant.

## Avant de commencer

- Vous devez avoir un VPC configuré
- Le VPC doit avoir un sous-réseau configuré
- Le sous-réseau doit avoir au moins une adresse IP disponible
- Le nombre d'instances qui doivent être initialement déployées
- Le nombre maximum d'instances à autoriser lors de Auto Scaling

## Procédure

1. Accédez à l'environnement souhaité. La page **Instances** s'affiche.

2. Cliquez sur le bouton **Ajouter une instance**. L'assistant **Ajouter une instance** s'affiche.

3. Configurez les paramètres de base de l'instance.

     1. Saisissez un nom dans le champ **Nom** ou acceptez la valeur par défaut.

     2. Sélectionnez la région où l'instance doit être déployée.

     3. Sélectionnez l'image à utiliser pour déployer l'instance.

     4. Sélectionnez le type d'instance souhaité dans le menu contextuel **Type d'instance**.

     5. Sélectionnez le nombre minimum et maximum souhaité d'instances à déployer.

     Cliquer sur **Suivant** pour continuer.

4. Configurez les paramètres de sécurité de l'instance.

     1. Entrez un nom pour la nouvelle paire de clés SSH dans le champ **Nom de la clé** ou acceptez la valeur par défaut.

     2. Définissez un nouveau groupe de sécurité pour l'instance ou sélectionnez un ensemble prédéfini.

     Cliquer sur **Suivant** pour continuer.

5. Configurez les paramètres de mise en réseau de l'instance.

     1. Dans le menu contextuel **VPC**, sélectionnez le VPC dans lequel l'instance sera créée.

     2. Dans le menu contextuel **Sous-réseau**, sélectionnez le sous-réseau dans lequel l'instance sera créée.

     Cliquer sur **Suivant** pour continuer.

6. Configurez les paramètres de stockage de l'instance.

     Sur la page **Configuration des volumes**, vous pouvez choisir les paramètres du volume racine de la nouvelle instance.

     1. Saisissez le nom de périphérique souhaité pour le volume dans le champ **Nom du périphérique** ou acceptez la valeur par défaut.

     2. Sélectionnez le type de performance du volume dans le menu contextuel **Type de volume**.

     3. Saisissez la taille du volume en gigaoctets \(Go\) dans le champ **Taille**.

     4. Si nécessaire, cochez la case **Suppression lors de la résiliation**.

     À cette étape, vous pouvez ajouter plusieurs volumes avec le bouton **Ajouter**. Appuyer sur ce bouton fera apparaître une section de configuration des volumes supplémentaires. Entrez les paramètres souhaités en conséquence. Lors de l'ajout de plusieurs volumes, le nom du périphérique doit être unique pour chaque volume. Cliquez sur le bouton **Supprimer** pour éliminer ce volume de la liste.

     Cliquer sur **Suivant** pour continuer.

7. Sélectionnez les volumes existants à attacher.

     Sur la page **Attacher des volumes existants**, vous pouvez attacher des volumes qui existent déjà dans la zone de disponibilité de l'instance à créer.

     Plusieurs volumes peuvent être attachés à la nouvelle instance en cliquant sur le bouton **Ajouter**. Assurez-vous que chaque volume a un nom du périphérique unique.

     1. Sélectionnez le volume à attacher dans le menu contextuel **Volumes**.

     2. Saisissez le nom du périphérique souhaité dans le champ **Nom du périphérique**.

     Cliquer sur le bouton **Supprimer** élimine ce volume de la liste.

8. Cliquez sur le bouton **Valider**.

     L'écran de l'assistant se ferme et vous revenez à l'écran **Instances** de l'onglet **Calcul**. L'ajout de l'instance peut prendre quelques instants. Pendant ce temps, le panneau de notification indiquera que l'instance est en cours de création.

9. Enregistrez la clé SSH privée fournie dans la notification.

     1. Cliquez sur l'icône **cloche** pour agrandir le panneau de notification.

     2. Identifiez la notification de votre instance en recherchant le nom de l'instance.

     3. Cliquez sur l'icône **Presse-papiers** pour copier la clé SSH privée complète dans votre presse-papiers.

     4. Stockez la clé SSH privée en toute sécurité.


## Résultats

- L'instance est créée avec les options de configuration sélectionnées
- Le nombre d'instances créées est la valeur fournie dans le champ **Nombre minimum d'instances**
- L'instance sera créée dans la zone de disponibilité du sous-réseau sélectionné
- Tous les nouveaux volumes définis seront attachés à la nouvelle instance
- Tous les volumes existants spécifiés dans l'assistant seront attachés à la nouvelle instance
- L'instance est maintenant listée dans la page **Instances** de l'onglet **Calcul**
- La clé SSH privée nécessaire pour se connecter à l'instance a été stockée en toute sécurité

## Exemple : Ajouter une instance

### À propos de cette tâche

Dans cet exemple, nous allons ajouter une instance à notre environnement de `production` Acme. L'instance exécutera Ubuntu et nous la créerons dans le VPC `acme-prod-vpc01`, en utilisant le sous-réseau `acme-prod-net-frontend`, avec uniquement le volume racine attaché.

### Avant de commencer

- Le VPC `acme-prod-vpc01` doit déjà exister dans l'environnement AWS `production`
- Le sous-réseau `acme-prod-net-frontend` doit déjà exister
- Le sous-réseau doit avoir au moins une adresse IP disponible
- Une seule instance sera initialement déployée
- Nous n'autoriserons qu'une seule instance maximum, il n'y aura pas Auto Scaling

### Procédure

1. Accédez à l'environnement de `production`. La page **Instances** s'affiche.

2. Cliquez sur le bouton **Ajouter une instance**. L'assistant **Ajouter une instance** s'affiche.

3. Configurez les paramètres de base de l'instance.

     1. Saisissez `acme-prod-web01` dans le champ **Nom**.

     2. Sélectionnez la région `us-east-1`.

     3. Sélectionnez l'image `Ubuntu 20.04`.

     4. Cliquez sur le menu contextuel **Type d'instance** et saisissez `micro`, puis sélectionnez `t1.micro` dans les résultats de la recherche.

     5. Saisissez `1` dans les champs **Nombre minimum d'instances** et **Nombre maximum d'instances**.

     Cliquer sur **Suivant** pour continuer.

4. Configurez les paramètres de sécurité de l'instance.

     1. Saisissez `ssh-prod-web01` dans le champ **Nom de la clé**.

     2. Cliquez sur le bouton radio **Autoriser le trafic uniquement pour HTTP, HTTPS et SSH** et acceptez le nom et la description du groupe de sécurité par défaut.

     Cliquer sur **Suivant** pour continuer.

5. Configurez les paramètres de mise en réseau de l'instance.

     1. Dans le menu contextuel **VPC**, sélectionnez `acme-prod-vpc01`.

     2. Dans le menu contextuel **Sous-réseau**, sélectionnez `acme-prod-net-frontend`.

     Cliquer sur **Suivant** pour continuer.

6. Configurez les paramètres de stockage de l'instance.

     1. Acceptez la valeur par défaut dans le champ **Nom du périphérique**.

     2. Sélectionnez le type de performance de volume `gp2` dans le menu contextuel **Type de volume**.

     3. Saisissez `10` dans le champ **Taille**.

     4. Cochez la case **Suppression lors de la résiliation** pour supprimer automatiquement ce volume lorsque l'instance est supprimée.

     Cliquer sur **Suivant** pour continuer.

7. Sur la page **Attacher des volumes existants**, cliquez sur le bouton **Supprimer** jusqu'à ce que tous les volumes soient supprimés, le cas échéant.

8. Cliquez sur le bouton **Valider**.

     L'écran de l'assistant se ferme et vous revenez à l'écran **Instances** de l'onglet **Calcul**. L'ajout de l'instance peut prendre quelques instants. Pendant ce temps, le panneau de notification indiquera que l'instance est en cours de création.

9. Enregistrez la clé SSH privée fournie dans la notification.

     1. Cliquez sur l'icône **cloche** pour agrandir le panneau de notification.

     2. La notification supérieure doit concerner l'ajout de l'instance `acme-prod-web01`.

     3. Cliquez sur l'icône **Presse-papiers** pour copier la clé SSH privée complète dans votre presse-papiers.

     4. Stockez la clé SSH privée en toute sécurité et à un endroit où elle est accessible lors de la connexion à l'instance.


### Résultats

- Notre nouvelle instance `acme-prod-web01` est créée avec les options de configuration sélectionnées
- Une seule instance est configurée et déployée
- C'est dans la région `us-east-1`
- Il a un volume racine avec 10 Go de stockage
- Aucun autre volume n'est joint
- L'instance est désormais répertoriée dans la page **Instances** de l'onglet **Calcul**.
- La clé SSH privée nécessaire pour se connecter à l'instance a été stockée en toute sécurité

