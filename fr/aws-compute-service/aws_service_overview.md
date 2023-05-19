---
title: "AWS: Aperçu des services"
slug: aws-apercu-des-services
---


## Résumé

CloudMC permet aux opérateurs de cloud d'accéder et de gérer l'infrastructure et les ressources qui ont été déployées sur la plate-forme Amazon Web Services \(AWS\). Cet article présente les concepts de base d'AWS et l'utilisation des ressources AWS dans CloudMC.

## Aperçu détaillé

La plate-forme AWS est un cloud public, où les clients peuvent allouer des ressources pour créer une infrastructure pour leurs applications. CloudMC fournit une interface unifiée pour accéder à AWS et à d'autres services à partir d'un portail unique. Grâce à CloudMC, les utilisateurs peuvent gérer :

-   [Ressources de calcul et de stockage](aws-compute.md) :
    -   [Instances](aws-instances.md)
    -   [Amazon Machine Images \(AMI\)](aws-amis.md)
    -   [Volumes](aws-volumes.md)
-   [Ressources de réseautage](aws-networking.md) :
    -   [VPC](aws-vpcs.md)
    -   [Sous-réseaux](aws-subnetworks.md)
-   [Ressources de stockage d'objets](aws-object_storage.md)
-   Grappes Kubernetes

À cause de que CloudMC agit comme un portail vers les services AWS, vous pouvez constater que certaines opérations semblent se comporter différemment que lors de l'interaction directe avec AWS. Cependant, dans les coulisses, toutes les opérations s'exécutent exactement comme elles le feraient normalement. Les modifications apportées aux entités AWS dans CloudMC seront immédiatement reflétées dans les ressources réelles.

CloudMC permet aux administrateurs de gérer l'accès aux ressources et de générer des rapports d'utilisation détaillés. De plus, l'activité de l'utilisateur dans l'interface utilisateur Web ainsi que via l'API est capturée et mise à disposition via le journal d'activité. Pour assurer une bonne gouvernance, CloudMC crée automatiquement un utilisateur IAM sur le service AWS pour chaque membre d'un environnement. Toute opération effectuée par un utilisateur dans CloudMC est exécutée sur le service AWS à l'aide de cet utilisateur IAM, offrant une responsabilité complète.

