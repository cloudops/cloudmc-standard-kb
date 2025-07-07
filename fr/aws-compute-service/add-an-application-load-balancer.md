---
title: "AWS: Ajouter un équilibreur de charge d'application"
slug: aws-ajouter-équilibreur-de-charge-d-application
---


## À propos de cette tâche

Cet article vous guidera à travers les étapes nécessaires au déploiement d’un équilibreur de charge d’application.

## Avant de commencer

- Vous devez avoir un environnement AWS avec un groupe cible

## Procédure

1. Accédez à votre environnement AWS, puis à **Équilibrage de charge** &gt; **Équilibreurs de charge d'application**, puis cliquez sur le bouton **Ajouter un équilibreur de charge**.

2. Lorsque l'assistant **Ajouter un équilibreur de charge** s'affiche, entrez un nom pour le nouvel équilibreur de charge dans le champ **Nom**.

3. Dans le champ **Méthode**, sélectionnez si l'équilibreur de charge recevra le trafic public provenant d'Internet ou s'il recevra le trafic provenant d'une adresse IP privée.

4. Dans le champ **Type d'adresse IP**, sélectionnez **IPv4** pour communiquer avec des cibles utilisant IPv4, ou **Dualstack** pour communiquer avec des cibles utilisant IPv6.

5. Cliquez sur le bouton **Suivant**.

6. Dans la section **Cartographie du réseau**, sélectionnez le VPC avec les cibles souhaitées, puis sélectionnez au moins deux sous-réseaux vers lesquels l'équilibreur de charge enverra le trafic.

7. Cliquez sur le bouton **Suivant**.

8. Dans la section **Groupes de sécurité**, sélectionnez un groupe de sécurité à appliquer au nouvel équilibreur de charge, puis cliquez sur le bouton **Suivant**.

9. Dans la section **Écouteurs et routage**, sélectionnez le protocole, précisez le numéro de port vers lequel envoyer le trafic et sélectionnez le groupe cible avec les cibles enregistrées. Vous pouvez ajouter plusieurs auditeurs.

10. Cliquez sur le bouton **Suivant**.

11. \(Optionnel\) Dans la section **Étiquettes d'équilibreur de charge**, entrez une paire nom-valeur avec laquelle étiqueter l'équilibreur de charge.

12. Cliquez sur le bouton **Suivant**.

13. Vérifiez les paramètres et cliquez sur le bouton **Valider** pour créer l’équilibreur de charge.


## Résultats

- L'équilibreur de charge d'application sera créé avec le(s) groupe(s) cible(s) spécifié(s)
- L'équilibreur de charge apparaît maintenant sur la page **Équilibreurs de charge d'application**
- Une fois l'approvisionnement terminé, l'équilibreur de charge sera dans l'état **Actif**