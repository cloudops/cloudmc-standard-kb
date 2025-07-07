---
title: "AWS: Añadir un equilibrador de carga de aplicaciones"
slug: aws-añadir-equilibrador-de-carga-de-aplicaciones
---


## Acerca de esta tarea

Este artículo te guiará por los pasos necesarios para implementar un balanceador de carga de aplicaciones.

## Antes de comenzar

- Debes tener un entorno de AWS con un grupo de destino

## Procedimiento

1. Ve a tu entorno de AWS, luego a **Equilibrio de carga** > **Equilibradores de carga de aplicaciones** y haz clic en el botón **Añadir equilibrador de carga**.

2. Cuando aparezca el asistente **A˜ãdir equilibrador de carga**, introduce un nombre para el nuevo equilibrador de carga en el campo **Nombre**.

3. En el campo **Esquema**, selecciona si el equilibrador de carga recibirá tráfico público de Internet o tráfico procedente de una dirección IP privada.

4. En el campo **Tipo de Dirección IP**, selecciona **IPv4** para comunicar con destinos que usan IPv4 o **Dualstack** para comunicarse con destinos que usan IPv6.

5. Haz clic en el botón **Siguiente**.

6. En la sección **Mapeo de la red**, selecciona la VPC con los destinos deseados y, a continuación, selecciona al menos dos subredes a las que el equilibrador de carga enviará tráfico.

7. Haz clic en el botón **Siguiente**.

8. En la sección **Grupos de seguridad**, selecciona el grupo de seguridad que se aplicará al nuevo equilibrador de carga y, a continuación, haz clic en el botón **Siguiente**.

9. En la sección **Oyentes y enrutamiento**, selecciona el protocolo, especifica el número de puerto al que se enviará el tráfico y selecciona el grupo de destino con los destinos registrados. Puedes agregar varios oyentes.

10. Haz clic en el botón **Siguiente**.

11. \(Opcional\) En la sección **Etiquetas del equilibrador de carga**, introduce el par nombre-valor para etiquetar el equilibrador de carga.

12. Haz clic en el botón **Siguiente**.

13. Revisa la configuración y haz clic en el botón **Aplicar** para crear el equilibrador de carga.

## Resultados

- El equilibrador de carga de aplicaciones se creará con el grupo de destino especificado
- El equilibrador de carga ahora aparece en la página **Equilibradores de carga de aplicaciones**
- Una vez finalizado el aprovisionamiento, el equilibrador de carga estará en estado **Activo**