---
title: "AWS: Add a volume"
slug: aws-add-a-volume
---


## À propos de cette tâche

Cet article vous guidera tout au long du processus d'ajout d'un nouveau volume à un environnement AWS.

## Avant de commencer

- Votre environnement AWS doit déjà exister

## Procédure

1. Accédez à l'environnement souhaité. La page **Instances** s'affiche.

2. Cliquez sur l'élément **Volumes**. Une liste des volumes de cet environnement s'affiche.

3. Cliquez sur le bouton **Ajouter un volume**. L'assistant **Ajouter un volume** s'affiche.

4. Configurez le nouveau volume :

     1. Saisissez un nom dans le champ **Nom** ou acceptez la valeur par défaut.

     2. Sélectionnez le type de volume à créer.

     3. Entrez le nombre de gigaoctets à allouer au nouveau volume dans la zone de texte **Taille**. Le volume doit être un nombre entier.

     4. Sélectionnez la zone de disponibilité dans laquelle le nouveau volume doit être créé.

         Le choix de la zone de disponibilité déterminera les instances auxquelles le nouveau volume pourra être rattaché.

5. \(Facultatif\) Vous pouvez attacher automatiquement le nouveau volume à une instance existante :

     1. Cliquez sur **Attacher un volume à une instance existante**.

     2. Une liste d'instances dans la zone de disponibilité sélectionnée apparaîtra. Sélectionnez l'instance souhaitée.

     3. Saisissez le nom de l'appareil souhaité dans la zone de texte intitulée **Nom du périphérique**.

6. Cliquez sur le bouton **Valider**.


## Résultats

- Le volume de la taille spécifiée est créé dans l'environnement actif
- Il existe dans la zone de disponibilité sélectionnée
- Si une instance a été sélectionnée, le volume est automatiquement attaché à cette instance
- Le volume est répertorié dans l'écran **Volumes** de l'onglet **Calcul**

## Exemple : Ajouter un volume

### À propos de cette tâche

Dans cet exemple, nous allons ajouter un nouveau volume à l'environnement AWS `production` d'Acme. Nous allons ajouter un volume de 10 Go à usage général à la zone de disponibilité `us-east-1b` et l'associer automatiquement à notre instance `acme-prod-db01`.

### Avant de commencer

- L'environnement de `production` d'Acme doit déjà exister
- L'instance `acme-prod-db01` doit déjà exister dans la zone de disponibilité `us-east-1b`

### Procédure

1. Accédez à l'environnement de `production` d'Acme. La page **Instances** s'affiche.

2. Cliquez sur l'élément **Volumes**. Une liste des volumes de l'environnement s'affiche.

3. Cliquez sur le bouton **Ajouter un volume**. L'assistant **Ajouter un volume** s'affiche.

4. Configurez le nouveau volume :

     1. Saisissez `acme-prod-vol01` dans le champ **Nom**.

     2. Sélectionnez `SSD à usage général (gp2)` pour le type de volume.

     3. Saisissez `10` dans la zone de texte **Taille**.

     4. Sélectionnez la zone de disponibilité `us-east-1b`

5. Nous allons configurer le nouveau volume à rattacher à notre instance :

     1. Cliquez sur **Attacher un volume à une instance existante**.

     2. Sélectionnez `acme-prod-db01` dans la liste des instances.

     3. Entrez `/dev/sdf` dans la zone de texte intitulée **Nom du périphérique**.

6. Cliquez sur le bouton **Valider**.


### Résultats

- Notre nouveau volume `acme-prod-vol01` de 10 Go est créé dans l'environnement de `production` Acme
- Il existe dans la zone de disponibilité `us-east-1b`
- Le volume a été automatiquement attaché à l'instance `acme-prod-db01`
- Le volume est listé dans l'écran **Volumes** de l'onglet **Calcul**

