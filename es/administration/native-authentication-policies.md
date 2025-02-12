---
title: "Políticas de autenticación nativas"
slug: politicas-de-autenticacion-nativas
---


## Resumen

Los revendedores pueden controlar cuales dominios se pueden usar para las cuentas de usuario nativas de CloudOps y también establecer ciertos requisitos mínimos para las contraseñas. Esta función se denomina "política de autenticación nativa" y cada organización puede configurar su propia política o utilizar la política predeterminada. Una sub-organización heredará la política de su matriz y no se puede anular.

Para administrar estas funciones para una organización específica, navega a **Administración** \> **Organizaciones**, haz clic en la organización de destino, luego navega a **Políticas de autenticación** \> **Nativa**.

![Captura de pantalla de la página Políticas de autenticación nativa](/assets/native-authentication-policy-en.png)

## Dominios denegados

Las cuentas nativas de CloudOps usan una dirección de correo electrónico como nombre de usuario. La función `Dominios denegados` permite a un revendedor especificar nombres de dominio que no están permitidos. Acepta una lista de nombres de dominio separados por comas. Se denegará el acceso a los usuarios que intenten establecer una contraseña o iniciar sesión con una dirección de correo electrónico con este nombre de dominio.

## Política de complejidad de contraseña

Los revendedores pueden definir una política de complejidad de contraseñas para una organización. La política se aplica solo a las contraseñas de las cuentas nativas de CloudOps creadas en esa organización. No afecta las cuentas administradas por LDAP u OIDC. Los requisitos mínimos para las contraseñas pueden incluir:

-   Longitud
- Caracteres en minúsculas o mayúsculas
- Números
- Caracteres especiales como los asteriscos, los signos et, y otros
