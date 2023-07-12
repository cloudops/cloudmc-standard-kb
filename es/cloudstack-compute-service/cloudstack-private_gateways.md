---
title: "CloudStack: Puertas de enlace privadas"
slug: cloudstack-puertas-de-enlace-privadas
---


Este artículo presenta el concepto de una puerta de enlace privada e incluye detalles sobre la administración de sus ACLs y rutas estáticas.

## Resumen detallado

Las instancias en VPCs separadas están aisladas entre sí. A menudo, configurar una [VPN de sitio a sitio](create-site-to-site-vpn-on-vpc.md) es una forma conveniente de establecer una conexión entre dos VPCs y permitir que sus instancias se comuniquen entre sí. Sin embargo, existen limitaciones con este enfoque. Una VPN cifra el tráfico de la red, lo que puede reducir el rendimiento. Además, las conexiones VPNes pueden terminar inesperadamente y deben restablecerse, lo que afecta la disponibilidad y el rendimiento.

Para abordar estos problemas, los proveedores de servicios pueden ofrecer una infraestructura de red privada dedicada para permitir que se interconecten dos VPCs. El tráfico de red entre las VPCs atraviesa una ruta interna en lugar de la red pública. Esto es útil cuando se necesita una conexión confiable y rápida, como para aplicaciones en tiempo real o para monitoreo y administración. En tal escenario, CloudMC puede aprovechar la ruta interna mediante la creación de una puerta de enlace privada entre las VPCs.

![Ilustración simplificada de dos VPC interconectadas por una puerta de enlace privada a través de una conexión de red interna](/assets/private-gateways-diagram-es.jpg)

El diagrama anterior ilustra una topología posible, donde dos VPCs están interconectadas y cada lado puede comunicarse con el otro. Un enrutador virtual en la VPC 1 se conecta a la puerta de enlace privada a través de una interfaz de red dedicada. Los cuadros rojos contienen la dirección IP que podría asignarse a cada interfaz. Las direcciones IP son solo para fines ilustrativos. Se configura una puerta de enlace privada en ambas VPCs y se identifica en cada lado por la dirección IP de la interfaz de terminación en el enrutador virtual. En esta ilustración, la puerta de enlace privada de la VPC 1 aparecería como 10.0.5.2 y la puerta de enlace privada de la VPC 2 sería 10.0.2.2. El diagrama no incluye detalles de la red física subyacente y también omite las redes dentro de cada VPC.

Debido a que la configuración de una puerta de enlace privada requiere un conocimiento específico de cómo se configura la red física, solo una cuenta de CloudMC con privilegios de nivel de revendedor puede configurar esta función. Sin embargo, los usuarios y administradores tienen permiso para ver las puertas de enlace privadas en sus entornos y pueden configurar el acceso y el enrutamiento. La configuración de la puerta de enlace privada en cada lado tiene su propio conjunto de rutas estáticas. Estos definen, en función de la IP de destino, el tráfico que se enrutará a través de la puerta de enlace privada. El control de acceso se establece a través de las ACLs de red que has definido; consulta [Asegurar la red](securing-your-network.md) para obtener más información.

Las puertas de enlace privadas se pueden ver navegando a tu entorno deseado, luego **Redes** \> **Puertas de enlace privadas**.

![Una captura de pantalla de la página de descripción general de VPC, con puntos numerados que indican las características de la puerta de enlace privada](/assets/private-gateways-vpc-en.png)

1. **Lista de puertas de enlace privadas**

     En esta sección, aparece una lista de todas las puertas de enlace privadas en esta VPC, junto con su estado. Cada puerta de enlace se identifica por la dirección IP de la interfaz de terminación \(el otro extremo de la conexión\).

2. **Ícono de engranaje**

     Haz clic en el ícono de ajustes para navegar a la página de **Puertas de enlace privadas** para esta VPC.


## Pasarelas privadas y ACLs

![Captura de pantalla de los detalles de las puertas de enlace privadas paginadas, con puntos numerados en las características principales](/assets/private-gateways-list-en.png)

1. **Lista de puertas de enlace privadas**

     En el área principal del espacio de trabajo, aparece una lista de todas las puertas de enlace privadas en la VPC seleccionada.

2. **Cuadro de búsqueda**

     Escribe en el cuadro de búsqueda para filtrar la lista de puertas de enlace privadas. El sistema buscará en todos los campos de la puerta de enlace privada, incluido el nombre, la dirección IP de la puerta de enlace, los nombres de ACL y las cadenas de UUID internas, y devolverá cualquier puerta de enlace privada que coincida con la cadena en el cuadro de búsqueda.

3. **Fila de puerta de enlace privada**

     Cada fila incluye la dirección IP y la máscara de subred de la interfaz del enrutador virtual conectada a la puerta de enlace privada, la dirección IP de la puerta de enlace privada, su estado y la ACL aplicada actualmente.

     Haz clic en una puerta de enlace privada para ver sus detalles, incluidas las rutas estáticas.

4. **Menú de acciones escondidas**

     Cada entrada en la lista de puertas de enlace privadas tiene un menú de Acciones ocultas. Haz clic en el menú Acciones escondidas para acceder al comando **Reemplazar ACL**.

     Para aplicar una ACL diferente a una puerta de enlace privada, haz clic en el comando **Reemplazar ACL**. Aparecerá un cuadro de diálogo, donde puedes seleccionar uno para aplicar de una lista de ACL de red que se han definido para su VPC.


## Rutas estáticas

![Una captura de pantalla de la página Rutas estáticas, con puntos numerados en las características principales](/assets/private-gateways-static-routes-en.png)

1. **Lista de rutas estáticas**

     En el área principal del espacio de trabajo, aparece una lista de todas las rutas estáticas que se han definido para la puerta de enlace privada seleccionada.

2. **Cuadro de búsqueda**

     Escribe en el cuadro de búsqueda para filtrar la lista de rutas estáticas. El sistema buscará a través del campo CIDR y devolverá cualquier ruta estática que coincida con la cadena en el cuadro de búsqueda.

3. **Añadir ruta estática**

     Al hacer clic en este botón, se abrirá un cuadro de diálogo donde puede agregar una nueva ruta estática a la puerta de enlace privada. Ingresa el CIDR de la red o el host de destino, y el tráfico a ese destino se enrutará a través de la puerta de enlace privada.

4. **Fila de ruta estática**

     Cada fila incluye el CIDR de la ruta de destino, su estado y un menú de Acciones escondidas con el comando **Eliminar** para eliminar esta ruta estática.


