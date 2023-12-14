---
title: "AWS: Resumen de servicios"
slug: aws-resumen-de-servicios
---


## Resumen

CloudMC permite a los operadores de la nube acceder y administrar la infraestructura y los recursos que se han implementado en la plataforma de Amazon Web Services \(AWS\). Este artículo presentará los conceptos básicos de AWS y de trabajar con los recursos de AWS en CloudMC.

## Descripción detallada

La plataforma de AWS es una nube pública, donde los clientes pueden asignar recursos para construir una infraestructura para sus aplicaciones. CloudMC proporciona una interfaz unificada para acceder a AWS y otros servicios desde un único portal. A través de CloudMC, los usuarios pueden gestionar:

-   [Recursos de cómputo y almacenamiento](aws-compute.md):
    -   [Instancias](aws-instances.md)
    -   [Imágenes de máquina de Amazon \(AMIs\)](aws-amis.md)
    -   [Volúmenes](aws-volumes.md)
-   [Recursos de red](aws-networking.md):
    -   [VPCs](aws-vpcs.md)
    -   [Subredes](aws-subnetworks.md)
-   [Recursos de almacenamiento de objetos](aws-object_storage.md)
-   Clústeres de Kubernetes

Debido a que CloudMC actúa como un portal para los servicios de AWS, es posible que algunas operaciones parezcan comportarse de manera diferente que cuando interactúa directamente con AWS. Sin embargo, detrás de escena, todas las operaciones se ejecutan exactamente como lo harían normalmente. Los cambios realizados en las entidades de AWS en CloudMC se reflejarán inmediatamente en los recursos reales.

CloudMC brinda a los administradores la capacidad de administrar el acceso a los recursos y generar informes de uso detallados. Además, la actividad del usuario en la interfaz de usuario web, así como a través de la API, se captura y se pone a disposición a través del registro de actividad. Para garantizar una gobernanza adecuada, CloudMC crea automáticamente un usuario de IAM en el servicio de AWS para cada miembro de un entorno. Cualquier operación realizada por un usuario en CloudMC se ejecuta en el servicio de AWS utilizando ese usuario de IAM, lo que proporciona una responsabilidad completa.

