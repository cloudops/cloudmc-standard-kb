---
title: "Usar entornos para organizar usuarios y cargas de trabajo"
slug: entornos-para-organizar-cargas-de-trabajo-y-usuarios
---


### Resumen de entornos

La plataforma proporciona un mecanismo poderoso, el de **entornos**, para segregar cargas de trabajo y recursos, y para controlar quién tiene acceso a ellos. Los ejemplos de casos de uso de este concepto incluyen la creación de entornos distintos para aislar las cargas de trabajo de producción de los sistemas de desarrollo, o el establecimiento de [aislamiento de procesos](https://es.wikipedia.org/wiki/Aislamiento_de_procesos) específicos del proyecto.

Un entorno pertenece a una organización, está asociado con un servicio específico (por ejemplo, Computación o Almacenamiento de objetos) y está compuesto por un conjunto de miembros que tienen visibilidad en un grupo de recursos compartidos, como instancias, almacenamiento, etc.  Los miembros son usuarios a los que se les ha concedido acceso a un entorno determinado. Un usuario de una organización no es necesariamente miembro de los entornos de esa organización.

Aunque el sistema calcula el uso del servicio a nivel de la organización para fines de facturación, los recursos consumidos por cada entorno también se rastrean por separado, lo que permite a las empresas generar informes internos de devolución de cargo por entorno si así lo desean.

Navega hasta el servicio deseado en la barra lateral para llegar a la página *Entornos*, donde se enumeran todos los entornos del servicio seleccionado. Además, cuando se trabaja dentro de un entorno, el servicio y el entorno actuales se muestran en la parte superior izquierda de la página. Al hacer clic en este botón, se mostrará una opción para volver a la página *Entornos* o para cambiar a otro entorno.

### Roles de entorno

La membresía del entorno se combina con un **rol de entorno**, que controla lo que un usuario puede hacer con los recursos contenidos en este entorno. Al contrario de los roles de sistema, los roles de entorno son fijos y no se pueden personalizar de forma granular. Consulta [El control de acceso basados en roles](../administration/rbac.md) para obtener más información sobre los roles de entorno.

### Crear un ambiente

Cualquier usuario con el rol **Usuario**, o cualquier otro rol que tenga el permiso *Entornos: Crear*, puede agregar entornos adicionales y decidir quién debe tener acceso a él.

1. Haz clic en *Agregar entorno*. Aparecerá la página *Agregar entorno*.
1. Introduce un nombre y una descripción opcional para el entorno.
1. Si deseas permitir que los usuarios de otras organizaciones se agreguen como miembros, selecciona **Autorizar a miembros externos**.
1. Para algunos servicios, estará disponible un triángulo de información con opciones avanzadas. Consulte el artículo *Gestionar las instancias* de su servicio en particular para obtener más detalles. <!-- This is inaccurate, needs to be addressed. -->
1. Haz clic en *Siguiente*. El entorno se aprovisionará.
1. La página *Administrar miembros* aparecerá en un momento. Aquí puedes:
    - Seleccionar uno o más usuarios individuales de la lista
    - Buscar usuarios específicos
    - Agregar **todos los usuarios** en la organización (**membresía automática**)
    - Agregar ningunos usuarios al entorno (haz clic en *Omitir* para pasar a la página siguiente)
1. Para cualquier usuario que haya agregado, selecciona un rol de entorno. Si has activado la membresía automática, selecciona un rol de entorno predeterminado.
1. Haz clic en *Aplicar* para comprometer a los miembros seleccionados. Se agregarán los usuarios.
1. Para algunos servicios, la página *Inicializar entorno* aparecerá a continuación. Los elementos de esta página son específicos del servicio en el que se está creando el entorno. Es seguro hacer clic en *Omitir* y configurar el entorno más tarde.

<!-- This needs to be moved to a CloudStack article: Here, you may:
   - Configure an isolated network with no access to any other subnet, nor to the public Internet
   - Configure one, two, or three VPCs.  See [What is a VPC](../cloudstack-compute-service/what-is-a-vpc.md) for more information on VPCs
   - Configure no network (click *Skip* to finish creating the environment)
1. If you've chosen to create one or more networks, enter the requested parameters for the networks to be created.
1. Click *Initialize*.
1. The networks will be created and you will be returned to the *Environments* page. -->

### Gestionar y eliminar un entorno

Desde la página *Entornos*, puedes hacer clic en el icono *Editar* a la derecha de un entorno para cambiar el nombre, la descripción, o la opción para permitir miembros externos.

Al hacer clic en el menú *Acción* de un entorno, se podrá gestionar a los miembros que tienen acceso al entorno, o eliminar el entorno. Además, también puedes copiar el UUID del entorno del orquestador de la nube subyacente y forzar la actualización de la información almacenada en caché en este entorno desde el orquestador de la nube.

**Nota:** Eliminar un entorno destruye permanentemente TODAS las instancias, discos, redes y cualquier otro recurso en el entorno eliminado. Esta es una operación destructiva y **no se puede deshacer**.
