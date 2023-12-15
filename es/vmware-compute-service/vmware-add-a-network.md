---
title: "VMware: Agregar una red"
slug: vmware-agregar-una-red
---

## Acerca de esta tarea

Este artículo lo guiará a través del proceso de agregar una nueva red a un entorno VMware. La interfaz de CloudMC proporciona un asistente de una sola página para seleccionar e implementar una nueva configuración de red.

## Antes de comenzar

- Su entorno VMware ya debe existir
- Para crear una red enrutada NAT, debe tener una puerta de enlace Edge ya configurada

## Procedimiento

1. Navegue hasta el entorno deseado. Aparece la página **Máquinas virtuales**.

2. Haga clic en la pestaña **Redes**.

3. Haga clic en el botón **Agregar red**. Aparece el asistente **Agregar red**.

4. Configure la nueva red:

     1. Ingrese un nombre en el campo **Nombre** o acepte el valor predeterminado.

     2. *\(Opcional\)* Ingrese una descripción en el campo **Descripción**.

     3. Ingrese una dirección IP en formato CIDR para la puerta de enlace en el campo **CIDR de la puerta de enlace**.

         El sistema interpretará esta entrada para el número de red y la máscara de subred y los utilizará para configurar la dirección y el tamaño de la red. La dirección IP en sí se asignará automáticamente a la puerta de enlace que se creará para esta red.

     4. Seleccione el tipo de red deseado en el menú emergente **Tipo de red**.

         Para proporcionar conectividad externa a su red, elija **Enrutada**. Se le pedirá que especifique una puerta de enlace Edge en el menú emergente **Puertas de enlace Edge**. Si no se configura ninguna puerta de enlace perimetral para este entorno, la nueva red no podrá conectarse al Internet público.

         Si no necesita conectividad externa para su red, elija **Aislada**. Esto es útil para redes que tienen información privilegiada o confidencial, o para cumplir con restricciones de acceso y otras reglas comerciales.

    5. Ingrese una o más direcciones IP, o rangos de IP, en el campo **Grupos de IP estáticas** para reservarlas para la asignación estática.

         Estas direcciones no serán ofrecidas por el servidor DHCP de la nueva red. Esto es útil para asignar manualmente direcciones IP a interfaces en la red. Todas las direcciones deben estar dentro del espacio de direcciones de la nueva red, como se especifica en el campo **CIDR de la puerta de enlace**.

         Puede ingresar una única dirección IP o un único rango contiguo \(especifique las direcciones IP más baja y más alta del rango, separadas por un guión\). Para especificar múltiples rangos o direcciones IP individuales, use el botón **+** para revelar campos de entrada adicionales.

    6. *\(Opcional\)* Para anular los servidores DNS primarios predeterminados \(y, si lo desea, secundarios\) que ofrecerá el servidor DHCP, ingrese las direcciones IP de sus servidores de nombres en los campos **DNS primario** y **DNS secundario**.

5. Haga clic en el botón **Aplicar**.


## Resultados

- La red con la configuración especificada se realiza en el entorno activo.
- El espacio de direcciones IP, el tamaño de la red y la dirección IP de la puerta de enlace son los especificados en el campo **CIDR de la puerta de enlace**
- La red aparece en la pestaña **Redes**



