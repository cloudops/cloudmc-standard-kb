---
title: "AWS: Grupos de seguridad"
slug: aws-grupos-de-seguridad
---


Los grupos de seguridad son conjuntos de reglas que brindan control sobre el acceso de red a tus recursos en un entorno de AWS.

Al implementar una nueva instancia, el asistente **Agregar instancia** presenta tres opciones:

- **Permitir el tráfico de todas las fuentes**

     El grupo de seguridad permitirá el tráfico de entrada desde todas las direcciones IP, para todos los protocolos y números de puerto.

- **Habilitar el tráfico solo para HTTP, HTTPS y SSH**

     Esto creará un grupo de seguridad que deniega todo el tráfico de entrada, excepto los puertos TCP 22, 80 y 443. Ingresa un nombre y una descripción para los grupos, o acepte los valores predeterminados.

- **Configurar una política de grupo de seguridad personalizada**

     Se puede especificar una dirección IP o un bloque CIDR, protocolo y números de puerto para permitir la entrada. Ingresa un nombre y una descripción para el grupo de seguridad, o acepta los valores predeterminados, luego ingresa los criterios para el grupo.


**Tema principal:** [AWS: Redes](aws-networking.md)

