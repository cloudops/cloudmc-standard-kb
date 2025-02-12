---
title: "GCP: Comprobaciones de estado"
slug: gcp-comprobaciones-de-estado
---


Las comprobaciones de estado de Google Cloud Platform te permiten definir los criterios de disponibilidad de una instancia que proporciona un servicio de backend. Se aplica una comprobación de estado a un grupo de instancias cuando se configura un servicio de backend de GCP. Una vez que una comprobación de estado está activa, GCP enviará una solicitud simple a la instancia de destino cada 5 segundos. Si la instancia responde con HTTP 200 OK, se considera que la instancia está en buen estado. Si la solicitud expira después de 5 segundos, o si la respuesta es diferente a HTTP 200 OK, la instancia se considera en mal estado y no se enviarán solicitudes entrantes hasta que vuelva a un estado correcto.

Las comprobaciones de estado se pueden administrar navegando a tu entorno de GCP en CloudOps, haciendo clic en la pestaña **Cómputo** y haciendo clic en el elemento **Comprobaciones de estado**.

### Crear una comprobación de estado

1. Desde la página *Comprobaciones de estado*, haz clic en el botón *Agregar una comprobación de estado*.
1. Ingrese un nombre o acepte el predeterminado e ingrese una descripción si lo desea.
1. Seleccione el protocolo a usar (HTTP o HTTPS) e ingrese el número de puerto al que conectarse en la instancia de backend.
1. Haz clic en *Aplicar*. Aparecerá la página *Comprobaciones de estado* y se incluirá la nueva comprobación de estado.

De forma predeterminada, CloudOps creará una verificación de estado que consulta la ruta raíz ("/"). GCP permite que las verificaciones de estado consulten otras rutas. CloudOps mostrará la ruta de solicitud de una verificación de estado en la lista de la página *Comprobaciones de estado*.

### Eliminar una comprobación de estado

Una comprobación de estado no se puede eliminar si está siendo utilizada por un servicio de backend.

1. En la página *Comprobaciones de estado*, busca la comprobación de estado deseada y haz clic en el menú *Acción* en el extremo derecho de la entrada. Haz clic en *Eliminar*.
1. Aparecerá un cuadro de diálogo de confirmación. Haz clic en *Aplicar*.
1. La verificación de estado se eliminará del entorno de GCP.
