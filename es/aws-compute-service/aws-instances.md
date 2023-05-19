---
title: "AWS: Instancias"
slug: aws-instancias
---


Al igual que otras plataformas en la nube, AWS le proporciona la infraestructura para ejecutar máquinas virtuales. Estas máquinas virtuales se denominan instancias. Una instancia se basa en una imagen predefinida llamada **[AMI](aws-amis.md)**, que no se puede cambiar una vez que se implementa una instancia. Diferentes conjuntos de especificaciones se agrupan como tipos de instancia. Cada tipo de instancia es un paquete de varios tamaños de vCPU, memoria y un volumen de almacenamiento raíz. Para obtener más detalles, consulte [Tipos de instancias de Amazon EC2](https://aws.amazon.com/es/ec2/instance-types/) en la documentación de AWS.

Al implementar una instancia, se debe seleccionar una región de AWS. La región determina qué subredes, volúmenes, AMI y otros recursos estarán disponibles para las nuevas instancias.

Con las reglas de escalado automático, puedes definir las condiciones bajo las cuales el sistema de AWS implementará automáticamente instancias adicionales, en caso de que su aplicación requiera más recursos informáticos. Todas las instancias añadidas tendrán un nombre y una configuración idénticos. AWS creará hasta el número máximo de instancias definidas en el campo **Número máximo de instancias** en la página **Agregar instancia**. AWS también finalizará las instancias innecesarias cuando se cumplan las condiciones, hasta el valor especificado en el campo etiquetado **Número mínimo de instancias**, también en la página **Agregar instancia**. Para mayor comodidad, esta guía se referirá a la creación de una sola instancia, pero si eligas crear más de una instancia, la configuración seleccionada se aplicará a todas las instancias por igual.

Para iniciar sesión en una instancia, usa el par de claves SSH que se crea automáticamente al crear la instancia. La clave SSH privada es su única forma de iniciar sesión en la instancia y debe almacenarse e instalarse de manera segura en la aplicación SSH que usará para conectarse a la instancia. Cuando se crean varias instancias a través del escalado automático, puedes usar esta clave SSH privada para conectarte a cada instancia.

**Importante:** Debes almacenar de forma segura la clave SSH privada inmediatamente. No se almacenará en ningún lugar de la interfaz de usuario de CloudMC y no se podrá recuperar una vez que se borre la notificación del panel. No se puede iniciar sesión en una instancia sin esta clave. Si se pierde, deberás seguir un procedimiento de recuperación, que requiere el reinicio de la instancia.

Las instancias se enumeran en la pestaña **Cómputo** de tu entorno de AWS, en la sección **Instancias**.

**Tema principal:** [AWS: Cómputo](aws-compute.md)

