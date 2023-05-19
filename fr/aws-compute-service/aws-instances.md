---
title: "AWS: Instances"
slug: aws-instances
---


Semblable à d'autres plates-formes cloud, AWS vous fournit l'infrastructure nécessaire pour exécuter des machines virtuelles. Ces machines virtuelles sont appelées instances. Une instance est basée sur une image prédéfinie appelée **[AMI](aws-amis.md)**, qui ne peut pas être modifiée une fois l'instance déployée. Différents ensembles de spécifications sont regroupés sous forme de types d'instance. Chaque type d'instance est un ensemble de différentes tailles de vCPU, de mémoire et d'un volume de stockage racine. Pour plus de détails, consultez [Types d'instances Amazon EC2](https://aws.amazon.com/fr/ec2/instance-types/) dans la documentation AWS.

Lors du déploiement d'une instance, une région AWS doit être sélectionnée. La région détermine quels sous-réseaux, volumes, AMI et autres ressources seront disponibles pour les nouvelles instances.

À l'aide de règles de mise à l'échelle automatique, vous pouvez définir les conditions dans lesquelles le système AWS déploiera automatiquement des instances supplémentaires, si votre application nécessite davantage de ressources de calcul. Les instances ajoutées auront toutes un nom et une configuration identiques. AWS créera jusqu'au nombre maximal d'instances défini dans le champ **Nombre maximum d'instances** sur la page **Ajouter une instance**. AWS résilie également les instances inutiles lorsque les conditions sont remplies, jusqu'à la valeur spécifiée dans le champ intitulé **Nombre minimum \# d'instances**, également sur la page **Ajouter une instance**. Pour plus de commodité, ce guide fera référence à la création d'une seule instance, mais si vous choisissez de créer plusieurs instances, la configuration sélectionnée sera appliquée à toutes les instances de la même manière.

Pour vous connecter à une instance, utilisez la paire de clés SSH créée automatiquement lors de la création de l'instance. La clé SSH privée est votre seul moyen de vous connecter à l'instance et doit être stockée et installée en toute sécurité dans l'application SSH que vous utiliserez pour vous connecter à l'instance. Lorsque plusieurs instances sont créées via la mise à l'échelle automatique, vous pouvez utiliser cette clé SSH privée pour vous connecter à chaque instance.

**Important :** Vous devez immédiatement stocker en toute sécurité la clé SSH privée. Il ne sera stocké nulle part dans l'interface utilisateur CloudMC et ne pourra pas être récupéré une fois la notification effacée du panneau. Vous ne pouvez pas vous connecter à une instance sans cette clé. En cas de perte, vous devrez suivre une procédure de récupération, qui nécessite le redémarrage de l'instance.

Les instances sont répertoriées sous l'onglet **Calcul** de votre environnement AWS, dans la section **Instances**.

**Sujet parent :** [AWS : Calcul](aws-compute.md)

