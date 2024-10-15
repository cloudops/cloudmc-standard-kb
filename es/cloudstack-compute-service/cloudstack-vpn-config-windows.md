---
title: "Configurar el cliente: Windows"
slug: configurar-el-cliente-windows
---

Las siguientes instrucciones se aplican a Microsoft Windows 10 usando su cliente VPN nativo:

#### Agregar el certificado a la lista de certificados de confianza

1. Ejecuta `mmc.exe`
1. Ve a *Archivos > Agregar/Eliminar complemento…*
1. Selecciona *Certificados* de la lista de la izquierda y haz clic en *Agregar >*.
1. En la ventana emergente, selecciona **Cuenta de computadora**.

![Complemento de certificados](/assets/Win-1-Computer-Account.png)

5. En la siguiente ventana, selecciona **Computadora local: (la computadora en la que se ejecuta esta consola)** y haz clic en *Finalizar*.
5. De vuelta en la ventana de la consola, selecciona "*Raíz de consola > Certificados (equipo local) > Autoridades de certificación raíz de confianza > Certificados*.
5. Haz clic derecho en *Certificados* y haz clic en *Todas las tareas > Importar…*.

![Menú de todas las tareas, opción de importación](/assets/Win-2-Import.png)

8. En la siguiente ventana, haz clic en *Siguiente*.
8. Haz clic en *Examinar...* y selecciona el archivo de certificado que guardaste en el disco con la extensión **.crt** (el certificado se proporciona en la interfaz de usuario de CloudMC, en la página para configurar la VPN de administración remota) y haz clic en *Próximo*.

![Asistente de importación de certificados](/assets/Win-3-Browse.png)

10. Guarda **Coloque todos los certificados en el siguiente almacén: Autoridades de certificación raíz de confianza** y haz clic en *Siguiente*.
10. Haz clic en *Finalizar*. Deberías ver el mensaje *La importación fue exitosa*. Puedes cerrar la ventana emergente y la Consola.
10. Si tu servidor está detrás de un NAT, sigue este procedimiento: [Enlace de Microsoft](https://support.microsoft.com/en-us/help/926179/how-to-configure-an-l2tp-ipsec-server-behind-a-nat-t-device-in-windows-vista-and-in-windows-server-2008)


#### Crear conexión VPN de red
![Ajustes](/assets/Win-4-Settings.png)

![Configuración VPN](/assets/Win-5-VPN.png)

![Agregar conexión](/assets/Win-6-Add-Connection.png)

![Detalles de la conexión](/assets/Win-7-Connection-Details.png)

![Seleccionar la conexión](/assets/Win-8-Select-Connection.png)


#### Iniciar conexión VPN
![Conectar](/assets/Win-9-Connect.png)

![Conectado](/assets/Win-10-Connected.png)
