---
title: "CloudStack: Trabajar con las API de cómputo de CloudStack"
slug: cloudstack-trabajar-con-la-api-de-computo-de-cloudstack
---


Como usuario de CloudMC, tienes acceso a un subconjunto de la API de cómputo de CloudStack para habilitar sus flujos de trabajo de automatización.

### Acceso a la API de cómputo de CloudStack

La documentación está disponible para la [API de usuario de CloudStack](http://cloudstack.apache.org/api/apidocs-4.7/TOC_User.html) (*en inglés*).

Se puede llamar a estas API basadas en HTTP mediante [elaboración manual](http://docs.cloudstack.apache.org/en/latest/dev.html#making-api-requests) y [firmando la solicitud de API](http://docs.cloudstack.apache.org/en/latest/dev.html#signing-api-requests). O puedes usar una de las muchas bibliotecas de contenedores disponibles para el lenguaje de programación de su elección.

#### Obtención de puntos de entrada de la API

Para obtener la información necesaria para realizar llamadas API a cualquiera de sus entornos, haga lo siguiente:

1. En el menú de nombre de usuario (en la barra de menú), selecciona **Credenciales de API**.
1. Debajo de la sección **Claves de API de servicio**, selecciona el **servicio** y el **entorno** deseados. Se muestran el punto de entrada HTTP, la clave de API y la clave secreta necesarios para llamar a las API de usuario de CloudStack. Debido a que existe una relación de uno a uno entre un *entorno* de CloudMC y un *proyecto* de CloudStack, también se le proporciona el parámetro de consulta necesario para apuntar al proyecto de CloudStack correspondiente.
