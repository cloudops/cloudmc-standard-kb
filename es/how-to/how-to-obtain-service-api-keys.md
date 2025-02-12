---
title: "Cómo obtener claves API de servicio"
slug: como-obtener-claves-api-de-servicio
---


Algunos servicios permiten la conexión directa a su API utilizando las claves API de su servicio CloudOps. Para obtener tus claves de API de servicio, navega hasta el menú de usuario en la parte superior derecha de la página, haz clic en **Credenciales de API**, luego desplácete hacia abajo hasta la sección titulada *Claves de API de servicio*. Haz clic en el cuadro de búsqueda y selecciona el servicio deseado. Las claves API de servicio para el servicio seleccionado aparecerán debajo.

![Claves API de servicio](/assets/api-service-keys-es-1.png)

### Credenciales para almacenamiento de objetos usando Keystone v3 (predeterminado)

El proyecto OpenStack proporciona 2 CLI para interactuar con Object Store: la [CLI genérica de OpenStack](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) y la [CLI Swift](https://www.swiftstack.com/docs/integration/python-swiftclient.html), que se configuran de la misma manera.  Necesitarás los siguientes parámetros:

![Parámetros de OpenStack](/assets/api-service-keys-en-2.png)

Luego puedes exportar las siguientes variables de entorno (reemplace los valores de **OS_PASSWORD**, **OS_USERNAME** y **OS_PROJECT_NAME** con los del portal):

```
export OS_PASSWORD=hunter2
export OS_USERNAME=system-ccontini-2925
export OS_PROJECT_NAME=system-ccontini
export OS_AUTH_URL=https://auth.cloud.ca
export OS_IDENTITY_API_VERSION=3
```

<!-- ### Credenciales para la API compatible con S3
The AWS CLI requires several pieces of information to connect to the S3 endpoint, including the secret key and the access key, which are available at the same place as your regular cloud.ca Object Storage credentials, as well as the endpoint URL and a region name. The endpoint URL is always **https://objects.cloud.ca** and the region name *cloud.ca*.

![OpenStack S3 API key](/assets/api-service-keys-en-3.png)

**Note:** If it is the first time you use the S3 API in this environment, you might need to click the "Regenerate" button on the right of the screen. Warning: this will regenerate a new password for this user for object storage (Swift and AWS), for all the environments he or she currently is part of. Alternatively, you can remove the user from the environment, and re-add it. This does not change the password for this user for any environment he or she is currently a member.

You can then configure the AWS CLI by updating the file `~/.aws/credentials` with the following content (replace the value of *aws_access_key_id* and *aws_secret_access_key* with those from the portal):

```
[default]
region = cloud.ca
aws_access_key_id = 076d7a255a4236965ba97b4f91363f2
aws_secret_access_key = ********************
s3 =
endpoint_url = https://objects.cloud.ca
```
--> 

### Credenciales para almacenamiento de objetos mediante Keystone v2.0 (obsoleto)

El almacenamiento de objetos aún admite conexiones mediante Keystone v2.0. Sin embargo, este método está en desuso y se eliminará en el futuro. Para usar la [CLI genérica de OpenStack](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) y la [CLI Swift](https://www.swiftstack.com/docs/integration/python-swiftclient.html) con credenciales v2.0, utiliza la siguiente información:

![Parámetros de OpenStack](/assets/api-service-keys-en-4.png)

Luego, exporte las siguientes variables de entorno (reemplace el valor de **OS_USERNAME**, **OS_PROJECT_NAME** y **OS_PASSWORD** con los del portal):

```
export OS_USERNAME=system-ccontini-2925
export OS_PROJECT_NAME=system-ccontini
export OS_PASSWORD=hunter2
export OS_AUTH_URL=https://auth.cloud.ca/v2.0
```
