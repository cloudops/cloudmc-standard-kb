---
title: "Client Configuration: Ubuntu 18.04"
slug: cca-client-config-ubuntu
---

This guide will help you configure the remote management VPN on Ubuntu using the network manager, which is installed by default on the Desktop version.

1. Install the necessary packages:
   - `sudo apt-get install strongswan network-manager-strongswan libcharon-extra-plugins`
1. Open the application *Settings*, navigate to the *Network* tab on the left.
1. Click on the **+** next to *VPN*.
1. Select **IPsec/IKEv2 (strongswan)** as the VPN type.

![VPN selection dialogue](/assets/Lx-1-Strongswan.png)

5. Go to the *Identity* tab.
5. Give the VPN a name, for example: **hypertec-cloud-vpn**
5. Under *Gateway*, the *Address* field is the public IP displayed in the VPN configuration page, and *Certificate* is the certificate file displayed in the VPN configuration page.
5. In *Client*, set *Authentication* to *EAP*.
5. Fill in the *Username* and *Password* fields.
5. Under *Options*, check the **Request an inner IP address** checkbox.

![VPN configuration page](/assets/Lx-2-Request-internal.png)

11. Optionally, you can go to the *IPv4* tab, and check **Use this connection only for resources on its network**.
11. Click on *Add* at the top right of the window to save the configuration.


You can now enable the VPN from the *Network* page or from the network widget at the top right of the screen.
