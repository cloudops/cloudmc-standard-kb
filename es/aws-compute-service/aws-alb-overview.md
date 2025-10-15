---
title: "AWS: Equilibradores de carga de aplicaciones"
slug: aws-alb-resumen
---


Este artículo proporciona información sobre los equilibradores de carga de aplicaciones en AWS, sus propiedades y los componentes de los que dependen, así como el flujo de trabajo para crearlos.

## Resumen

Dentro de la oferta de Elastic Load Balancing, AWS admite equilibradores de carga diseñados específicamente para actuar como front-end para una aplicación web. El equilibrador de carga de aplicaciones, o ALB (por su ortografía en inglés), es un dispositivo virtual que escucha las solicitudes entrantes de los clientes en un puerto y protocolo específicos. Cuando el **oyente** recibe una solicitud, el equilibrador de carga la reenvía a un servidor en el back-end. El servidor es una instancia en una VPC a la que se le ha concedido acceso al equilibrador de carga, y normalmente este se configura con más de un servidor en el back-end. La instancia del back-end procesa la solicitud y devuelve una respuesta al equilibrador de carga. El equilibrador de carga entrega la respuesta al cliente.

![Diagrama de la función de equilibrador de carga de aplicaciones de AWS](/assets/aws-alb-overview.png)

Los casos de uso para los equilibradores de carga de aplicaciones incluyen:

- Mejora del rendimiento y la disponibilidad de las aplicaciones
- Escalado dinámico del back-end
- Descarga del procesamiento SSL de los servidores de aplicaciones

Dado que el equilibrador de carga de aplicaciones cuenta con un conjunto de instancias en el back-end, denominado **grupo de destino**, él puede seleccionar una instancia específica para cada solicitud, basándose en un algoritmo, para optimizar el uso de los recursos. Además, puede ejecutar periódicamente una **comprobación de estado** para verificar que una instancia determinada responda a las solicitudes de forma oportuna. El equilibrador de carga puede tomar las medidas oportunas cuando las instancias tardan en responder o no responden en absoluto. De igual forma, si se añaden instancias al grupo de destino, el equilibrador de carga puede comenzar a reenviar solicitudes inmediatamente a las nuevas instancias.

El equilibrador de carga de aplicaciones actúa como punto de terminación de las conexiones de los clientes. Por lo tanto, si se requiere compatibilidad con conexiones SSL, se debe configurar un certificado SSL para el equilibrador de carga. La solicitud descifrada se puede reenviar mediante una conexión HTTP a las instancias del back-end. Sin embargo, si se necesita cifrado de extremo a extremo, las instancias del back-end también deberán configurarse con certificados SSL.

## Flujo de trabajo para la creación de los ALB

![Diagrama que muestra los principales pasos necesarios para implementar un equilibrador de carga de aplicaciones](/assets/aws-alb-workflow.png)

1.  **Implementar infraestructura de red y cómputo**

    El entorno de destino debe tener una VPC implementada, y la VPC debe tener al menos dos subredes en dos zonas de disponibilidad independientes. Las instancias que recibirán el tráfico del equilibrador de carga de aplicaciones deben estar implementadas en estas subredes.

2.  **Añadir grupo de destino**

    El grupo de destino es el conjunto de instancias que deseas que atiendan las solicitudes recibidas por el equilibrador de carga. Aquí también se especifica el protocolo de comunicación entre el equilibrador de carga y las instancias, así como las comprobaciones de estado necesarias para mantener la disponibilidad de la aplicación.

3.  **Adquirir certificado SSL**

    Este paso es opcional, pero muy recomendable si se trata de un equilibrador de carga con conexión a internet. Se puede solicitar la generación de un certificado SSL o importar el tuyo propio.

4.  **Añadir equilibrador de carga**

    Una vez completados los pasos anteriores, ya estás listo para configurar las propiedades del equilibrador de carga de la aplicación, definir los oyentes que aceptarán las solicitudes entrantes y seleccionar las instancias a las que se reenviarán las solicitudes.


