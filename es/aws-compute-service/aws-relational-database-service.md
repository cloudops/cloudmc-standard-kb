---
title: "AWS: Relational Database Service"
slug: aws-rds
---


La plataforma CloudOps te permite utilizar el servicio de base de datos administrado AWS Relational Database Service \(RDS\) para implementar fácilmente una instancia de base de datos en tu entorno.

## Resumen

AWS Relational Database Service ofrece bases de datos administradas como un servicio práctico, que pueden utilizarse como cualquier otra base de datos, sin necesidad de operar ni mantener un sistema de gestión de bases de datos relacionales complejo (RDBMS). Un usuario de RDS accede a la base de datos a través de un punto final de red mediante un cliente o un conector de base de datos. Mientras tanto, AWS se encarga de las licencias, los respaldos y otras tareas operativas.

Para acceder a las funciones de RDS, se navega al entorno de AWS que deseas y haz clic en la pestaña **Bases de datos**.

![Captura de pantalla de la pestaña de bases de datos de AWS, con puntos numerados que indican características de interés](aws-rds-databases-list.png)

1. **Lista de instancias de base de datos**

En el área principal del espacio de trabajo, aparece una lista de todas las instancias de base de datos en el entorno seleccionado.

2. **Cuadro de búsqueda**

Escribe en el cuadro de búsqueda para filtrar la lista de instancias de base de datos. El sistema buscará en los campos de identificador de la base de datos y devolverá cualquier base de datos que coincida con la cadena del cuadro de búsqueda.

3. **Añadir base de datos**

Al hacer clic en este botón, se abrirá la página **Añadir base de datos**.

4. **Entrada de instancia de base de datos**

Cada entrada incluye el identificador \(nombre\) de la base de datos, su estado, el motor de base de datos que se está ejecutando y si la base de datos es una instancia o un clúster.

5. **Menú de acciones ocultas**

Cada entrada de la lista de bases de datos tiene un menú de acciones ocultas. Haz clic en el menú de acciones ocultas para acceder a una lista de operaciones frecuentes para la base de datos, como la gestión de etiquetas, la creación de instantáneas y la eliminación de la instancia.


Al implementar una instancia de RDS, deberás elegir un grupo de subredes de base de datos donde residirá la instancia. El grupo de subredes de base de datos debe contener al menos dos subredes. Estas dos subredes deben estar en zonas de disponibilidad separadas y deben tener CIDR no superpuestos. Al crear la instancia, puedes elegir entre los siguientes atributos:

- Tipo de motor de base de datos
- Tipo de instancia
- Tipo y tamaño del volumen raíz
- Escalado automático para almacenamiento
- Grupo de subredes de base de datos
- Credenciales para conectarse a la instancia de base de datos

## Copias instantáneas de base de datos

Para preservar el estado de tu instancia de base de datos en un momento específico, se puede tomar una copia instantánea. Esta no es un respaldo de la base de datos, sino una imagen de toda la instancia y de todas las bases de datos implementadas en ella. Las copias instantáneas no están diseñadas para un uso a largo plazo. Además, se aplicarán cargos por cada copia instantánea guardada.

Las copias instantáneas se pueden crear mediante el menú "Acciones ocultas" de la instancia deseada y seleccionando "Crear instantánea".