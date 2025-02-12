---
title: "GCP: Balanceo de carga"
slug: gcp-balanceo-de-carga
---


CloudOps es compatible con las funciones de balanceo de carga de Google Cloud Platform, mediante las cuales el tráfico puede dirigirse a un servicio de backend confiable con múltiples servidores para entregar una aplicación.

Se accede al balanceo de carga de GCP navegando al entorno de GCP deseado, haciendo clic en la pestaña **Redes** y haciendo clic en el elemento **Balanceo de carga**.

### Conceptos en el balanceo de cargas de GCP

- **Grupo de instancias**: define el grupo de instancias que proporcionan una aplicación o un microservicio.
- **Comprobación de estado**: define los criterios para determinar la disponibilidad de una instancia.
- **Servicio backend**: une un grupo de instancias, una comprobación de estado para las instancias de ese grupo y el protocolo que se usará para comunicarse con esas instancias.
- **Mapa de URL**: especifica a qué servicio de backend enviar tráfico, según la URL de la solicitud.
- **Proxy de destino**: escucha el tráfico en el protocolo especificado y reenvía ese tráfico al servicio de backend correcto, según el mapa de URL especificado.
- **Regla de reenvío de puertos**: une una dirección IP externa que sirve como punto final del balanceador de carga, un protocolo, un puerto y un proxy de destino.
- **Google Front End**: punto de interfaz entre GCP y la Internet pública.

Este modelo permite una flexibilidad significativa en las implementaciones, así como para la reutilización de componentes:
    - Si necesita admitir HTTP y HTTPS para sus clientes, dos proxies de destino (uno para HTTP y otro para HTTPS) pueden reenviar solicitudes al mismo servicio de backend.
    - Las conexiones SSL se pueden descifrar en el proxy de destino para descargar ese trabajo desde el backend.
    - Para los datos altamente sensibles que requieren encriptación de un extremo a otro, los proxies de destino pueden conectarse al backend a través de HTTPS.

El siguiente diagrama proporciona una visualización simplificada de las relaciones entre estos diferentes componentes:

![El balanceo de cargas en ](../../assets/gcp-load-balancing-en-1.png)

### Configurar el balanceo de cargas de GCP

Antes de configurar manualmente un nuevo balanceador de carga, ya debes tener lo siguiente:
    - Al menos una instancia en la región deseada, sirviendo tu aplicación o microservicio.
    - Un grupo de instancias en la misma región, que contiene las instancias.
    - Una verificación de estado adecuada para las instancias de destino.
    - Un certificado SSL cargado, si se requiere la compatibilidad con HTTPS. Ver [GCP: Certificados SSL](gcp-ssl-certs.md).

#### Configurar un balanceador de carga en un solo paso

Si ya se ha definido un servicio de backend, CloudOps permite la creación de un balanceador de carga en una sola página y creará los componentes necesarios en tu nombre utilizando valores predeterminados razonables.

1. Desde la página *Balanceadores de carga*, haz clic en el botón *Agregar balanceador de carga*.
1. Ingrese un nombre para el balanceador de carga o acepte el predeterminado.
1. Selecciona el servicio de backend para este balanceador de carga.
1. Selecciona cómo asignar una dirección IP externa. Consulte *Crear una regla de reenvío de puertos* en la sección **Configuración manual** a continuación para obtener más detalles sobre la asignación de una dirección IP externa.
1. Selecciona en qué protocolo escuchar las solicitudes entrantes.
    - Al seleccionar HTTPS, aparecerá una lista que contiene los certificados SSL cargados. Selecciona el certificado apropiado para este balanceador de carga.
1. Haz clic en *Aplicar*.
1. Aparecerá la página *Balanceadores de carga* y el nuevo balanceador de carga aparecerá en la lista.

El nuevo balanceador de carga ya está activo y listo para realizar pruebas con tráfico público. La dirección IP externa del balanceador de carga se enumera en la página *Reglas de reenvío de puertos* y también en la página *Balanceadores de carga*.

#### Configuración manual

1. Crea un servicio backend:
    - Haz clic en **Servicios backend** y haz clic en el botón *Agregar un servicio backend*.
    - Ingresa un nombre o acepta el predeterminado e ingresa una descripción si lo deseas.
    - Selecciona el protocolo que se utilizará para comunicarse con el grupo de instancias. Si usa HTTPS, consulta la siguiente sección sobre cómo habilitar SSL.
    - Selecciona la comprobación de estado deseada para el grupo de instancias.
    - Selecciona el grupo de instancias deseado.
    - Haz clic en *Aplicar*.
