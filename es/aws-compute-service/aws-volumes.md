---
title: "AWS: Volúmenes"
slug: aws-volumenes
---


Un volumen en Amazon Web Services es donde puedes almacenar datos de forma permanente para usar con tus instancias. Para una instancia que se ejecuta en AWS, un volumen es indistinguible de un disco físico que está conectado al sistema. Los volúmenes residen en la infraestructura con una sola zona de disponibilidad y solo se pueden adjuntar a instancias dentro de la misma zona. La zona de disponibilidad no se puede cambiar una vez que se aprovisiona un volumen.

Cada instancia tiene un volumen con un tipo de volumen de `Root` (`raíz` en español). Este volumen contiene el sistema operativo y, a menudo, contiene software adicional. No se puede iniciar una instancia sin un volumen raíz.

Se pueden aprovisionar y adjuntar o separar volúmenes adicionales de las instancias según sea necesario. Cuando se adjuntan a una instancia, se pueden particionar, formatear y cambiar de tamaño. Un volumen puede separarse de una instancia y luego adjuntarse a otra instancia en la misma zona de disponibilidad. Los datos almacenados en el volumen se conservan independientemente de si están conectados a una instancia o no.

AWS ofrece varios tipos de volúmenes, que ofrecen diferentes niveles de rendimiento y precio del disco. Al crear un volumen, especifica el tipo de volumen deseado. El tipo de volumen no se puede cambiar una vez que se aprovisiona un volumen.

Al adjuntar volúmenes a instancias, cada volumen debe tener un nombre de dispositivo único. Este es un nombre de archivo que usará el sistema operativo en la instancia cuando interactúe con el volumen. El nombre del dispositivo toma la forma de `/dev/sd*` o `/dev/xvd*`. Al adjuntar un volumen, CloudMC proporcionará un nombre de dispositivo predeterminado razonable. El nombre del dispositivo `/dev/sda1` es un nombre especial y está reservado para el volumen raíz de una instancia.

En algunas circunstancias, un volumen adjunto a una instancia puede configurarse con la opción **Eliminar en el momento de terminar**. Cuando está habilitado para un volumen, el volumen se eliminará automáticamente si se elimina su instancia adjunta. Utilice esta opción con precaución, la eliminación de un volumen es una operación permanente y no se puede deshacer.

Los volúmenes se enumeran en la pestaña **Cómputo** de su entorno de AWS, en la sección **Volúmenes**.

**Tema principal:** [AWS: Cómputo](aws-compute.md)

