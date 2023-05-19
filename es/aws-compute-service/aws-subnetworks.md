---
title: "AWS: Subredes"
slug: aws-subredes
---


Una subred es una parte de una VPC de AWS que se puede utilizar para implementar instancias. Una sola subred puede usar una parte del rango de IP de su VPC, o puede usar el rango de IP completo de la VPC.

Al igual que una VPC, una subred se define mediante un CIDR. El CIDR de la subred debe existir completamente dentro del CIDR de la VPC y no debe superponerse al CIDR de ninguna otra subred dentro de la misma VPC. Existe una subred dentro de una única zona de disponibilidad de AWS.

La elección de la subred determinará la zona de disponibilidad de una instancia. Esto afecta qué volúmenes están disponibles para adjuntar a una instancia.

Las subredes se encuentran en la pestaña **Redes** de su entorno de AWS. Busque la VPC deseada y haga clic en la función **Subredes** para ver una lista completa.

**Tema principal:** [AWS: Redes](aws-networking.md)

