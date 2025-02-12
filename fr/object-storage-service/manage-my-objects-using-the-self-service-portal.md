---
title: "Gérer mes objets avec le portail de libre-service"
slug: gerer-mes-objets-avec-le-portail-de-libre-service
---


Il existe plusieurs façons de gérer vos objets dans CloudOps, en utilisant [l'API de Swift](https://docs.openstack.org/api-ref/object-store/), avec le [CLI Swift](https://ops.cloud.ca/hc/service-de-stockage-object/gerer-mes-objets-avec-outil-de-ligne-de-commande-swift) ou en utilisant le portail.

### Gérer les récipients

CloudOps possède une vue pour pouvoir gérer les objets de façon simple et intuitive. On y accède en cliquant sur **Services** dans les menu à gauche, en cliquant sur **Object Storage** et en sélectionnant un environnement dans la liste.

L'image suivante montre la liste des récipients dans un environnement. Pour chaque récipient, vous pouvez voir leur niveau d'accès (public ou privé), leur stratégie de stockage et leur taille totale. Vous pouvez également ajouter ou retirer des récipients depuis cette vue.

![Liste des récipients](/assets/managing-objects-portal-fr-1.png)

Quand on clique sur **Ajouter un récipient** en haut à droite, on vous demandera:
- De donner un nom à votre récipient
- De sélectionner la stratégie de stockage
- Par défault, les nouveaux récipients sont privés. Nous offrons la possibilité de rendre un récipient accessible publiquement pour permettre l'accès aux objets sans aucune authentification (pour cela, cliquez sur "Rendre accessible publiquement")

### Gérer les objets

Quand vous cliquez sur un récipient, vous arrivez sur une page qui montre la liste des objets actuellement stockés dans le récipient. C'est aussi à partir de cette page que vous pouvez téléverser de nouveaux objets.

Depuis cette page, vous pouvez aussi récupérer l'URL d'un objet pour l'utiliser dans votre application, télécharge un objet, le renommer ou le supprimer. La liste donne aussi des informations à propos du type de chaque objet ainsi que leur taille.

![Menu d'Action d'objet](/assets/managing-objects-portal-fr-2.png)

Notez que vous pouvez également cliquer sur C**réer un dossier** (en cliquant sur les 3 points à droite de Téléverser) pour créer un pseudo-dossier. Si vous voulez ajouter un nouvel objet au récipient, cliquez sur **Téléverser**: ceci va ouvrir une nouvelle fenêtre pour vous laisser sélectionner vos fichiers. Nous supportons la sélection de plusieurs fichiers à la fois, mais ils seront téléversés les uns après les autres. Vous pouvez aussi simplement déposer un fichier dans la partie principale de l'écran pour le téléverser dans le récipient.

![Téléverser un objet](/assets/managing-objects-portal-fr-3.png)
