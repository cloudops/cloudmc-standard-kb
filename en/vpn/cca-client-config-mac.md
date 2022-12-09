---
title: "Client Configuration: macOS"
slug: cca-client-config-mac
---

This operating system provides a native IKEv2 VPN client. Here are the steps to set up a VPN connection:

#### Install the certificate

1. Double click on the certificate you downloaded and saved on your computer (for ex: **cloudca-vpn.crt**) and add it to your **login** keychain.
   ![Add certificate](/assets/Mac-1-Add-Certificate.png)
1. Open the *Keychain Access* application: *Finder > Applications > Utilities > Keychain Access.app*
1. Click **login** on the left side, then on *Certificates* on the bottom left.
1. In the search box at the top right of the Keychain Access window, search for "Cloud.ca" to locate the **Cloud.ca VPN System CA** certificate.
   ![Keychain Access](/assets/Mac-2-Keychain.png)
1. Double click on the certificate, and in the first dropdown box that reads *IP Security (IPsec)*, select **Always Trust**. You can now close the window.
   ![Always trust this certificate](/assets/Mac-3-Always-Trust.png)


#### Create the VPN connection

1. Open *System Preferences -> Network*
1. Click on **+** button to add a VPN
   - **Interface:** VPN
   - **VPN Type:** IKEv2
   - **Service Name:** a name for your VPN connection (e.g.hHypertec-cloud-vpn)
   ![Add VPN](/assets/Mac-4-Add-VPN.png)
1. From the left, select the connection you just created and enter the following details.
   - **Server:** Public IP address
   - **Remote ID:** same as server
   - **Local ID:** leave this blank
   - Click on *Authentication Settings...*
       - **Username:** the VPN user username
       - **Password** the VPN user password
       ![Authenticate](/assets/Mac-5-Authentication.png)
1. Click *Apply*.
1. Check *Show VPN status in menubar* option to access it more easily.
1. You can now connect to the VPN from the menu bar.
