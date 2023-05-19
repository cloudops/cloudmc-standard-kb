---
title: "AWS: Ajouter un VPC"
slug: aws-ajouter-un-vpc
---


## À propos de cette tâche

Cet article vous guidera tout au long du processus d'ajout d'un nouveau VPC à un environnement AWS.

## Avant que tu commences

- Votre environnement AWS doit déjà exister
- Si vous ne souhaitez pas utiliser les valeurs par défaut fournies par le système, vous devez disposer du nom et du CIDR que vous souhaitez attribuer au nouveau VPC

## Procédure

1. Cliquez sur le bouton **Ajouter un réseau VPC**. La page **Ajouter un réseau VPC** s'affiche.

2. Entrez un nom pour le nouveau VPC dans le champ **Nom** ou acceptez la valeur par défaut.

3. Entrez le CIDR souhaité pour le nouveau VPC dans le champ **CIDR** ou acceptez la valeur par défaut.

     Le CIDR exprime la taille et la plage d'adresses IP à utiliser pour définir le nouveau VPC. Voir [VPC](aws-vpcs.md) pour plus de détails.

     Le système affichera une erreur si un CIDR non valide est fourni.

4. Cliquez sur **Valider**.


## Résultats

- Le VPC est créé et peut être utilisé pour ajouter des sous-réseaux
- Il a la plage IP spécifiée par le CIDR
- Le VPC est listé dans l'onglet **Résautique**

## Exemple : Ajouter un VPC

### À propos de cette tâche

Dans cet exemple, nous allons ajouter un nouveau VPC à l'environnement AWS `production` d'Acme. Nous souhaitons avoir un VPC plus petit que celui par défaut, nous allons donc utiliser un CIDR avec un masque de sous-réseau de /26.

### Avant que tu commences

- L'environnement de `production` d'Acme doit déjà exister

### Procédure

1. Accédez à l'environnement de `production` d'Acme, puis cliquez sur **Réseautique**.

2. Cliquez sur le bouton **Ajouter un réseau VPC**. La page **Ajouter un réseau VPC** s'affiche.

3. Saisissez `acme-prod-vpc01` dans le champ **Nom**.

4. Saisissez `172.16.0.0/26` dans le champ **CIDR**.

     Cela nous donnera la plus petite plage IP souhaitée de 64 adresses, commençant à 172.16.0.0 et se terminant à 172.16.0.63.

5. Cliquez sur **Valider**.


### Résultats

- Notre nouveau VPC `acme-prod-vpc01` est créé et peut être utilisé pour créer des sous-réseaux
- Le VPC a la plage IP de 172.16.0.0 à 172.16.0.63
- Il est répertorié dans l'onglet **Réseautique**

