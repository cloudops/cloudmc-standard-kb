---
title: "AWS: VPCs"
slug: aws-vpcs
---


Una nube privada virtual, denominada VPC, es una característica estándar de la computación basada en la nube y proporciona la estructura de red subyacente donde se implementan las instancias. A una VPC se le asigna un rango de IP y puede alojar una o más subredes dentro de ese rango. Luego se pueden crear instancias según sea necesario dentro de una subred. Consulta [¿Qué es una VPC?](../cloudstack-compute-service/what-is-a-vpc.md) para obtener información general sobre las VPCs.

Un entorno de CloudMC AWS recién creado tendrá una VPC predeterminada. Puedes crear VPCs adicionales según sea necesario. También puedes eliminar las VPCs. Si se eliminan todas las VPCs, deberás crear al menos una VPC antes de agregar una nueva instancia.

<hr>
PELIGRO

Eliminar una VPC eliminará todas las instancias, subredes, tablas de ruteo y grupos de seguridad en la VPC. Todos los volúmenes adjuntos a las instancias en la VPC eliminada y marcados como **Eliminar en el momento de terminar** se destruirán y se perderán todos los datos almacenados en esos volúmenes. Esto es permanente y no se puede deshacer.
<hr>

Al asignar un rango de IP a una VPC, se utiliza una notación llamada CIDR. El CIDR especifica la primera dirección IP del rango y usa un sufijo para indicar el tamaño del rango. Los tamaños comunes para redes más pequeñas son /24 y /26, que brindan 256 y 64 direcciones IP, respectivamente, y las redes más grandes pueden usar /16, que brinda 65 536 direcciones. Para ingresar un CIDR en CloudMC, use el formato `X.X.X.X/Y`. Por ejemplo, `192.168.0.0/24`.

**Consejo:** Para especificar una sola dirección IP en notación CIDR, ingrese la dirección IP con una máscara de red de 32, por ejemplo, `172.217.165.14/32`.

Antes de que se pueda usar una VPC para implementar instancias, se debe agregar al menos una subred dentro de la VPC. Una VPC puede tener múltiples subredes siempre que sus rangos de IP no se superpongan y se encuentren completamente dentro del rango de la VPC. Las subredes pueden ser la misma zona de disponibilidad de AWS o estar en zonas separadas. Ten en cuenta que la elección de VPC para una instancia determinará qué subred estará disponible para esa instancia.

Las VPCs se enumeran en la pestaña **Redes** de tu entorno de AWS, en la sección **Redes VPC**.

**Tema principal:** [AWS: Redes](aws-networking.md)

