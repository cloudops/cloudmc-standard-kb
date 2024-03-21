---
title: "Ajouter une instance"
slug: hypertec-ajouter-une-instance
---


## À propos de cette tâche

Cet article vous guidera tout au long du processus d'ajout d'une nouvelle instance à un environnement Hypertec Cloud. L'interface fournit un assistant en plusieurs étapes pour sélectionner une configuration, et l'instance \(ou les instances\) sera créée après la dernière étape de l'assistant.

## Avant de commencer

- Vous devez avoir au moins un réseau configuré
- Le réseau peut être isolé ou se trouver dans un VPC
- Le réseau doit avoir au moins une adresse IP disponible
- Accédez à l'environnement souhaité
- Cliquez sur le bouton **Ajouter une instance** pour commencer

## Procédure

1. **Réseautique**

     - Choisissez une zone et un réseau pour déployer la nouvelle instance. Le choix de la zone déterminera les réseaux et volumes disponibles plus tard dans le processus de configuration.
     - Facultativement, développez la section **Personnalisation** pour spécifier une adresse IP privée ou pour choisir une ou plusieurs règles de redirection de port courantes pour l'instance.
2. **Offres**

     - Machine virtuelle : choisissez parmi les combinaisons standard de vCPU et de mémoire, ou choisissez la vôtre.
     - Bare metal : sélectionnez parmi les configurations disponibles.
3. **Image**

     - Sélectionnez parmi une liste de modèles et d'ISO mis à disposition pour cette connexion de service.
     - Si un modèle est disponible dans différentes versions, vous pouvez accepter la version par défaut ou en sélectionner une dans le menu contextuel **Version**.
4. **Volumes**

     - Conservez la taille par défaut du volume du système d'exploitation ou choisissez la taille qui répondra à vos besoins dans le menu contextuel **Taille du volume du système d'exploitation**.
     - Vous pouvez éventuellement attacher un volume qui existe déjà dans cet environnement en le sélectionnant dans le menu contextuel **Attacher un volume**. Le volume sera automatiquement attaché à la nouvelle instance au moment du lancement. Vous devrez toujours monter le volume à l'intérieur de l'instance pour y accéder.
     - Vous pouvez éventuellement ajouter un nouveau volume et le joindre à la nouvelle instance. Sélectionnez le type de volume dans le menu contextuel **Ajouter et associer un nouveau volume**, puis choisissez la taille souhaitée dans le menu contextuel **Taille du nouveau volume**. Le nouveau volume sera automatiquement attaché à la nouvelle instance au moment du lancement. Vous devrez toujours partitionner, formater et monter le volume à l'intérieur de l'instance pour y accéder.
5. **Options supplémentaires**

     Il existe des fonctionnalités facultatives que vous pouvez choisir de configurer :

     - Choisissez une clé SSH pour l'authentification. Vous pouvez en sélectionner une qui est déjà dans le système en cliquant sur le menu contextuel intitulé **Clé SSH**, ou vous pouvez télécharger une nouvelle clé SSH publique en sélectionnant **Nouvelle clé SSH** dans le menu et en collant la clé dans la zone de texte intitulée **Clé publique**. L'authentification SSH n'est pas prise en charge pour certains types de modèles ni pour les ISO.
     - Utilisez l'automatisation pour configurer le logiciel selon vos besoins après le premier lancement de la nouvelle instance par le système. Le type d'automatisation disponible dépend du modèle sélectionné. Utilisez la zone de texte intitulée **Script** pour fournir les paramètres, les données de configuration ou le script souhaités.
     - Si un ou plusieurs groupes d'affinité ont été définis pour cet environnement, vous pouvez choisir d'associer la nouvelle instance à l'un d'entre eux en la sélectionnant dans le menu contextuel **Groupes d'affinité disponibles**.
6. **Nommer**

     - Acceptez le nom par défaut ou saisissez le nom souhaité dans le champ **Nom de l'instance\(s\)**.
     - Pour créer plusieurs instances avec la configuration sélectionnée, cliquez sur le bouton à bascule **Création par lots** et choisissez le nombre d'instances à créer. Pour différencier le lot d'instances, un suffixe numéroté sera ajouté à la fin du nom de chaque instance. Entrez le numéro à ajouter au nom de la première instance dans le champ **Suffixe de départ**, et le reste des instances sera numéroté de manière séquentielle et incrémentielle.
7. **Terminer**

     - À ce stade, un résumé de la configuration sélectionnée apparaîtra.
     - Cliquez sur le bouton **Ajouter** pour accepter la configuration.

## Résultats

- L'instance sera créée avec la configuration sélectionnée
- Si la création par lots a été activée, les instances seront créées avec des configurations identiques et nommées avec un suffixe qui incrémente séquentiellement
- La ou les instances apparaîtront sur la page **Instances**
- Les instances se lanceront automatiquement après leur provisionnement
- Si l'authentification par mot de passe a été sélectionnée, une notification d'activité apparaîtra dans le panneau Notifications avec le nom d'utilisateur et le mot de passe à utiliser pour se connecter au système et doit être enregistrée en toute sécurité.

