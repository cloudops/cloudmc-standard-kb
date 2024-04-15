---
title: "Configurar el cliente: macOS"
slug: configurar-el-cliente-macos
---

Este sistema operativo proporciona un cliente VPN IKEv2 nativo. Estos son los pasos para configurar una conexión VPN:

#### Instalar el certificado

1. Haz doble clic en el certificado que descargaste y guardaste en tu computadora (por ejemplo: **acme-vpn.crt**) y agrégalo a tu llavero de **inicio de sesión**.
1. Abre la aplicación *Acceso a Llaveros*: *Finder > Aplicaciones > Utilidades > Acceso a Llaveros*.
1. Haz clic en **Inicio de sesión** en el lado izquierdo, luego en *Certificados* en la parte superior derecha.
1. En el cuadro de búsqueda en la parte superior derecha de la ventana Acceso a Llaveros, busca el certificado que acabas de agregar.
    ![Acceso a llavero](/assets/Mac-2-Keychain.png)
1. Haz doble clic en el certificado y, en el primer cuadro desplegable que dice *Seguridad IP (IPsec)*, selecciona **Confiar siempre**. Ahora puedes cerrar la ventana.  Es posible que se te solicita que ingreses tu contraseña para guardar el cambio en tu llavero.
    ![Confiar siempre en este certificado](/assets/Mac-3-Always-Trust.png)


#### Crear la conexión VPN

1. Abre *Configuración del Sistema* > *Red*.
    ![Add VPN](/assets/Mac-4-Add-VPN.png)
1. Haz clic en el menú emergente **...**, luego en **Agregar configuración de VPN** > **IKEv2**:
    - **Nombre mostrado:** Ingresa un nombre para tu conexión VPN (por ejemplo, **acme-vpn**)
    - **Dirección del servidor:** Ingresa la dirección IP pública desde la página *VPN de acceso remoto*
    - **ID remoto:** Igual que el servidor
    - **ID local:** Deja esto en blanco
    - **Autenticación de usuario:** Selecciona *Nombre de usuario*
    - **Nombre de usuario:** Ingresa el nombre de usuario del usuario de VPN creado para ti por tu administrador
    - **Contraseña:** Ingresa la contraseña especificada para el usuario de VPN
   ![VPN configuration](/assets/Mac-5-Configuration.png)
1. Haz clic en *Crear*.
1. La nueva VPN ahora aparece en la página *VPN*. Haz clic en el conmutador para conectar la VPN.
   ![VPN List](/assets/Mac-6-VPN-List.png)

Opcionalmente, puedes habilitar el módulo VPN en la barra de menú para acceder más fácilmente:
1. Abre *Configuración del Sistema* > *Centro de control*.
1. Desplázate hasta el módulo *VPN*.
1. Elige la opción *Mostrar en la barra de menús*.
   ![Show in Menu Bar](/assets/Mac-7-Show-In-Menu-Bar.png)
1. Ahora puedes conectarte a la VPN desde la barra de menú.
   ![Connect from Menu Bar](/assets/Mac-8-Connect-From-Menu-Bar.png)