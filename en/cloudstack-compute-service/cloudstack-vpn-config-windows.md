---
title: "Client Configuration: Windows"
slug: cca-client-config-windows
---

The following instructions apply to Microsoft Windows 10 using its native VPN client:

#### Add the certificate to the list of trusted certificates

1. Run `mmc.exe`
1. Go to *Files > Add/Remove Snap-in…*
1. Select *Certificates* from the list on the left and click *Add >*.
1. In the pop-up window, select **Computer account**.

![Certificates snap-in](/assets/Win-1-Computer-Account.png)

5. In the next window, select **Local Computer: (the computer this console is running on)** and click *Finish*.
5. Back in the console window, select "*Console Root > Certificates (Local Computer) > Trusted Root Certification Authorities > Certificates*.
5. Right click on *Certificates* and click *All Tasks > Import…*.

![All tasks menu, import option](/assets/Win-2-Import.png)

8. In the next window, click *Next*.
8. Click on *Browse…* and select the certificate file that you saved on disk with the **.crt** extension (the certificate is provided in the CloudMC UI, in the page to configure the remote management VPN) and click on *Next*.

![Certificate import wizard](/assets/Win-3-Browse.png)

10. Keep **Place all certificates in the following store: Trusted Root Certification Authorities**  and click *Next*.
10. Click on *Finish*. You should see the message *The import was successful*. You can close the pop-up and the Console.
10. If your server is behind a NAT, follow this procedure: [Microsoft link](https://support.microsoft.com/en-us/help/926179/how-to-configure-an-l2tp-ipsec-server-behind-a-nat-t-device-in-windows-vista-and-in-windows-server-2008)


#### Create network VPN connection
![Settings](/assets/Win-4-Settings.png)

![VPN Configuration](/assets/Win-5-VPN.png)

![Add Connection](/assets/Win-6-Add-Connection.png)

![Connection Details](/assets/Win-7-Connection-Details.png)

![Select Connection](/assets/Win-8-Select-Connection.png)


#### Initiate VPN connection
![Connect](/assets/Win-9-Connect.png)

![Connected](/assets/Win-10-Connected.png)
