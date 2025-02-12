---
title: "Connect to a VPC using remote access VPN (IKEv2)"
slug: connect-to-a-remote-management-vpn-ikev2
---

CloudOps provides the ability to connect securely from your home or office to your VPC. Using an IKEv2-over-IPSec based VPN client on your preferred platform (e.g.: Windows, macOS, Ubuntu...), you will be able to access your instances without having to go through port forwarding on public IP addresses.

## VPC Configuration
**Note:** To perform the following operations, your user account needs to be assigned either the **Editor** or **Owner** role on the target environment.

#### Enable VPN access
Before you can connect to your VPC through a client VPN connection, you need to enable VPN access on the VPC.

1. Navigate to the target CloudStack environment.
1. Select the *Networking* tab.
1. Locate the target VPC.  This is the VPC that you wish to connect to via the VPN.
1. Click the *Remote Access VPN* gear icon for the target VPC.  The *Remote access VPN* page appears.
1. Click on the Hidden Actions menu and select *Enable* to activate VPN access.
1. Click on the *Submit* button when it appears.
1. After a few moments, a certificate being displayed on the page.
1. Copy and paste this certificate into a new empty file with the **.crt** extension, for example `hypertec-cloud-vpn.crt`. Make sure you keep the exact same formatting and content as displayed on the page.

#### Create VPN account
1. In the VPN page of a VPC, the list of VPN users is also displayed below the certificate.
1. Click on *Add VPN User*.
1. Fill the *Add VPN User* form.
1. Click on *Done*.
1. Repeat previous steps for each desired VPN user.


## Connection to VPN
After you've successfully configured your VPC for VPN access, and created at least one VPN user, you are now ready to connect to this VPN to access your instances and applications. When connected to a VPC via VPN, the clients have access to all its tiers (up to 4 subnets).

The following information is required to configure the VPN client:

   - **Public IP:** The VPC's public IP address with tagged with the "VPN" purpose.
   - **IKEv2 certificate:** The certificate used to authenticate the remote VPN. This is the SSL certificate that you saved when enabling VPN access.
   - **Username:** a valid VPN account username.
   - **Password:** a valid VPN account password.
