---
title: "Azure: Resumen de servicios"
slug: azure-resumen-de-servicios
---


CloudOps permite a los operadores de la nube acceder y administrar la infraestructura y los recursos que se han implementado en la plataforma Microsoft Azure. Este artículo presentará conceptos básicos de Azure y cómo trabajar con recursos de Azure en CloudOps.

## Descripción detallada

La plataforma Microsoft Azure es una nube pública, donde los clientes pueden asignar recursos para construir una infraestructura para sus aplicaciones. CloudOps proporciona una interfaz unificada para acceder a Azure y otros servicios desde un único portal. A través de CloudOps, los usuarios pueden gestionar:

-   [Instancias](azure-instances.md)
-   [Discos](azure-disks.md)
-   Redes

Debido a que CloudOps actúa como un portal para los servicios de Azure, es posible que algunas operaciones parezcan comportarse de manera diferente que cuando interactúan directamente con Azure. Sin embargo, entre bastidores, todas las operaciones se ejecutan exactamente como lo harían normalmente. Los cambios realizados en las entidades de Azure en CloudOps se reflejarán inmediatamente en los recursos reales. Por ejemplo, Azure administra recursos dentro de grupos de recursos. CloudOps, por otro lado, expone recursos a los usuarios dentro de entornos, que es un concepto que ya les resulta familiar a los usuarios de CloudOps.

CloudOps brinda a los usuarios la capacidad de administrar el acceso a los recursos y generar informes de uso detallados. Además, la actividad del usuario en la interfaz de usuario web, así como a través de la API, se captura y se pone a disposición a través del registro de actividad. Para garantizar una gobernanza adecuada, CloudOps crea automáticamente una cuenta de usuario en el servicio de Azure para cada miembro de un entorno. Cualquier operación realizada por un usuario en CloudOps se ejecuta en el servicio de Azure con la cuenta de Azure de ese usuario, lo que proporciona una responsabilidad completa.

