---
title: "CloudStack: Activar NAT estático"
slug: cloudstack-activar-nat-estatico
---


Este artículo te guiará a través de los pasos para configurar NAT estática para una instancia en tu entorno. Activar NAT estática para una instancia creará una asignación uno a uno desde una dirección IP pública a esa instancia. Debes estar familiarizado con [conceptos de redes](../cloudstack-compute-service/what-is-a-vpc.md) como la traducción de direcciones de red (NAT), la NAT estática, el reenvío de puertos y las listas de control de acceso (ACL).

## Prerrequisitos

- Deberás tener un entorno configurado con una VPC.
- La VPC debe tener una red *estándar* o *de carga equilibrada* en esa VPC.
- La máquina virtual de destino debe tener una NIC con una IP privada en esa red.
- La red de destino debe tener las [ACL de red](securing-your-network.md) adecuadas configuradas para permitir el tráfico deseado y denegar el resto del tráfico.

## Pasos

1. Navega hasta tu entorno de destino y haa clic en la pestaña *Redes*.
1. Ve a *Acceso público* haciendo clic en el icono de engranaje. Aparecerá la pantalla *IP públicas*.
1. Haz clic en *Adquiera la dirección IP*. Cuando aparezca el cuadro de diálogo de confirmación, haga clic en *Aplicar*.
1. Después de que la dirección IP recién asignada aparezca en la lista de IP públicas, ve al menú de tres puntos a la derecha de la entrada y selecciona *Habilitar NAT estática*.
1. En la pantalla *Habilitar NAT estática*, selecciona la instancia de destino.
1. Después de seleccionar la instancia de destino, el menú emergente *IP privada* mostrará las IP privadas que se han asignado a la instancia seleccionada.
1. Selecciona de la lista la IP privada a la que se debe enviar el tráfico.
1. Haz clic en *Aplicar*.

## Resultado

- El NAT estático creará una asignación uno a uno desde la dirección IP pública a la máquina virtual de destino. El tráfico enviado a la dirección IP pública desde una fuente permitida a un puerto permitido llegará a la VM de destino en la IP privada seleccionada. Del mismo modo, todo el tráfico enviado desde la instancia a través de esa IP privada se enviará desde la IP pública asignada.
- La pantalla *Direcciones IP públicas* mostrará la dirección IP pública asignada con la etiqueta **NAT estática**, junto con los nombres de la VPC asociada, la red y la instancia de destino.
- La conectividad se puede probar con el método de tu elección, como con un `tcpdump` en la máquina virtual de destino, o conectándose a un servicio que se ejecuta en la máquina virtual, como SSH, RDP o un servicio web.

## Ejemplo

### Configuración

En este ejemplo, configuraremos NAT estático para nuestra instancia `acme-staging-web-01`. El ejemplo comienza en la pestaña *Redes* de nuestro entorno. La instancia ejecuta CentOS y se ha implementado en la VPC `acme-vpc-staging`, en la red `acme-net-frontend`. La red `acme-net-frontend` tiene la siguiente ACL aplicada:

| Número de regla | Descripción | CIDR | Acción | Protocolo | Tipo de tráfico | Puerto de inicio | Puerto final |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 10 | Permitir entrada HTTP | 0.0.0.0/0 | Permitir | TCP | Ingreso | 80 | 80 |
| 20 | Denegar todo otro tráfico entrante | 0.0.0.0/0 | Denegar | TCP | Ingreso | 1 | 65535 |

1. Haz clic en el ícono de ajustes a la derecha de la sección *Acceso público*. Aparece la pantalla *Direcciones IP públicas*.
1. Haz clic en *Adquirir dirección IP pública*. Cuando aparezca el cuadro de diálogo de confirmación, haz clic en *Aplicar*.
1. La dirección IP pública (45.72.188.68) ahora aparece en la lista. Haz clic en el menú de tres puntos y selecciona *Habilitar NAT estática*.
1. En la pantalla *Habilitar NAT estática*, selecciona la instancia de destino (`acme-staging-web-01`), luego selecciona la dirección IP privada de destino deseada (10.210.69.62).
1. Haz clic en *Aplicar*. Cuando aparezca la pantalla *Direcciones IP públicas*, verá que la IP pública 45.72.188.68 ahora está etiquetada como **NAT estática**.


### Comprobación

Probaremos la conectividad a través de la NAT estática utilizando las utilidades `tcpdump` y `nc`. Puedes usar stu propio método para confirmar que el NAT estático funciona como se esperaba.

1. Abre la consola de tu máquina virtual desde la pestaña *Instancias*.
1. Cuando se abra la ventana de la consola, inicia sesión en la instancia.
1. Ejecuta el siguiente comando:
`sudo tcpdump puerto 80`
1. En tu estación de trabajo local, abre una ventana de terminal y ejecuta el siguiente comando:
`nc 45.72.188.68 80`
1. `tcpdump` genera dos líneas que indican que el tráfico que se origina en tu estación de trabajo llega a tu instancia a través de la NAT estática.
<!-- ![Results of tcpdump](/assets/static-nat-tcpdump-en.png) -->
