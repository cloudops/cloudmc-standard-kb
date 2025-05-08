---
title: "AWS: Desplegar RDS"
slug: aws-desplegar-rds
---


## Acerca de esta tarea

Este artículo te guiará por los pasos para implementar RDS y también incluye los prerrequisitos, así como un método de prueba.

## Antes de comenzar

- El entorno de destino debe tener al menos una VPC.
- La VPC debe haber al menos dos subredes con CIDR no superpuestos.
- Las subredes deben estar en zonas de disponibilidad separadas.
- Para realizar pruebas después de la implementación, debes tener una instancia en la misma subred que el punto final de la base de datos.

## Procedimiento

**Crear un grupo de subredes de base de datos**

1\. Navega al entorno de AWS de destino y haz clic en la pestaña **Bases de datos**. Luego, haz clic en **Grupos de subredes de BD**.

2\. Haz clic en el botón **Añadir grupo de subredes de base de datos**. Aparecerá la página **Añadir grupo de subredes de BD**.

3\. Ingresa un nombre y una descripción para el grupo de subredes.

4\. Selecciona la VPC de destino en el menú emergente **VPC**.

5\. Selecciona las subredes de destino en el menú emergente **Subredes**.

   Se debe seleccionar al menos dos subredes para poder continuar.

6\. Haz clic en el botón **Aplicar** para guardar el grupo de subredes de base de datos.

**Desplegar la instancia de base de datos**

7\. Haz clic en la opción **Bases de datos** y, a continuación, en el botón **Añadir base de datos**.

8\. Cuando aparezca el asistente **Añadir base de datos**, en la sección **Configuración general**, introduce un nombre para la instancia de la base de datos y selecciona un tipo de motor de base de datos. Haz clic en **Siguiente**.

9\. En la sección **Tipo de instancia**, selecciona el tipo de instancia donde deseas desplegar la base de datos y, a continuación, haz clic en **Siguiente**.

10\. Cuando aparezca la sección **Almacenamiento**, selecciona el tipo de volumen y el tamaño que deseas asignar al volumen raíz de la instancia. También se puede habilitar el escalado automático del almacenamiento; aparecerá un campo de texto donde podrás introducir el tamaño máximo al que se escalará. Haz clic en **Siguiente**.

11\. En la sección **Red**, selecciona el grupo de subredes que se creó anteriormente. Haz clic en **Siguiente**.

12\. La sección **Credenciales** te permite introducir un nombre de usuario y una contraseña para el usuario maestro en la base de datos.

**Atención:** Asegúrate de guardar la contraseña en un lugar seguro, ya que no se puede recuperar. Si la pierdes, deberás restablecerla.

13\. Haz clic en el botón **Siguiente**. Revisa los parámetros seleccionados en todas las secciones.

14\. Haz clic en el botón **Aplicar** para crear la instancia de la base de datos.

**Nota:** La implementación puede tardar varios minutos en completarse.

**Probar la conectividad**

15\. Una vez creada la base de datos, navega a la pestaña **Bases de datos**, haz clic en ella para ver sus detalles y navega a la sección **Punto de acceso**.

La sección **Punto de acceso** mostrará el nombre de dominio y el número de puerto que debes usar para acceder a la instancia de la base de datos.

16\. Utiliza el cliente de base de datos adecuado con el nombre de usuario y la contraseña definidos en la sección **Credenciales** para conectarte a la instancia de la base de datos.

## Resultados

- La nueva base de datos RDS se ha creado y aparece en la pestaña **Bases de datos**.
- Has verificado la conectividad conectándote a la instancia con el punto final y las credenciales adecuados.
- La instancia de la base de datos ya está lista para funcionar.