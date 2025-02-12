---
title: "Autenticar con OpenID Connect"
slug: openid-connect
---


### Resumen de OpenID Connect

OpenID Connect (OIDC) es un sistema de autenticación basado en OAuth 2.0 y actualmente es el sistema de autenticación externo más adoptado.

Con OpenID Connect configurado, una persona puede iniciar sesión en su cuenta de CloudOps utilizando credenciales válidas de un proveedor de identidad externo. Además, si una organización ha configurado un dominio personalizado, CloudOps puede, opcionalmente, crear una nueva cuenta de usuario automáticamente para una persona que inicia sesión con éxito utilizando el proveedor de identidad externo, según el dominio de la dirección de correo electrónico con la que el usuario está iniciando sesión. Esto facilita la gestión de usuarios para las empresas y la integración en un entorno de inicio de sesión único (SSO).

Cuando está configurado el inicio de sesión por OIDC, aparecerá un botón en la página de inicio de sesión que permite al usuario iniciar un sesión a través del proveedor externo. Es importante destacar que si una cuenta de CloudOps está configurada para usar la autenticación de dos factores, se le pedirá al usuario su token 2FA después de un inicio de sesión OIDC exitoso.

### Cómo configurar un proveedor OpenID Connect externo

La integración de CloudOps con un proveedor de OpenID Connect es un proceso de tres pasos, que se describen en las siguientes secciones:
    - Configurar el proveedor de identidad
    - Configurar CloudOps
    - Enviar un **URL de devolución de llamada** (un **URL de callback**) al proveedor

Un usuario con el rol de **Revendedor**, o cualquier otro rol que tenga el permiso *Autenticación: Gestionar*, puede agregar un proveedor de identidad OpenID Connect.

Navega a *Administración* -> *Autenticación* para llegar a la página *Autenticación*, donde se enumeran todos los proveedores de identidad configurados.

#### Configurar un proveedor de identidad

El primer paso al integrarse con un proveedor de identidad es configurar un cliente para CloudOps dentro de tu proveedor de identidad OpenID Connect. Sigue el procedimiento de tu proveedor de identidad para configurar un cliente y obten las credenciales de cliente requeridas por CloudOps:
    - El URL del emisor
    - La identificación del cliente
    - El secreto del cliente

#### Configurar CloudOps

1. Haz clic en *Agregar un proveedor de identidad*. Aparecerá la página *Agregar un proveedor de identidad*.
![Página del proveedor de identidad](/assets/oidc-add-1-en.png)
1. *OpenID Connect (OIDC)* es actualmente la única opción para **Tipo**.
1. Elige un proveedor del menú emergente etiquetado **Proveedor**. Cualquier proveedor de identidad que ya se haya configurado aparecerá en gris en el menú.
![Seleccionar el proveedor de identidad](/assets/oidc-add-2-en.png)
1. Aparecerán los campos para la información requerida para conectarse al proveedor de identidad.
![Detalles del proveedor de identidad](/assets/oidc-add-3-en.png)
1. Ingrese los detalles requeridos que obtuviste del proveedor de identidad.
1. Opcionalmente, si tienes varios proveedores de identidad externos configurados, puedes controlar el orden en el que aparecen en la página de inicio de sesión asignándoles un **orden de visualización**. Los proveedores aparecen ordenados en orden ascendente según sus valores de orden de visualización. Las entradas sin un orden de visualización establecido se enumerarán al final, en orden alfabético.
1. Haz clic en *Aplicar*.
1. Aparece la página *Autenticación* y se enumera el nuevo proveedor. Además, la página de inicio de sesión de CloudOps ahora presenta a los usuarios un botón para iniciar sesión con el proveedor de identidad.

#### Enviar el URL de devolución de llamada al proveedor

Para completar la integración con el proveedor de identidad, CloudOps generará un URL de devolución de llamada para pasarlo al proveedor:

1. Desde la página *Autenticación*, selecciona el menú *Acción* a la derecha de su proveedor de identidad configurado. Selecciona *Copiar URL de devolución de llamada*.
1. En la configuración de tu proveedor de identidad, navega hasta el cliente e ingrese el URL de devolución de llamada a la lista de URL de redireccionamiento autorizadas.
1. CloudOps ahora se autenticará correctamente a través de tu proveedor de identidad.

### Creación automática de cuentas

Si lo deseas, CloudOps puede crear automáticamente una cuenta para una persona que inicia sesión con credenciales válidas del proveedor de identidad externo, pero que aún no tenga una cuenta en CloudOps.

Esta configuración se aplica a nivel de la organización, lo que permite a una organización optar por no participar en esta función. La organización debe tener al menos un [dominio personalizado](https://cloudops.github.io/cloudmc-docs/#/reseller/custom-domains) configurado. CloudOps emparejará el nombre de dominio de la dirección de correo electrónico utilizada para iniciar sesión con el dominio personalizado seleccionado para determinar la organización en la que crear la cuenta de usuario final.

1. Haz clic en *Organizaciones* en la barra lateral.
1. Busca la organización deseada y haz clic en el menú de tres puntos *Acción* en el extremo derecho de la entrada.
1. Selecciona *Gestionar la seguridad*.
1. Aparecerá la pantalla *Política de autenticación nativa*. Haz clic en el elemento etiquetado *OIDC*, luego haz clic en el botón *Editar* en la parte superior derecha de la página.
1. Marca la casilla titulada **Permitir la creación automática de cuentas de usuario final al iniciar sesión correctamente con OIDC**. Aparecerán dos secciones, **Dominios asociados** y **Rol principal**.
1. Selecciona uno o más dominios para habilitar la creación automática de cuentas.
1. Selecciona el rol que se asignará a las cuentas creadas automáticamente.
- Solo se enumerarán los roles en tu nivel de privilegio y por debajo. Esto es para evitar una escalada de privilegios no deseada.
1. Haz clic en *Aplicar* para guardar la configuración. La creación automática de cuentas de usuario final ahora está habilitada.
