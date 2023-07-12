---
title:  "CloudStack: Configurar el reenvío de puertos"
slug:  cloudstack-configurar-reenvio-de-puertos
---

El reenvío de puertos proporciona conectividad entrante desde Internet a un puerto o protocolo de instancia específico. Se configura a través de la dirección IP pública de una VPC dedicada al reenvío de puertos.

Nota: no se pueden configurar reglas de reenvío de puertos en una dirección IP pública que ya se esté utilizando para **NAT de origen**, **VPN** o **Equilibrio de carga**.

En el siguiente ejemplo, habilitaremos el reenvío de puertos para HTTP (puerto TCP 80) a la instancia *acme-web-01* a la IP privada en el puerto 8080. Esta instancia ejecuta un servidor web que escucha en el puerto 8080.

1. Haz clic en **Servicios** en la barra lateral.
1. Selecciona el entorno informático deseado.
1. Selecciona la pestaña **Redes**.
1. Desde el elemento de la lista de la VPC de destino, haz clic en el botón **Acceso público**.
1. Haz clic en *Adquirir dirección IP*.
![Adquirir dirección IP](/assets/config-port-fwd-1-en.png)
1. Se te pedirá que confirmas la adquisición de una nueva dirección IP. Haz clic en *Aplicar*. La nueva dirección IP se asignará y aparecerá en **IP públicas**.
1. Haz clic en la entrada de la nueva dirección IP:
![Dirección adquirida](/assets/config-port-fwd-2-en.png)
1. Aparecerá la pantalla **Reglas de reenvío de puertos**. Haz clic en *Agregar regla de reenvío de puertos*:
![Reglas de reenvío de puertos](/assets/config-port-fwd-3-en.png)
1. Selecciona la instancia de destino *acme-web-01* y tu dirección IP privada correspondiente de la lista emergente y selecciona **TCP** como protocolo.
1. Ingresa **80** en el campo **Inicio de puerto público** e ingresa **8080** en el campo **Inicio de puerto privado**. Debido a que estamos ingresando un solo puerto y no un rango de puertos, podemos dejar los campos de fin de puerto en blanco.
![Agregar regla de reenvío de puertos](/assets/config-port-fwd-4-en.png)
1. Haz clic en *Aplicar*. Aparecerá la pantalla **Reglas de reenvío de puertos** y se enumerará la nueva regla:
![Regla de reenvío de puertos agregada](/assets/config-port-fwd-5-en.png)
1. Valida que la regla de reenvío de puertos esté funcionando conectándose a la instancia a través de la IP pública en el puerto 80:
![Validar con HTTP](/assets/config-port-fwd-6.png)
