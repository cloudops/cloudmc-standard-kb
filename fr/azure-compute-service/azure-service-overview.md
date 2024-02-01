---
title: "Azure: Aperçu des services"
slug: azure-apercu-des-services
---


CloudMC permet aux opérateurs cloud d'accéder et de gérer l'infrastructure et les ressources qui ont été déployées sur la plateforme Microsoft Azure. Cet article présentera les concepts de base d'Azure et l'utilisation des ressources Azure dans CloudMC.

## Résumé

La plateforme Microsoft Azure est un cloud public, dans lequel les clients peuvent allouer des ressources pour créer une infrastructure pour leurs applications. CloudMC fournit une interface unifiée pour accéder à Azure et à d'autres services à partir d'un portail unique. Grâce à CloudMC, les utilisateurs peuvent gérer des :

-   [Instances](azure-instances.md)
-   [Disques](azure-disks.md)
-   Réseaux

Étant donné que CloudMC agit comme un portail vers les services Azure, vous constaterez peut-être que certaines opérations semblent se comporter différemment que lors d'une interaction directe avec Azure. Cependant, en coulisses, toutes les opérations s’exécutent exactement comme elles le feraient normalement. Les modifications apportées aux entités Azure dans CloudMC seront immédiatement reflétées dans les ressources réelles. Par exemple, Azure gère les ressources dans des groupes de ressources. CloudMC, en revanche, expose des ressources aux utilisateurs dans d'environnements, un concept déjà familier aux utilisateurs de CloudMC.

CloudMC offre aux utilisateurs la possibilité de gérer l'accès aux ressources et de générer des rapports d'utilisation détaillés. De plus, l'activité des utilisateurs dans l'interface utilisateur Web ainsi que via l'API est capturée et mise à disposition via le journal d'activité. Pour garantir une bonne gouvernance, CloudMC crée automatiquement un compte utilisateur sur le service Azure pour chaque membre d'un environnement. Toute opération effectuée par un utilisateur dans CloudMC est exécutée sur le service Azure avec le compte Azure de cet utilisateur, offrant ainsi une responsabilité totale.

