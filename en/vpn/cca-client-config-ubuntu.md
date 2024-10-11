---
title: "Client Configuration: Ubuntu 24.04"
slug: cca-client-config-ubuntu
---

This guide will help you configure the remote management VPN on Ubuntu using the network manager, which is installed by default on the Desktop version.

1. Install the necessary packages:
   - `sudo apt-get install strongswan network-manager-strongswan libcharon-extra-plugins`
1. Open the application *Settings*, navigate to the *Network* tab on the left.
1. In the *VPN* section, click on the **+** button on the far right.
1. Select **IPsec/IKEv2 (strongswan)** as the VPN type.

![VPN selection dialogue](/assets/Lx-1-Strongswan.png)

5. Go to the *Identity* tab.
5. Give the VPN a name in the **Name** field, for example: **Hypertec VPN**
5. Under the *Server* section, the *Address* field is the public IP displayed in the VPN configuration page, and *Certificate* is the certificate file you created when [enabling the VPN](cca-using-remote-access.md).
5. Under the *Client* section, set *Authentication* to **EAP (Username/Password)**.
5. Enter the VPN username into the *Identity* and *Username* fields.
5. Under the *Options* section, check the **Request an inner IP address** checkbox.

![VPN configuration page](/assets/Lx-2-Request-internal.png)

11. Optionally, you can go to the *IPv4* tab, and check **Use this connection only for resources on its network**.
11. Click on *Add* at the top right of the window to save the configuration.


You can now enable the VPN from the *Network* page or from the network widget at the top right of the screen.
