---
title: "CloudStack: Configurar equilibrio de carga"
slug: cloudstack-configurar-equilibrio-de-carga
---


El equilibrio de carga proporciona una forma de distribuir las cargas de trabajo entre varios recursos informáticos. Esto generalmente aumenta el rendimiento y la disponibilidad a través de la redundancia. En el contexto de CloudMC, esto se logra asociando reglas de equilibrio de carga a la dirección IP pública de una VPC.

Solo una red que se creó con la oferta de **Load Balanced Tier** se puede usar para el equilibrio de carga, y una VPC solo puede tener una red configurada con esta oferta. No se pueden configurar reglas de equilibrio de carga en una dirección IP pública que ya se está utilizando para **NAT de origen**, **VPN** o **reenvío de puertos**.

<!-- Can add here an explanation of the algorithms and stickiness methods provided by CloudStack. -->

En el siguiente ejemplo, habilitaremos el equilibrio de carga para HTTP (puerto TCP 80) en las instancias *acme-web-01* y *acme-web-02* usando un algoritmo de planificación [round-robin](https://en.wikipedia.org/wiki/Round-robin_scheduling) sencillo.

1. Haz clic en **Servicios** en la barra lateral.
1. Selecciona el entorno informático deseado.
1. Selecciona la pestaña **Redes**.
1. Desde el elemento de la lista de la VPC de destino, haz clic en el botón **Acceso público**.
1. Haz clic en *Adquirir dirección IP*.
![Adquirir dirección IP](/assets/load-balancing-1-en.png)
1. Se te pedirá que confirmas la adquisición de una nueva dirección IP. Haz clic en *Aplicar*. La nueva dirección IP se asignará y aparecerá en **Direcciones IP públicas**.
1. Haz clic en la entrada de la nueva dirección IP:
![Dirección adquirida](/assets/load-balancing-2-en.png)
1. Haz clic en el elemento etiquetado como **Reglas del equilibrador de carga**. Aparecerá la pantalla *Reglas del equilibrador de carga*:
![Página de reglas del equilibrador de carga](/assets/load-balancing-3-en.png)
1. Haz clic en *Agregar regla de equilibrador de carga*. Aparecerá la página *Agregar regla de equilibrador de carga*.
1. Asigna un nombre a tu nueva regla, especifica el puerto público para equilibrar la carga y el puerto privado para reenviar el tráfico, y selecciona las instancias que manejarán el tráfico para el equilibrador de carga:
![Agregar regla de equilibrador de carga, información básica](/assets/load-balancing-4-en.png)
1. Selecciona el algoritmo de equilibrio deseado, el protocolo y el método de adherencia. En este ejemplo, no prescribimos ninguna política de adherencia y equilibramos la carga del tráfico TCP:
![Agregar regla de equilibrador de carga, políticas](/assets/load-balancing-5-en.png)
1. Haz clic en *Aplicar*. Aparecerá la página *Reglas del equilibrador de carga* y se enumerará la nueva regla del equilibrador de carga:
![Regla de equilibrador de carga creada](/assets/load-balancing-6-en.png)
1. Haz clic en el enlace *IP públicas* en la ruta de navegación y valida que la información mostrada refleje tu regla recién creada:
![Lista de direcciones IP públicas](/assets/load-balancing-7-en.png)
1. Finalmente, verifique que las reglas de equilibrio de carga funcionen como se esperaba ejecutando algo de tráfico y verifica si cada servidor está atendiendo una parte igual de las solicitudes. Una forma de lograr esto es obligar a cada servidor a devolver una respuesta ligeramente diferente (por ejemplo, el nombre de host del servidor) en su respuesta (o encabezados de respuesta).
