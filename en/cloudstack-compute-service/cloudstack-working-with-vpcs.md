---
title: "CloudStack: Working with VPCs"
slug: cloudstack-working-with-vpcs
---


<!-- - [Create a new VPC](#create-a-new-vpc)
- [Create a new network tier](#create-a-new-network-tier)
- [Site-to-Site VPN](#site-to-site-vpn)
    + [Considerations:](#considerations-) -->

To create, modify, or delete a VPC, an account with the *User* role must be a member of the environment which contains the VPC, and also have the *Editor* or *Owner* environment role assigned.  An account with the *Administrator* role or higher may create, modify, or delete VPCs in an environment.

For more information about VPCs, please see [What is a VPC](../cloudstack-compute-service/what-is-a-vpc.md).

### Create a new VPC

1. Select **Services** from the left sidebar.
1. Select the appropriate compute environment.
1. Select the **Networking** tab.
1. Click on **Configure Networking**, and from the dropdown choose **Add VPC**.
![Networking tab](/assets/working-with-vpcs-1-en.png)
1. Fill the Add VPC form:
   - **Name:** Name of the VPC (ex: *acme-prod-vpc01*).
   - **Description:** (Optional) Description of the VPC (ex: "Production network site A").
   - **CIDR:** The IP range to use for the VPC.  The range must be a /22 network.
   - **Network Domain:** (Optional) Domain name for internal DNS resolution (ex: *internal.acme.com*).  CloudMC will add this domain name to the */etc/hosts* file for new instances.
   - **VPC offering:** Choose the Service Level of this VPC.
   ![Add VPC page](/assets/working-with-vpcs-2-en.png)
1. Click on **Submit**.
1. The **Networking** tab will appear, and your new VPC will be listed in the **starting** state.  When it has been created, the VPC will appear in the **enabled** state.
![Networking tab with VPC](/assets/working-with-vpcs-3-en.png)

### Create a new network tier

1. From the target VPC, find the *Networks* item and click the gear menu.
1. In the top right corner, click **Add network**.
![VPC details page](/assets/working-with-vpcs-4-en.png)
1. Fill the Add network form:
   - **Name:** Name of the Tier (ex: *acme-net-web1*)
   - **Description:** (Optional) Description of the tier (ex: "Production Web servers")
   - **Network offering:**  Choose the service level of this tier
      - **Standard Tier:**  A regular network supporting NAT and port forwarding. Suitable for internal applications such as a database server.
      - **Load Balanced Tier:**  (Default) Includes the features of the Standard Tier and also offers the ability to load-balance traffic across multiple instances within that tier, via rules that are applied on a public IP Address. **Note: Only a single tier within a VPC can have this offering.**
   - **Gateway:** The IP address of the default gateway for the network tier to be created.
   - **Netmask:**  The subnet mask of the network tier to be created.
   - **ACL:** Access control list (ACL) for communication across tiers within the same VPC.  See [Securing your network](securing-your-network.md) for more information about ACLs.
      - **default_allow:**  (Default) Allow all type of traffic from/to other tiers in the VPC.
      - **default_deny:**  Deny all type of traffic from/to other tiers in the VPC.
   ![Add network page](/assets/working-with-vpcs-5-en.png)
1. Click on **Submit**.
1. The *VPCs* page will appear.  The new network will appear in the list of networks in **allocated** state and is now ready for use.

### Site-to-Site VPN

Site-to-site VPNs offer the capability to interconnect multiple VPCs, a remote office to a VPC, or another cloud provider to a VPC.  An example site-to-site VPN can be found in the how-to article [Create a site-to-site VPN on a VPC](../cloudstack-compute-service/create-site-to-site-vpn-on-vpc.md).

1. From the target VPC, find the **Site-to-Site VPNs** item and click the gear menu.
   ![Site-to-site VPN page](/assets/working-with-vpcs-6-en.png)
1. In the top right corner, select **Add site-to-site VPN**.
1. Fill in the *Add site-to-site VPN* form:
   - **Name this VPN connection:** Name of the VPN connection, likely what this connection is to.
   - **Remote Public IP:** The IP for the VPN to connect to. For another VPC, this is its source NAT. This can be found from the VPC item under the **Networking** tab.
   - **Remote CIDR List:** A comma-separated list of CIDRs that can be accessed through this connection. If connecting to another VPC, this is the VPC's CIDR.
   - **IPSec pre-shared key:** A key used by both ends of the VPN to connect. There is no complexity minimum for this, but it is suggested to provide a more secure key.
   - **IKE encryption algorithm:** The encryption algorithm for the VPN connection for phase 1 negotiations. Authentication uses the pre-shared key.
   - **IKE hash algorithm:**  The hash algorithm for the VPN connection.
   - **IKE Diffie-Hellman group:** The Diffie-Hellman group for the VPN connection.
   - **IKE lifetime:** The lifetime of the VPN. The default value is one day.
   - **ESP encryption algorithm:** The encryption algorithm for the encapsulating security protocol.
   - **ESP hash algorithm:** The hash algorithm for the encapsulating security protocol for phase 2 negotiations.
   - **ESP perfect forward secrecy:** The Diffie-Hellman group for the encapsulating security protocol.
   - **ESP lifetime:** The lifetime for the encapsulating security protocol. The default value is one hour.
   - **Dead Peer Detection:**  Checks to see whether or not the other end of the VPN is alive.  If the other end does not respond, the VPN will attempt to reconnect.
   - **Force encapsulation for NAT traversal:** Force NAT traversal for the VPN connection (UDP encapsulation).
   - **Passive connection:** Check this box if the remote end has not yet been configured. Only one passive end should exist per site-to-site VPN.
1. Click on **Submit**.
1. The **Site-to-site VPNs** tab will appear, and the new VPN will be listed in the **disconnected** state.
   ![VPN created but not yet connected](/assets/working-with-vpcs-7-en.png)
1. If necessary, set up the other end of the VPN with the same pre-shared key as this one.
1. Once the other end of the VPN tunnel has been configured, the state will change to **connected**.

### Remote Access VPN

A remote access VPN allows you network access to resources within a VPC. For more information, see [Connect to a VPC using remote access VPN (IKEv2)](../vpn/cca-using-remote-access.md).
