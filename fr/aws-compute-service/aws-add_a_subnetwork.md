---
title: "AWS: Ajouter un sous-réseau"
slug: aws-ajouter-un-sous-reseau
---


## À propos de cette tâche

Cet article vous guidera tout au long du processus d'ajout d'un nouveau sous-réseau à votre VPC AWS.

## Avant de commencer

- Vous devez avoir un VPC dans votre environnement AWS
- La plage IP du VPC doit avoir un bloc qui n'est pas attribué à un autre sous-réseau
- Si vous ne souhaitez pas utiliser les valeurs par défaut fournies par le système, vous devez disposer du nom, de la plage IP et de la zone de disponibilité AWS que vous souhaitez attribuer au nouveau sous-réseau

## Procédure

1. Accédez à l'environnement souhaité, puis cliquez sur **Réseautique**.

2. Recherchez le VPC souhaité et cliquez sur l'icône d'engrenage dans la section **Sous-réseaux**. La page **Sous-réseaux** s'affiche.

3. Cliquez sur le bouton **Ajouter un sous-réseau**. La page **Ajouter un sous-réseau** s'affiche.

4. Saisissez un nom pour le nouveau sous-réseau dans le champ **Nom** ou acceptez la valeur par défaut.

5. Entrez la plage IP souhaitée, en utilisant la notation CIDR, dans le champ **CIDR**.

     Le CIDR du sous-réseau doit exister entièrement dans le CIDR du VPC, et il ne doit pas chevaucher le CIDR de tout autre sous-réseau au sein du même VPC. Voir [Sous-réseaux](aws-subnetworks.md) pour plus d'informations.

     Le système affichera une erreur si un CIDR non valide est fourni.

6. Sélectionnez la zone de disponibilité souhaitée dans le menu contextuel **Zone de disponibilité** ou acceptez la valeur par défaut.

7. Cliquez sur le bouton **Valider**.


## Résultats

- Le sous-réseau est créé, et peut être utilisé pour ajouter des instances
- Il a la plage IP spécifiée par le CIDR
- Le sous-réseau est listé dans l'écran **Sub-réseaux** du VPC dans lequel il a été créé

## Exemple : Ajouter un sous-réseau

### À propos de cette tâche

Dans cet exemple, nous allons ajouter un sous-réseau au VPC `acme-prod-vpc01`. Nous voulons utiliser seulement la moitié de la plage IP, nous allons donc spécifier une taille de réseau de /27.

### Avant de commencer

- Le VPC `acme-prod-vpc01` doit déjà exister dans l'environnement AWS `production`.

### Procédure

1. Accédez à l'environnement de `production` d'Acme, puis cliquez sur **Réseautique**.

2. Recherchez le VPC `acme-prod-vpc01` et cliquez sur l'icône d'engrenage dans la section **Sous-réseaux**. La page **Sous-réseaux** s'affiche.

3. Cliquez sur le bouton **Ajouter un sous-réseau**. La page **Ajouter un sous-réseau** s'affiche.

4. Saisissez `acme-prod-net-frontend` dans le champ **Nom**.

5. Entrez `172.16.0.0/27` dans le champ CIDR.

     Cela nous donnera le sous-réseau souhaité, composé de 32 adresses IP allant de 172.16.0.0 à 172.16.0.31.

6. Acceptez la zone de disponibilité par défaut.

7. Cliquez sur le bouton **Valider**.


### Résultats

- Notre nouveau sous-réseau `acme-prod-net-frontend` est créé et peut être utilisé pour ajouter des instances
- Il a la plage IP de 172.16.0.0 à 172.16.0.31
- Le sous-réseau est listé dans l'écran **Sous-réseaux** du VPC `acme-prod-vpc01`

