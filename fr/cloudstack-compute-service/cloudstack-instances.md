---
title: "CloudStack: Instances"
slug: cloudstack-instances
---


Les instances constituent un type fondamental d'infrastructure fourni par CloudStack. Cet article aborde le concept d'instances et la manière dont elles sont gérées dans la plateforme.

Les instances sont répertoriées dans la section **Instances** de l'environnement CloudStack sélectionné.

## Aperçu

Semblable à d'autres plates-formes cloud, CloudStack vous offre la possibilité d'exécuter des instances. Une fois qu'une instance est provisionnée, elle peut être utilisée pour exécuter les différents composants de vos applications.

Une instance est toujours basée sur une image prédéfinie, qui ne peut pas être modifiée une fois l'instance déployée. L'image peut être un modèle contenant un système d'exploitation entièrement installé, ou il peut s'agir d'un ISO, l'équivalent virtuel d'un CD-ROM ou d'un DVD qui peut être attaché à une nouvelle instance et utilisé pour installer un système d'exploitation.

CloudStack prend en charge deux types d'instances. Les **machines virtuelles** sont des instances qui existent sur un pool partagé de ressources de calcul. Plusieurs machines virtuelles peuvent s'exécuter simultanément sur un seul hôte physique et sont gérées par un hyperviseur. En revanche, une instance **physique** est un hôte physique unique et complet. L'environnement dans lequel l'instance physique est allouée est le seul locataire et la ressource n'est partagée avec aucun autre client.

Le choix entre les machines virtuelles et les physiques dépend des besoins particuliers de votre entreprise. Les machines virtuelles sont économiques, rapides à provisionner, redimensionner et détruire, mais elles existent dans un environnement informatique partagé. Les instances physiques assurent une isolation physique pour les charges de travail ayant des exigences de sécurité complexes, et ce niveau d'isolation réduit également la possibilité que la charge de travail soit affectée dans un scénario de « voisin bruyant ». Toutefois, les instances physiques ont une taille fixe basée sur le matériel disponible et ne peuvent pas être redimensionnées.

Une instance se voit également attribuer une taille. Chaque taille est un ensemble de processeurs virtuels et de mémoire. La taille d'une machine virtuelle peut être modifiée selon les besoins, ne nécessitant qu'un redémarrage de l'instance. Un disque pour le système d'exploitation sera créé pour chaque nouvelle instance. La capacité du disque du système d'exploitation est déterminée par l'image sélectionnée. Le disque du système d'exploitation peut être étendu ultérieurement si nécessaire. Des disques de stockage supplémentaires peuvent être ajoutés à l'instance à tout moment.

## Configurer une instance

Au moment de la configuration, d'autres options de déploiement sont disponibles. Un volume existant peut être attaché à l'instance nouvellement créée, ou un volume supplémentaire peut être créé et attaché. Un ensemble de ports TCP publics couramment utilisés peut être automatiquement ouvert à l'Internet public. L'automatisation peut être utilisée pour configurer le logiciel selon les besoins après le premier lancement de la nouvelle instance par le système. Si des groupes d'affinité ont été définis pour l'environnement, l'instance peut être attribuée à un seul lors du lancement initial. Il est également possible de créer simultanément un lot d'instances ayant des caractéristiques identiques, ne différant que par leur nom. La création par lots est utile pour le traitement parallèle et d'autres applications nécessitant une puissance de calcul importante.

L'utilisateur peut fournir au système une clé SSH publique à installer sur l'instance lors du déploiement. L'utilisateur peut ensuite se connecter à l'instance à l'aide de la clé SSH privée correspondante. Si aucune clé SSH n'est fournie au moment de la configuration, le système fournira à l'utilisateur un mot de passe à utiliser lors de la connexion à l'instance. Le nom d'utilisateur est personnalisable au moment de la configuration.

De plus, lors de la configuration, un estimateur de coûts apparaîtra en bas de page. L'estimateur de coûts répertorie les options de configuration sélectionnées et leurs coûts individuels, ainsi qu'un total estimé horaire et mensuel. Il sera mis à jour dynamiquement à mesure que vous sélectionnez la configuration souhaitée pour votre instance.

![Capture d'écran de la page Ajouter une instance avec l'estimateur de coût affiché](/assets/cloudstack-add-an-instance.png)

## Liste des instances

Les instances sont répertoriées dans la section **Instances** de l'environnement CloudStack sélectionné.

![Une capture d'écran de la page CloudStack Instances, avec des points numérotés indiquant les fonctionnalités intéressantes](/assets/cloudstack-instances-numdot.png)

1. **Liste des instances CloudStack**

Une liste de toutes les instances de l'environnement CloudStack sélectionné apparaît ici dans cette zone.

2. **Boîte de recherche**

Saisissez dans la boîte de recherche pour filtrer les instances. Le système recherchera dans les champs Instance, État, Réseautiqu et Date de création, ainsi que dans diverses propriétés des instances qui ne sont pas répertoriées sur cette page, notamment l'ID, la zone, la clé SSH et d'autres.

3. **Ajouter une instance**

Cliquer sur ce bouton ouvrira la page **Ajouter une instance**.

4. **Entrée instance**

Chaque entrée comprend le nom de l'instance, son état actuel, la configuration réseautique et la date de création. Cliquez sur une entrée pour accéder à une page contenant les détails de la configuration et une liste de toutes les opérations pour cette instance individuelle.

5. **Menu des actions cachées**

Chaque entrée de la liste des instances possède un menu des actions cachées. Cliquez sur le menu des actions cachées pour accéder à une liste des opérations fréquemment utilisées pour l'instance.