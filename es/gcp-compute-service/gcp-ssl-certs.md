---
title: "GCP: Certificados SSL"
slug: gcp-certificados-ssl
---


CloudOps te permite cargar un [certificado SSL](https://es.wikipedia.org/wiki/Certificado_de_clave_p%C3%BAblica) y tu clave privada asociada a su entorno de Google Cloud Platform, y vincularlos a un **proxy de destino** para proporcionar conexiones HTTPS a tus clientes. Los certificados pueden estar firmados por una autoridad de certificación (CA), por un certificado intermedio o pueden ser autofirmados.

Actualmente, GCP limita los certificados SSL a lo siguiente:
    - El certificado y la clave privada deben estar en formato PEM
    - La clave privada no debe tener frase de contraseña
    - La clave privada debe ser de 2048 bits.

Los certificados SSL se pueden administrar en CloudOps navegando al entorno de GCP deseado, seleccionando la pestaña **Redes**, haciendo clic en el elemento **Balanceo de carga** y haciendo clic en **Certificados SSL**.

### Subiendo un certificado SSL

1. Desde la página **Certificados SSL**, haz clic en el botón *Agregar un certificado SSL*.
    ![La página para agregar un certificado SSL](../../assets/gcp-ssl-cert-1-en.png)
1. Ingresa un nombre o acepta el predeterminado e ingresa una descripción si lo deseas.
1. Pega el certificado completo, incluidas las líneas de encabezado y pie de página, en el cuadro de texto etiquetado *Certificado público*.
1. Pega los certificados intermedios, incluidas las líneas de encabezado y pie de página, en el cuadro de texto etiquetado *Cadena de certificación*.
    - Si hay más de un certificado intermedio, colócalos en orden desde el más bajo (el certificado que se utilizó para firmar el certificado cargado) al más alto (el certificado que se firmó con el certificado raíz). No dejes espacios entre la línea de pie de página de un certificado y la línea de encabezado del siguiente.
1. Pega la clave privada del certificado que se estás cargando.
1. Haz clic en *Enviar*.
1. El certificado ahora aparecerá listado en la página **Certificados SSL**.
   ![La página de certificados SSL](../../assets/gcp-ssl-cert-2-en.png)

### Eliminar un certificado SSL

Un certificado SSL no se puede eliminar si lo estás utilizando un proxy de destino.

1. Desde la página **Certificados SSL**, busca el certificado en la lista y selecciona el menú *Acción* en el extremo derecho de la entrada. Haz clic en *Eliminar*.
1. Aparecerá un cuadro de diálogo de confirmación. Haz clic en *Aplicar*.
1. El certificado se eliminará del entorno de GCP.
