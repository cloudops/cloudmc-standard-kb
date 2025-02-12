---
title: "Activar la autenticación de dos factores"
slug: activar-autenticacion-dos-factores
---


Según Wikipedia, la **autenticación de dos factores** (también conocida como **2FA**) proporciona una identificación inequívoca de los usuarios mediante la combinación de dos componentes diferentes. Estos componentes pueden ser algo que el usuario conoce, algo que el usuario posee o algo que es inseparable del usuario.

En el contexto de CloudOps, esto se logra aprovechando el teléfono inteligente o la computadora portátil del usuario como un token. Combinado con un nombre de usuario y contraseña, eso nos da una autenticación de dos factores.

### Instalar un generador de tókenes

En tu teléfono inteligente, debes instalar un generador de tókenes para que el proceso funcione. CloudOps funciona bien con la aplicación Google Authenticator o Authy. Ambos están disponibles de forma gratuita para Android o iPhone. Si no posees un teléfono inteligente, este software tiene una versión para computadoras de escritorio.

Consulta la documentación específica de la aplicación sobre cómo instalarla en su dispositivo.

### Activar la autenticación de dos factores

Esto se hace accediendo a tu propia página de preferencias de usuario. Haga clic en tu nombre de usuario en la parte superior derecha de la aplicación y luego en *Mi perfil*.

Mira hacia la parte inferior de la página, verás una sección sobre Autenticación de dos factores. El flujo de trabajo es muy sencillo. Primero, haga clic en el botón **Habilitar** como se muestra a continuación.

![Habilitar 2FA](/assets/2FA-en-1.jpeg)

El sistema solicitará una validación de contraseña para confirmar la identidad del usuario. Luego, simplemente sigue las instrucciones en pantalla.

![Código QR](/assets/2FA-en-2.jpeg)

Asegúrate de ingresar tu código de 6 dígitos de tu generador de tókenes para confirmar que el proceso funcionó. Luego haz clic en **Verificar y guardar**. Esto abrirá una nueva ventana que te mostrará 8 códigos de respaldo. Estos códigos de respaldo son tu red de seguridad en caso de que pierdas o cambias tu teléfono. Por lo tanto, no se te bloqueará y podrás volver a configurar la autenticación. ***ASEGÚRATE DE GUARDAR ESTOS CÓDIGOS EN UN LUGAR SEGURO***.

![Códigos de respaldo](/assets/2FA-en-3.jpeg)

Una vez que hayas hecho clic en **Cerrar**, obtendrás tu token cada vez que vuelvas a autenticarte en la plataforma.

### Regenera tus códigos de seguridad

Si por alguna razón pierdes tus códigos de seguridad, tus códigos se pueden volver a generar. Esto también se hace a través de la página de preferencias del usuario. Haz clic en el botón *Regenerar códigos de seguridad* en la sección **Seguridad**. Aparecerá un cuadro de diálogo con tus nuevos códigos para que puedas tomar nota o imprimirlos.

### Desactivar la autenticación de dos factores

Si deseas desactivar la autenticación de dos factores en tu cuenta, ve a *Mi perfil* y en la sección **Seguridad**, haz clic en *Desactivar la autenticación de dos factores*. Te pedirá que ingreses tu contraseña. Una vez hecho esto, solo te pedirá tu nombre de usuario y contraseña cuando te autentiques en CloudOps.
