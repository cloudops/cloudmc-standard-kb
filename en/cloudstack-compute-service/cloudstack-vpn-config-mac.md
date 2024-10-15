---
title: "Client Configuration: macOS"
slug: cca-client-config-mac
---

This operating system provides a native IKEv2 VPN client. Here are the steps to set up a VPN connection:

#### Install the certificate

1. Double click on the certificate you downloaded and saved on your computer (for ex: **acme-vpn.crt**) to add it to your **login** keychain.
1. Open the *Keychain Access* application: *Finder > Applications > Utilities > Keychain Access*.
1. Click **login** on the left side, then on *Certificates* on the bottom left.
1. In the search box at the top right of the Keychain Access window, search for the certificate you just added.
   ![Keychain Access](/assets/Mac-2-Keychain.png)
1. Double click on the certificate, and in the first dropdown box that reads *IP Security (IPsec)*, select **Always Trust**. You can now close the window.  You may be prompted to enter your password to save change to your keychain.
   ![Always trust this certificate](/assets/Mac-3-Always-Trust.png)


#### Create the VPN connection

1. Open *System Settings* > *Network*.
   ![Add VPN](/assets/Mac-4-Add-VPN.png)
1. Click on the **...** popup menu, then on **Add VPN Configuration** > **IKEv2**:
   - **Display name:** Enter a name for your VPN connection (e.g., **acme-vpn**)
   - **Server:** Enter the public IP address from the *Remote Access VPN* page
   - **Remote ID:** Same as server
   - **Local ID:** Leave this blank
   - **User authentication:** Select *Username*
   - **Username:** Enter the username for the VPN user created for you by your administrator
   - **Password:** Enter the password specified for the VPN user
   ![VPN configuration](/assets/Mac-5-Configuration.png)
1. Click *Create*.
1. The new VPN is now listed on the *VPN* page.  Click the toggle switch to connect the VPN.
   ![VPN List](/assets/Mac-6-VPN-List.png)

Optionally, you may enable the VPN module in the menu bar to access it more easily:
1. Open *System Settings* > *Control Center*.
1. Scroll to the *VPN* module.
1. Choose the *Show in Menu Bar* option.
   ![Show in Menu Bar](/assets/Mac-7-Show-In-Menu-Bar.png)
1. You can now connect to the VPN from the menu bar.
   ![Connect from Menu Bar](/assets/Mac-8-Connect-From-Menu-Bar.png)