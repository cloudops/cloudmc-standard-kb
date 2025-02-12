---
title: "Activar la autenticación de dos factores"
slug: activar-2fa
---


Este artículo presenta el concepto de autenticación de dos factores y describe cómo habilitar y deshabilitar esta función para tu cuenta.

## Resumen detallado

La autenticación de dos factores, también conocida como autenticación de múltiples factores, 2FA o MFA, proporciona una identificación inequívoca de un usuario por medio de dos piezas de identificación separadas. El primer componente es algo que el usuario debe saber, como una contraseña o una frase de contraseña. El segundo componente es algo que el usuario debes tener, por ejemplo, un token de una sola vez. Este mecanismo ayuda a demostrarle al sistema que eres quien dices ser.

En general, se recomienda habilitar siempre 2FA para tu cuenta de CloudOps. Una vez que se configura 2FA, al iniciar sesión se te solicitará el token único:

![Captura de pantalla de la página de inicio de sesión de CloudOps que solicita un token único](/assets/enable-2fa-login-es.png)

Para generar un token único, deberás instalar una aplicación generadora de tokens, ya sea en tu teléfono inteligente o en tu estación de trabajo. Hay muchas aplicaciones que pueden funcionar con el sistema 2FA de CloudOps, como LastPass, 1Password, Google Authenticator, Microsoft Authenticator y otras. Consulta la documentación proporcionada por el proveedor de tu software para obtener información sobre la instalación y la configuración.

## Habilitación de la autenticación de dos factores

### Antes de que empieces

- Debes tener un generador de tokens instalado y configurado

### Procedimiento

1.  Haz clic en el **Menú de usuario** \> **Mi perfil** \> **Seguridad**. El menú de usuario se encuentra en la esquina superior derecha de la barra de menú de CloudOps.

2.  Desplácete hasta la parte inferior de la página y haz clic en el botón titulado **Habilitar autenticación de dos factores \(2FA\)**.

     ![Captura de pantalla de la página Seguridad, enfocada en el botón Habilitar autenticación de dos factores](/assets/enable-2fa-enablebutton-es.png)

3. Se te pedirá tu contraseña, ingrésala y luego haz clic en **Confirmar**.

4. Usa tu generador de tokens para escanear el código QR que aparece en la pantalla.

     Verifica que tu generador de tokens haya aceptado el código QR y esté generando un token único.

5. Ingresa el token único de tu generador de tokens en el campo de texto provisto.

     ![Captura de pantalla de la página de seguridad, enfocada en el código QR y la entrada del token](/assets/enable-2fa-qrcode-es.png)

6. Haz clic en **Habilitar**.

     Se mostrará una lista de códigos de respaldo. Guárdalos en un lugar seguro. En caso de que pierdas el acceso a tu generador de tokens, usa uno de estos códigos para iniciar sesión en el sistema y vuelvas a habilitar 2FA con un nuevo generador de tokens.

     ![Captura de pantalla de la página de Seguridad, enfocada en los códigos de respaldo](/assets/enable-2fa-codes-es.png)


### Resultados

- La autenticación de dos factores ahora está habilitada en tu cuenta de CloudOps
- En tu próximo inicio de sesión, después de verificar tu nombre de usuario y contraseña, el sistema te pedirá que ingreses el token único de tu generador de tokens

### Regenera tus códigos de respaldo

Si pierdes tus códigos de respaldo, tus códigos se pueden volver a generar.

#### Procedimiento

1. Haz clic en el **Menú de usuario** \> **Mi perfil** \> **Seguridad**. El menú de usuario se encuentra en la esquina superior derecha de la barra de menú de CloudOps.

2. Desplácete hasta la parte inferior de la página y haz clic en el botón titulado **Gestionar la autenticación de dos factores \(2FA\)**.

3. Se te pedirá tu contraseña, ingrésala y luego haz clic en **Confirmar**.

4. Haz clic en el botón titulado **Regenerar códigos de respaldo**.

     Se mostrará una lista de los nuevos códigos de respaldo. Guárdalos en un lugar seguro.


### Deshabilitar la autenticación de dos factores

#### Procedimiento

1. Haz clic en el **Menú de usuario** \> **Mi perfil** \> **Seguridad**. El menú de usuario se encuentra en la esquina superior derecha de la barra de menú de CloudOps.

2. Desplácete hasta la parte inferior de la página y haz clic en el botón titulado **Gestionar autenticación de dos factores \(2FA\)**.

3. Se te pedirá tu contraseña, ingrésala y luego haz clic en **Confirmar**.

4. Haz clic en el botón titulado **Deshabilitar autenticación de dos factores**.

     La autenticación de dos factores ahora está deshabilitada en tu cuenta. La próxima vez que inicies sesión, solo se te pedirá tu nombre de usuario y contraseña.


