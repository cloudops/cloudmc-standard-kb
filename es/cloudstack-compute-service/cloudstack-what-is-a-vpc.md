---
title: "CloudStack: ¿Qué es una VPC?"
slug: cloudstack-que-es-una-vpc
---


Una nube privada virtual (VPC) es una sección aislada lógicamente en un entorno, donde puedes crear una arquitectura de aplicación de varios niveles.

Por lo general, en la mayoría de las nubes públicas del mercado, uno implementa sus instancias en lo que nos gusta llamar una *red básica*. En otras palabras, su instancia y las instancias de otros inquilinos están todas conectadas en la misma red enorme.

![Red básica](/assets/what-is-a-vpc-1.png)

El control de acceso a la red se realiza mediante grupos de seguridad o ACLes en el nivel del hipervisor. Reconocemos que este modelo también es mucho más sencillo de implementar para los proveedores de servicios y los clientes, pero la seguridad y el aislamiento de los inquilinos son un gran problema.

En el modelo de VPC, puede haber un poco más de complejidad relacionada con la administración. Sin embargo, obtienes mucho más control y aislamiento. Por esta razón, seleccionamos este modelo sobre los métodos más tradicionales.

![Modelo de red de VPC](/assets/what-is-a-vpc-2.png)

Una VPC consta de los siguientes componentes de red:

- **VPC:** Una VPC actúa como un contenedor para múltiples redes aisladas que pueden comunicarse entre sí a través de un enrutador virtual.
- **Niveles de red:** Cada nivel actúa como una red aislada con sus propias VLAN y lista de CIDR, donde puedes colocar grupos de recursos, como VMs. Los niveles se segmentan mediante VLANs. La NIC de cada nivel actúa como su pasarela.
- **Enrutador virtual:** Un enrutador virtual se crea y se inicia automáticamente cuando creas una VPC. El enrutador virtual conecta los niveles y dirige el tráfico entre la pasarela pública, las pasarelas VPN y las instancias NAT. Para cada nivel, existe una NIC e IP correspondientes en el enrutador virtual. El enrutador virtual proporciona servicios DNS y DHCP a través de su IP.
- **Pasarela pública:** El tráfico hacia y desde Internet se enruta a la VPC a través de una pasarela pública. En una VPC, la pasarela pública no está expuesta al usuario final; por lo tanto, las rutas estáticas no son compatibles con la pasarela pública.
- **Pasarela privada:** Todo el tráfico hacia y desde una red privada se enruta a la VPC a través de la pasarela privada.
- **Pasarela VPN:** El lado VPC de una conexión VPN.
- **Conexión VPN de sitio a sitio:** Una conexión VPN basada en hardware entre tu VPC y el centro de datos, la red doméstica o la instalación de coubicación.
- **Pasarela del cliente:** El lado del cliente de una conexión VPN.
- **Instancia NAT:** Una instancia que proporciona traducción de dirección de puerto para que las instancias accedan a Internet a través de la pasarela pública.
- **ACL de red:** Reglas ordenadas que determinan si el tráfico está permitido dentro o fuera de cualquier nivel asociado con la ACL de red.

### Arquitectura de red en una VPC
En una VPC, las siguientes arquitecturas de red son las opciones básicas:

- VPC con una pasarela pública únicamente
- VPC con pasarelas públicas y privadas
- VPC con pasarelas públicas y privadas y acceso VPN de sitio a sitio
- VPC con una pasarela privada únicamente y acceso a VPN de sitio a sitio

### Opciones de conectividad para una VPC
Puedes conectar tu VPC a:

- Internet a través de la pasarela pública
- Un centro de datos corporativo mediante el uso de una conexión VPN de sitio a sitio a través de una pasarela VPN
- Tanto Internet como su centro de datos corporativo, utilizando tanto la pasarela pública como una puerta de enlace VPN

### Consideraciones sobre la red de VPC
Tengas en cuenta lo siguiente cuando creas una VPC:

- La cantidad máxima de niveles que puedes crear dentro de una VPC es 4.
- Cada nivel debe tener un CIDR único en la VPC. La interfaz web hace cumplir este requisito.
- Un nivel pertenece a una sola VPC.
- Cuando se crea una VPC, de forma predeterminada, se le asigna una IP de NAT de origen. La IP de NAT de origen se libera solo cuando se elimina la VPC.
- Una IP pública se puede utilizar para un solo propósito a la vez. Si la IP es una NAT de origen, no se puede utilizar para NAT estática o reenvío de puertos.
- **NAT estática** es un mapeo uno a uno entre una IP pública y una instancia en una VPC. Todo el tráfico enviado a la IP pública se enviará a la instancia designada y todo el tráfico de la instancia se enviará desde la IP pública. Usa NAT estática cuando necesitas que el tráfico de entrada siempre vaya a la misma instancia, o cuando necesitas que todo el tráfico de una instancia salga de la misma IP pública.
- **Reenvío de puertos** es una asignación de un puerto en una dirección IP pública a un puerto en una IP privada en una VPC. Se pueden reenviar diferentes puertos en la IP pública a puertos en instancias separadas, siempre que las instancias estén en la misma VPC. Todo el tráfico de las instancias utilizará la dirección IP de NAT de origen de la VPC para el tráfico de salida. Utiliza el reenvío de puertos cuando todo lo que necesitas es que el tráfico de entrada en puertos específicos se reenvíe a una instancia. Esto permite un uso eficiente del espacio de direcciones IP.
- Las instancias solo pueden tener una dirección IP privada, por lo tanto, estar conectadas solo a un nivel a la vez.
- El servicio público de equilibrio de carga solo puede ser compatible con un nivel dentro de la VPC.
- Si se asigna una dirección IP a un nivel:
    - Esa IP no puede ser utilizada por más de un nivel a la vez en la VPC. Por ejemplo, si tienes niveles A y B, y una IP pública, puedes crear una regla de reenvío de puertos utilizando la IP para A o B, pero no para ambos.
    - Esa IP no se puede usar para NAT estática, balanceo de carga o reglas de reenvío de puertos para otra red invitada dentro de la VPC.
