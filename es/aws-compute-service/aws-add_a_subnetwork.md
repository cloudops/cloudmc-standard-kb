---
title: "AWS: Agregar una subred"
slug: aws-agregar-una-subred
---


## Acerca de esta tarea

Este artículo te guiará a través del proceso de agregar una nueva subred a tu VPC AWS.

## Antes de comenzar

- Debes tener una VPC en tu entorno de AWS
- El rango de IP de la VPC debe tener un bloque que no esté asignado a otra subred
- Si no deseas utilizar los valores predeterminados proporcionados por el sistema, debes tener el nombre, el rango de IP y la zona de disponibilidad de AWS que deseas asignar a la nueva subred.

## Procedimiento

1. Navega hasta el entorno deseado y haz clic en **Redes**.

2. Busca la VPC deseada y haz clic en el ícono de engranaje en la sección **Subredes**. Aparecerá la página **Subredes**.

3. Haz clic en el botón **Agregar subredes**. Aparece la página **Agregar subredes**.

4. Introduce un nombre para la nueva subred en el campo **Nombre** o acepta el predeterminado.

5. Ingresa el rango de IP deseado, utilizando la notación CIDR, en el campo **CIDR**.

     El CIDR de la subred debe existir completamente dentro del CIDR de la VPC y no debe superponerse al CIDR de ninguna otra subred dentro de la misma VPC. Consulta [Subredes](aws-subnetworks.md) para obtener más información.

     El sistema presentará un error si se proporcionas un CIDR no válido.

6. Selecciona la zona de disponibilidad deseada en el menú emergente **Zona de disponibilidad** o acepta el valor predeterminado.

7. Haz clic en el botón **Aplicar**.


## Resultados

- Se crea la subred y se puede usar para agregar instancias
- Tiene el rango de IP especificado por el CIDR
- La subred aparece en la pantalla **Subredes** de la VPC en la que se creó

## Ejemplo: Agregar una subred

### Acerca de esta tarea

En este ejemplo, agregaremos una subred a la VPC `acme-prod-vpc01`. Queremos usar solo la mitad del rango de IP, por lo que especificaremos un tamaño de red de /27.

### Antes de comenzar

- La VPC `acme-prod-vpc01` ya debe existir en el entorno de `producción` de AWS.

### Procedimiento

1. Navega hasta el entorno de `producción` de Acme y haz clic en **Redes**.

2. Busca la VPC `acme-prod-vpc01` y haz clic en el ícono de engranaje en la sección **Subredes**. Aparecerá la página **Subredes**.

3. Haz clic en el botón **Agregar subredes**. Aparece la página **Agregar subredes**.

4. Ingresa `acme-prod-net-frontend` en el campo **Nombre**.

5. Ingresa `172.16.0.0/27` en el campo CIDR.

     Esto nos dará la subred deseada, compuesta por 32 direcciones IP que van desde la 172.16.0.0 hasta la 172.16.0.31.

6. Acepta la zona de disponibilidad predeterminada.

7. Haz clic en el botón **Aplicar**.


### Resultados

- Se crea nuestra nueva subred `acme-prod-net-frontend` y se puede usar para agregar instancias
- Tiene el rango de IP de 172.16.0.0 a 172.16.0.31
- La subred aparece en la pantalla **Subredes** de la VPC `acme-prod-vpc01`

