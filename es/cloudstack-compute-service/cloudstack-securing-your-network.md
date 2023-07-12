---
title: "CloudStack: Asegurar la red"
slug: cloudstack-asegurar-la-red
---

### Impedir el acceso a sus instancias

Es posible que debas poder acceder a tus instancias o permitir que usuarios externos accedan a las instancias. Esta página cubre lo que puedes hacer para permitir el acceso sin dejar de mantener la seguridad.

### VPN de acceso remoto

Una VPN de acceso remoto te permitirá acceder a sus instancias sin necesidad de conectarlas al mundo exterior. Si no necesitas acceso público a tus instancias, se sugiere esto. [Se puede encontrar cómo configurar una VPN de acceso remoto aquí.](../vpn/cca-using-remote-access.md)

### ACL de red

Puede configurar una lista de control de acceso (ACL) para tus redes para permitir el acceso externo a tus instancias, generalmente para mostrar un sitio web.

#### Crear la ACL

1. Selecciona **Servicios** en la barra lateral izquierda.
1. Selecciona el entorno informático deseado.
1. Selecciona la pestaña **Redes**.
1. En la VPC de destino, busca el elemento **ACL personalizadas** y haz clic en el menú de engranajes.
1. En la esquina superior derecha, selecciona *Agregar red ACL*.
1. Completa los campos de nombre y descripción para tu nueva ACL y presiona *Enviar*.
1. Aparecerá la página de detalles de la VPC y se seleccionará la pestaña **ACL de red**. La nueva ACL aparecerá en la lista de ACLS. Haz clic en la nueva ACL.
1. En la esquina superior izquierda, selecciona *Agregar regla ACL de red*.
1. Rellene el formulario *Agregar regla ACL de red*:
   1. **Número de regla:** El orden de prioridad de la regla. Las reglas se evalúan en orden numérico. Si se coloca una regla *denegar todo ingreso* en la posición 1, no se permitirá la entrada de tráfico. Si se coloca en último lugar, todas las demás reglas se evaluarán antes de aplicarla.
    1. **Descripción:** (Opcional) Una descripción de para qué sirve la regla ACL.
    1. **Acción:** Permitir o denegar el tráfico para esta regla.
    1. **Tipo de tráfico:** Si se trata de tráfico entrante o saliente.
    1. **CIDR:** El CIDR de red al que se aplica esta regla. Para el ingreso, esto se aplica a la fuente del tráfico. Para la salida, esto se aplica al tráfico de destino.
    1. **Protocolo:** El protocolo al que se aplica esta regla de red.
    1. **Puerto de inicio:** El puerto de inicio al que se aplica esta regla de ACL.
    1. **Puerto final:** El puerto final al que se aplica esta regla de ACL.
1. Continúe completando las reglas de la red hasta que la ACL esté completa.
1. Selecciona la pestaña **Redes** en la parte superior de la página.
1. Selecciona tu red en la VPC de destino.
1. Selecciona el menú *Acción* para tu red en el lado derecho y elige *Reemplazar ACL*.
1. Selecciona tu nueva ACL y haz clic en *Aplicar*.
1. Aparecerá la página de detalles de la red y la nueva ACL debe aparecer en **ACL**.
1. Selecciona la pestaña **Redes** en la parte superior de la página.
1. Desde la VPC de destino, busca el elemento **Acceso público** y haz clic en el menú de engranajes.
1. En la esquina superior derecha, selecciona *Adquirir dirección IP*.
1. Aparecerá un cuadro de diálogo solicitando confirmación. Haga clic en *Aplicar*. Aparecerá la pestaña **Direcciones IP públicas**.
1. Haz clic en la nueva dirección IP, que aparecerá en la lista titulada **Direcciones IP públicas**.
1. En el menú, selecciona *Reglas de reenvío de puertos*.
1. En la esquina superior derecha, selecciona *Agregar regla de reenvío de puertos*.
1. Rellena el formulario *Agregar regla de reenvío de puertos*:
    1. **IP pública:** La dirección IP pública que se asignó. Este campo no puede ser modificado.
    1. **Instancia:** Selecciona la instancia a la que deseas que esta IP pública se reenvíe.
    1. **IP privada:** La IP privada de la instancia a la que esta regla reenviará el tráfico.
    1. **Protocolo:** El protocolo del tráfico a reenviar.
    1. **Inicio de puerto público:** El puerto inferior de un rango de puertos públicos para esta regla de reenvío de puertos.
    1. **Extremo del puerto público:** (Opcional) El puerto superior de un rango de puertos públicos para esta regla de reenvío de puertos. Si solo estás abriendo un único puerto, puedes dejarlo vacío.
    1. **Inicio de puerto privado:** El puerto inferior de un rango de puertos privados para esta regla de reenvío de puertos.
    1. **Extremo del puerto privado:** (Opcional) El puerto superior de un rango de puertos privados para esta regla de reenvío de puertos. Si solo estás abriendo un único puerto, puedes dejarlo vacío.
1. Si es necesario, continúa agregando reglas de reenvío de puertos adicionales para esta IP pública.

Después de esto, se podrá acceder al tráfico a través de la IP pública asignada, a través de los puertos que haya reenviado a sus instancias, y solo se permitirá el tráfico que haya especificado en la ACL.

#### Lista de ACL de ejemplo

La siguiente lista permitirá el acceso a una instancia para HTTP y HTTPS, mientras bloquea el resto del tráfico:

| Número de regla | Descripción | CIDR | Acción | Protocolo | Tipo de tráfico | Puerto de inicio | Puerto final |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | HTTPS entrando | 0.0.0.0/0 | Permitir | TCP | Ingreso | 443 | 443 |
| 2 | HTTPS saliendo | 0.0.0.0/0 | Permitir | TCP | Egreso | 443 | 443 |
| 3 | HTTP entrando | 0.0.0.0/0 | Permitir | TCP | Ingreso | 80 | 80 |
| 4 | HTTP saliendo | 0.0.0.0/0 | Permitir | TCP | Egreso | 80 | 80 |
| 98 | Denegar todo entrando | 0.0.0.0/0 | Denegar | ALL | Ingreso | 1 | 65535 |
| 99 | Denegar todo saliendo | 0.0.0.0/0 | Denegar | ALL | Egreso | 1 | 65535 |