1. Crea un proxy de destino:
    - Haz clic en **Proxies de destino** y haz clic en el botón *Agregar un proxy de destino*
    - Ingresa un nombre o acepta el predeterminado e ingresa una descripción si lo deseas.
    - Selecciona el protocolo que utilizará el proxy de destino para escuchar las solicitudes entrantes de los clientes.
       - Para admitir conexiones HTTPS de clientes, selecciona HTTPS. Aparecerá una lista de los certificados SSL disponibles para CloudOps debajo de **Protocolo**, y deberás seleccionar el apropiado para este balanceador de carga.
    - Selecciona un mapa de URL. Si no se han creado mapas de URL, se creará un mapa de URL predeterminado al mismo tiempo que el proxy de destino.
    - Haga clic en *Aplicar*.
1. Crea una regla de reenvío de puertos.
    - Haz clic en **Reglas de reenvío de puertos** y haz clic en el botón *Agregar una regla de reenvío de puertos*.
    - Ingresa un nombre o acepta el predeterminado e ingresa una descripción si lo desea.
    - Selecciona cómo desea que se asigne una dirección IP externa para el balanceador de carga:
       - Para asignar una dirección IP únicamente para este balanceador de carga y hacer que se libere cuando se elimine esta regla de reenvío de puertos, deja *Reservar una nueva dirección IP estática* sin marcar y selecciona **Efímera** en la lista. La dirección IP asignada al balanceador de carga **no aparecerá** en la lista de **IP externas** para este entorno.
       - Para utilizar una dirección IP externa que ya ha sido asignada en este entorno, selecciónala de la lista.
       - Para reservar una nueva dirección IP externa que no se liberará cuando se elimine la regla de reenvío de puertos, selecciona *Reservar una nueva dirección IP estática*. La lista desaparecerá y se asignará una nueva dirección IP cuando se cree la regla de reenvío de puertos. La dirección IP también aparecerá en la lista de **IP externas** para este entorno.
   - Selecciona el protocolo a usar y en qué puerto escuchar las solicitudes entrantes.
      - Al seleccionar HTTPS, debe existir un proxy de destino configurado para SSL en el entorno.
   - En la lista **Proxy de destino**, selecciona el proxy de destino que se configuró en el paso anterior.
   - Haz clic en *Aplicar*.
1. Aparecerá la página *Reglas de reenvío de puertos* y se enumerará la nueva regla de reenvío de puertos.
1. El nuevo balanceador de carga aparecerá debajo del elemento **Balanceadores de carga**. Se le dará automáticamente el mismo nombre que el mapa de URL seleccionado.

El nuevo equilibrador de carga ya está activo y listo para realizar pruebas con tráfico público. La dirección IP externa de su balanceador de carga se enumera tanto en la página *Reglas de reenvío de puerto* como en la página *Balanceadores de carga*.

#### Habilitando SSL en el backend

Google Cloud Platform encripta automáticamente el tráfico entre el balanceador de carga y los servicios backend. Sin embargo, para mayor seguridad, GCP admite conexiones HTTPS entre el proxy de destino y el backend. Deben cumplirse los siguientes requisitos:

    - Se debe instalar un certificado SSL válido en cada instancia del grupo de instancias. El nombre común del certificado no tiene que coincidir con el nombre de host de la instancia.
    - Todas las instancias del grupo deben configurarse para usar HTTPS.
    - HTTPS debe configurarse como el protocolo en el servicio de backend deseado.

#### Eliminar un balanceador de cargas de GCP

La eliminación de un balanceador de cargas de GCP también eliminará automáticamente la regla de reenvío de puertos asociada, el proxy de destino y el mapa de URL, y también liberará las direcciones IP efímeras asignadas a la regla de reenvío de puertos.

1. Desde la página *Balanceadores de carga*, busca el balanceador de carga deseado y haz clic en el menú *Acción* en el extremo derecho de la entrada. Haz clic en *Eliminar*.
1. Aparecerá un cuadro de diálogo de confirmación. Haz clic en *Aplicar*.
1. El equilibrador de carga se eliminará del entorno de GCP.
