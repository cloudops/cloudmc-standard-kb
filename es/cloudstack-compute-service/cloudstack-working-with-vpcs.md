---
title: "CloudStack: Gestion de VPC"
slug: cloudstack-gestion-de-vpc
---


<!-- - [Create a new VPC](#create-a-new-vpc)
- [Create a new network tier](#create-a-new-network-tier)
- [Site-to-Site VPN](#site-to-site-vpn)
    + [Considerations:](#considerations-) -->

Para crear, modificar o eliminar una VPC, una cuenta con el rol *Usuario* debe ser miembro del entorno que contiene la VPC y también tener asignado el rol de entorno *Editor* o *Propietario*. Una cuenta con el rol *Administrador* o superior puede crear, modificar o eliminar VPC en un entorno.

Para obtener más información sobre las VPC, consulte [Qué es una VPC](../cloudstack-compute-service/what-is-a-vpc.md).

### Crear una nueva VPC

1. Selecciona **Servicios** en la barra lateral izquierda.
1. Selecciona el entorno informático deseado.
1. Selecciona la pestaña **Redes**.
1. Haz clic en **Configurar las redes** y, en el menú desplegable, seleccione **Agregar VPC**.
![La pestaña de redes](/assets/working-with-vpcs-1-en.png)
1. Completz el formulario **Agregar VPC**:
    - **Nombre:** Nombre de la VPC (ej.: *acme-prod-vpc01*).
    - **Descripción:** (Opcional) Descripción de la VPC (ej.: "Sitio A de la red de producción").
    - **CIDR:** El rango de IP que se usará para la VPC. El rango debe ser una red /22.
    - **Dominio de red:** (Opcional) Nombre de dominio para resolución DNS interna (por ejemplo: *internal.acme.com*). CloudMC agregará este nombre de dominio al archivo */etc/hosts* para nuevas instancias.
    - **Oferta de VPC:** Elige el nivel de servicio de esta VPC.
    ![Página de agregar una VPC](/assets/working-with-vpcs-2-en.png)
1. Haz clic en **Aplicar**.
1. Aparecerá la pestaña **Redes** y tu nueva VPC aparecerá en el estado de **Inicio**. Cuando se haya creado, la VPC aparecerá en el estado **habilitado**.
![Pestaña d redes con la VPC](/assets/working-with-vpcs-3-en.png)

### Crear un nuevo nivel de red

1. Desde la VPC de destino, busca el elemento *Redes* y haz clic en el menú de engranajes.
1. En la esquina superior derecha, haz clic en **Agregar red**.
![Página de detalles de la VPC](/assets/working-with-vpcs-4-en.png)
1. Completa el formulario **Agregar red**:
    - **Nombre:** Nombre del nivel (ej.: *acme-net-web1*)
    - **Descripción:** (Opcional) Descripción del nivel (por ejemplo: "Servidores web de producción")
    - **Oferta de red:** Elige el nivel de servicio de este nivel
       - **Nivel estándar:** Una red regular compatible con NAT y reenvío de puertos. Adecuado para aplicaciones internas como un servidor de base de datos.
       - **Nivel de equilibrio de carga:** (predeterminado) Incluye las funciones del nivel estándar y también ofrece la capacidad de equilibrar la carga del tráfico en varias instancias dentro de ese nivel, a través de reglas que se aplican en una dirección IP pública. **Nota: Solo un único nivel dentro de una VPC puede tener esta oferta.**
    - **Puerta de enlace:** La dirección IP de la puerta de enlace predeterminada para crear el nivel de red.
    - **Máscara de red:** La máscara de subred del nivel de red que se creará.
    - **ACL:** lista de control de acceso (ACL) para la comunicación entre niveles dentro de la misma VPC. Consulta [Asegurar la red](securing-your-network.md)) para obtener más información sobre las ACL.
       - **default_allow:** (Predeterminado) Permitir todo tipo de tráfico desde/hacia otros niveles en la VPC.
       - **default_deny:** Denegar todo tipo de tráfico desde/hacia otros niveles en la VPC.
    ![Agregar página de red](/assets/working-with-vpcs-5-en.png)
1. Haz clic en **Aplicar**.
1. Aparecerá la página *VPC*. La nueva red aparecerá en la lista de redes en estado **asignado** y ahora está lista para usarse.

### VPN de sitio a sitio

Las VPN de sitio a sitio ofrecen la capacidad de interconectar varias VPC, una oficina remota a una VPC u otro proveedor de nube a una VPC. Puedes encontrar un ejemplo de VPN de sitio a sitio en el artículo de procedimientos [Crear una VPN de sitio a sitio en una VPC](../cloudstack-compute-service/create-site-to-site-vpn-on-vpc.md).

1. En la VPC de destino, busca el elemento **VPN de sitio a sitio** y haz clic en el menú de ajustes.
   ![La página de VPN de sitio a sitio](/assets/working-with-vpcs-6-en.png)
1. En la esquina superior derecha, selecciona **Agregar VPN de sitio a sitio**.
1. Complete el formulario *Agregar VPN de sitio a sitio*:
    - **Nombre de esta conexión VPN:** Nombre de la conexión VPN, probablemente para qué es esta conexión.
    - **IP pública remota:** La IP a la que se conectará la VPN. Para otra VPC, este es tu NAT de origen. Esto se puede encontrar en el elemento VPC en la pestaña **Redes**.
    - **Lista de CIDR remotos:** Una lista separada por comas de CIDR a los que se puede acceder a través de esta conexión. Si se conecta a otra VPC, este es el CIDR de la VPC.
    - **Clave precompartida de IPSec:** Una clave utilizada por ambos extremos de la VPN para conectarse. No hay un mínimo de complejidad para esto, pero se sugiere proporcionar una clave más segura.
    - **Algoritmo de cifrado IKE:** El algoritmo de cifrado para la conexión VPN para las negociaciones de la fase 1. La autenticación utiliza la clave precompartida.
    - **Algoritmo hash IKE:** El algoritmo hash para la conexión VPN.
    - **Grupo IKE Diffie-Hellman:** El grupo Diffie-Hellman para la conexión VPN.
    - **Vida útil de IKE:** La vida útil de la VPN. El valor predeterminado es un día.
    - **Algoritmo de cifrado ESP:** El algoritmo de cifrado para el protocolo de seguridad de encapsulación.
    - **Algoritmo hash ESP:** El algoritmo hash para el protocolo de seguridad de encapsulación para las negociaciones de la fase 2.
    - **Secreto directo perfecto ESP:** El grupo Diffie-Hellman para el protocolo de seguridad de encapsulación.
    - **Vida útil del ESP:** La vida útil del protocolo de seguridad de encapsulación. El valor predeterminado es una hora.
    - **Detección de pares muertos:** Verifica si el otro extremo de la VPN está vivo o no. Si el otro extremo no responde, la VPN intentará volver a conectarse.
    - **Forzar encapsulación para NAT transversal:** Forzar NAT transversal para la conexión VPN (encapsulación UDP).
    - **Conexión pasiva:** Marque esta casilla si aún no se ha configurado el extremo remoto. Solo debe existir un extremo pasivo por VPN de sitio a sitio.
1. Haz clic en **Aplicar**.
1. Aparecerá la pestaña **VPN de sitio a sitio** y la nueva VPN aparecerá en el estado **Desconectado**.
   ![VPN creada pero aún no conectada](/assets/working-with-vpcs-7-en.png)
1. Si es necesario, configure el otro extremo de la VPN con la misma clave precompartida que esta.
1. Una vez que se haya configurado el otro extremo del túnel VPN, el estado cambiará a **Conectado**.

### VPN de acceso remoto

Una VPN de acceso remoto permite acceder a la red a los recursos dentro de una VPC. Para obtener más información, consulte [Conectarse a una VPC mediante VPN de acceso remoto (IKEv2)](../vpn/cca-using-remote-access.md).
