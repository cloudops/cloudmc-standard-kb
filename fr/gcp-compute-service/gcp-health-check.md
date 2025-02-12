---
title: "GCP: Vérifications d'état"
slug: gcp-verifications-d-etat
---


Les vérifications de l'état de Google Cloud Platform vous permettent de définir les critères de disponibilité d'une instance fournissant un service de backend. Une vérification d'état est appliquée à un groupe d'instances lors de la configuration d'un service de backend GCP. Une fois la vérification de l'état est active, GCP envoie une simple requête à l'instance cible toutes les 5 secondes. Si l'instance répond avec un HTTP 200 OK, l'instance est considérée comme opérationnel. Si la demande expire au bout de 5 secondes ou si la réponse est autre que HTTP 200 OK, l'instance est considérée comme non opérationnelle et elle ne recevra aucune demande entrante tant qu'elle ne retournera pas à un état opérationnel.

Les vérifications d'état peuvent être gérées en accédant à votre environnement GCP dans CloudOps, en cliquant sur l'onglet **Calcul** et en cliquant sur l'élément **Vérification d'état**.

### Créer une vérification d'état

1. À partir de la page *Vérification d'état*, cliquez sur le bouton *Ajouter une vérification d'état*.
1. Entrez un nom ou acceptez la valeur par défaut, et entrez une description si vous le souhaitez.
1. Sélectionnez le protocole à utiliser (HTTP ou HTTPS) et saisissez le numéro de port auquel se connecter sur l'instance backend.
1. Cliquez sur *Valider*. La page *Vérifications d'état* apparaîtra et la nouvelle vérification d'état sera répertoriée.

Par défaut, CloudOps créera une vérification de l'état qui interroge le répertoire racine ("/"). GCP permet aux vérifications d'état d'interroger d'autres chemins d'accès. CloudOps affichera le chemin d'accès de la demande d'une vérification de l'état dans la liste de la page *Vérification d'état*.

### Supprimer une vérification d'état

Une vérification d'état ne peut pas être supprimée si elle est utilisée par un service de backend.

1. À partir de la page *Vérifications d'état*, recherchez la vérification d'état souhaitée et cliquez sur le menu *Action* à l'extrême droite de l'entrée. Cliquez sur *Supprimer*.
1. Une boîte de dialogue de confirmation apparaît. Cliquez sur *Valider*.
1. La vérification de l'état sera supprimée de l'environnement GCP.
