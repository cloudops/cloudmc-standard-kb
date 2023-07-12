---
title: "CloudStack: Importer et déployer à partir d'une image ISO"
slug: cloudstack-importer-iso
---


Cet article vous guidera à travers les étapes de création d'une image à partir d'une ISO importée, puis de déploiement d'une nouvelle instance à partir de cette image. La création de vos propres images à partir d'ISO vous permet d'étendre votre choix de systèmes d'exploitation au-delà de l'offre standard, y compris les appliances virtuelles et autres systèmes autonomes. Vous devez être familiarisé avec des concepts tels que les images ISO et [travailler avec des instances](working-with-instances.md).

## Prérequis
   - Vous devez avoir une image ISO initialisable.
   - L'image doit être récupérable via une URL HTTP ou HTTPS.
   - Le système d'exploitation de l'image doit être compatible avec l'architecture x86 32 bits ou 64 bits.
   - Votre compte utilisateur doit être membre de l'environnement cible et avoir le rôle d'environnement **Éditeur** ou **Propriétaire** attribué.

## Étapes

Cette procédure est divisée en deux sections :
   - Importer l'image ISO
   - Créer une instance à partir de l'image

### Importer l'image ISO
1. Accédez à l'environnement cible et cliquez sur l'onglet **Images**.
1. Cliquez sur le bouton intitulé *Importer*, puis sélectionnez *Importer ISO* dans le menu contextuel.
1. Sur la page *Importer ISO* :
    - Saisissez un nom et une description à afficher dans l'interface utilisateur pour cette image.
    - Entrez l'URL à partir de laquelle le système peut récupérer l'image ISO.
    - Cochez la case *Initialisable* pour afficher le menu contextuel *Système d'exploitation*.
    - Sélectionnez le système d'exploitation qui correspond le mieux au système d'exploitation de l'image. Si le système d'exploitation est inconnu, une option générique telle que **Other (64-bit)** peut suffire pour votre image.
    - Ne cochez pas la case *Permet la génération d'URL de téléchargement*.
1. Cliquez sur *Valider*. Le système commencera la récupération de l'image et l'onglet **Images** apparaîtra. La récupération prendra plusieurs minutes.
1. Lorsque l'image ISO a été entièrement récupérée, vous serez alerté via le panneau Notifications que l'ISO a été importée. La nouvelle image sera également répertoriée dans l'onglet **Images**.

### Créer une instance à partir de l'image
1. Accédez à l'onglet **Instances**.
1. Cliquez sur le bouton intitulé *Ajouter une instance virtuelle*.
1. Saisissez un nom pour la nouvelle instance dans le champ **Nom**.
1. Sélectionnez le réseau sur lequel l'instance sera déployée.
1. Dans la section **Image**, cliquez sur *ISOs d'environnement*.
1. Sélectionnez l'image souhaitée.
1. Apportez toute autre modification de configuration souhaitée, puis cliquez sur le bouton *Valider*.

## Résultat
- L'image importée apparaîtra désormais dans la section *ISOs d'environnement* de la page *Ajouter une instance virtuelle*.
- Une nouvelle instance construite à partir de cette image a été déployée dans l'environnement cible.
- L'image sera également répertoriée dans l'onglet **Images**.
- L'image importée peut être testée en démarrant l'instance déployée et en affichant la console pour valider qu'elle fonctionne comme prévu.

## Exemple

### Configuration

Dans cet exemple, nous allons importer une image ISO dans notre environnement `env-staging` dans le service `Compute - Québec`, et utiliser l'image résultante pour déployer une nouvelle instance. L'exemple commence sur l'onglet **Images** de notre environnement et suppose que le fichier image ISO a été stocké sur un service tel que le [stockage objet](../object-storage-service/what-is-object-storage.md).

#### Importer l'image ISO

1. Cliquez sur le bouton intitulé *Importer*, puis sélectionnez *Importer ISO* dans le menu contextuel.
1. Sur la page *Importer ISO* :
    - Saisissez `Ubuntu 20.04` dans la zone intitulée **Nom** et `Ubuntu 20.04 de l'ISO` dans le champ **Description**.
    - Saisissez l'URL de l'image ISO.
    - Cochez la case étiquetée *Initialisable*.
    - Sélectionnez **Ubuntu 19.04 (64-bit)** dans le menu contextuel *Système d'exploitation*.
    - Ne cochez pas la case *Permet la génération d'URL de téléchargement*.
1. Cliquez sur *Valider*. Le système commencera la récupération de l'image et l'onglet **Images** apparaîtra. La récupération prendra plusieurs minutes.
1. Lorsque l'image ISO a été entièrement récupérée, nous voyons dans le panneau Notifications que l'ISO a été importée.

#### Créer une instance à partir de l'image

1. Accédez à l'onglet **Instances**.
1. Cliquez sur le bouton intitulé *Ajouter une instance virtuelle*.
1. Saisissez `acme-ubuntu01` dans le champ **Nom**.
1. Sélectionnez le réseau `acme-net-backend`.
1. Dans la section **Image**, cliquez sur *ISOs d'environnement*.
1. Sélectionnez l'image intitulée **Ubuntu 20.04**.
1. Faites défiler jusqu'au curseur **Taille du volume principal** et déplacez le curseur sur 10 Go.
1. Laissez tous les autres paramètres inchangés et cliquez sur le bouton *Valider*.

### Tester

Nous allons tester l'ISO importé en regardant l'onglet **Instances** pour vérifier que `acme-ubuntu01` est marqué avec la bonne étiquette d'image, puis en ouvrant une console pour voir que l'image a démarré, et enfin en vérifiant la configuration de disque pour vérifier que l'instance a été lancée avec le volume que nous avons sélectionné à la dernière étape.

1. Accédez à l'onglet **Instance**.
1. Vérifiez que l'instance `acme-ubuntu01` est balisée avec le nom de l'image **Ubuntu 20.04**.
1. Cliquez sur le menu à trois points à l'extrême droite de l'entrée pour `acme-ubuntu01`, et sélectionnez **Ouvrir console** dans le menu contextuel.
1. Lorsque la fenêtre de la console apparaît, nous voyons que la nouvelle instance a démarré sur le gestionnaire d'installation Ubuntu.
1. Cliquez sur les invites du gestionnaire d'installation jusqu'à ce que vous arriviez à l'écran *Type d'installation*. Vérifiez que la taille du périphérique de disque `/dev/xvda` correspond à la taille sélectionnée lors de la création de l'instance (10 Go).
