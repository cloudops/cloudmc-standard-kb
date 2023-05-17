---
title: "AWS: Agregar una VPC"
slug: aws-agregar-una-vpc
---


## Acerca de esta tarea

Este artículo te guiará a través del proceso de agregar una nueva VPC a un entorno de AWS.

## Antes de comenzar

- Tu entorno de AWS ya debe existir
- Si no deseas utilizar los valores predeterminados proporcionados por el sistema, debes tener el nombre y el CIDR que deseas asignar a la nueva VPC

## Procedimiento

1. Haz clic en el botón **Agregar una red VPC**. Aparecerá la página **Agregar una red VPC**.

2. Introduce un nombre para la nueva VPC en el campo **Nombre** o acepta el valor predeterminado.

3. Ingresa el CIDR deseado para la nueva VPC en el campo **CIDR** o acepta el valor predeterminado.

     El CIDR expresa el tamaño y el rango de direcciones IP que se usarán para definir la nueva VPC. Consulta [VPCs](aws-vpcs.md) para obtener más detalles.

     El sistema presentará un error si se proporciona un CIDR no válido.

4. Haz clic en **Aplicar**.


## Resultados

- Se crea la VPC y se puede usar para agregar subredes
- Tiene el rango de IP especificado por el CIDR
- La VPC aparece en la pestaña **Redes**

## Ejemplo: Agregar una VPC

### Acerca de esta tarea

En este ejemplo, agregaremos una nueva VPC al entorno de AWS de `producción` de Acme. Deseamos tener una VPC más pequeña que la predeterminada, por lo que usaremos un CIDR con una máscara de subred de /26.

### Antes de comenzar

- El entorno de `producción` de Acme ya debe existir

### Procedimiento

1. Navega hasta el entorno de `producción` de Acme y haz clic en **Redes**.

2. Haz clic en el botón **Agregar una red VPC**. Aparecerá la página **Agregar una red VPC**.

3. Ingresa `acme-prod-vpc01` en el campo **Nombre**.

4. Ingresa `172.16.0.0/26` en el campo **CIDR**.

     Esto nos dará el rango de IP más pequeño deseado de 64 direcciones, comenzando en 172.16.0.0 y terminando en 172.16.0.63.

5. Haz clic en **Aplicar**.


### Resultados

- Se crea nuestra nueva VPC `acme-prod-vpc01` y se puede usar para crear subredes
- La VPC tiene el rango de IP de 172.16.0.0 a 172.16.0.63
- Aparece en la pestaña **Redes**

