---
title: "Working with VPCs"
slug: working-with-vpcs
---

- [Create a new VPC](#create-a-new-vpc)
- [Create a new network tier](#create-a-new-network-tier)
- [Site-to-Site VPN](#site-to-site-vpn)
    + [Considerations:](#considerations-)

For basic information about VPCs, refer to this [article](../basic-concepts/what-is-a-vpc.md).

### Create a new VPC

**Note:** For this operation to be available, your user account needs to be assigned the **Environment Admin** role on the target environment.

1. Select **Services** from the left sidebar.
1. Select the appropriate compute environment.
1. Select the **Networking** tab.
1. Click on **Configure Networking**, and from the dropdown choose **Add VPC**.
1. Fill the Add VPC form:
   1. **Name:** Name of the VPC (ex: prod-vpc1)
   1. **Description:** (Optional) Description of the VPC (ex: Production network site A)
   1. **Zone:** cloud.ca zone name where to deploy the VPC
   1. **Network Domain:** (Optional) Domain Name.
1. Click on **Done**

### Create a new network tier

1. Select **Services** from the left sidebar.
1. Select the appropriate compute environment.
1. Select the **Networking** tab.
1. From the target VPC, find the Network item and click the gear menu.
1. In the top right corner, select **Add network**.
1. Fill the Add network form:
   1. **Name:** Name of the Tier (ex: net-web1)
   1. **Description:** (Optional) Description of the Tier (ex: Production Webservers)
   1. **Select a Network offering:**  Choose the Service Level of this Tier
      - **Standard Tier:**  Regular network supporting NAT, PortForwarding. Suitable for internal application such as Database server.
      - **Load Balanced Tier:**  (Default) Same as Standard Tier but also offers the capacity to load-balance traffic across multiple instances within that tier, via load-balancing rules applied on a public IP Address. **Only a single tier within a VPC can have this offering.**
   1. **ACL:** Access Control List for communication across Tiers within the same VPC.
      - **default_allow:**  Allow all type of traffic from/to other tiers in the VPC.
      - **default_deny:**  Deny all type of traffic from/to other tiers in the VPC.
1. Click on **Submit**.

### Site-to-Site VPN

Site-to-site VPN offers capability to interconnect:

- Multiple VPCs
- Office to VPC
- Other Cloud provider to VPC

1. Select **Services** from the left sidebar.
1. Select the appropriate compute environment.
1. Select the **Networking** tab.
1. From the target VPC, find the Site-to-Site VPN item and click the gear menu.
1. In the top right corner, select **Add site-to-site VPN**.
1. Fill in the Add site-to-site VPN form:
   1. **Name:** Name of the VPN connection, likely what this connection is to.
   1. **Remote Public IP:** The IP for the VPN to connect to. For another cloud.ca VPC, this is its source NAT. This can be found from the VPC item under the Networking tab.
   1. **Remote CIDR List:** A comma-separated list of CIDRs that can be accessed through this connection. If connecting to another cloud.ca VPC, this is the VPC's CIDR.
   1. **IPSec pre-shared key:** A key used by both ends of the VPN to connect. There is no complexity minimum for this, but it is suggested to provide a more secure key.
   1. **IKE encryption algorithm:** The encryption algorithm for the VPN connection for phase 1 negotiations. Authentication uses the pre-shared key.
   1. **IKE hash algorithm:**  The hash algorithm for the VPN connection.
   1. **IKE Diffie-Hellman group:** The Diffie-Hellman group for the VPN connection.
   1. **IKE lifetime:** The lifetime of the VPN. The default value is one day.
   1. **ESP encryption algorithm:** The encryption algorithm for the encapsulating security protocol.
   1. **ESP hash algorithm:** The hash algorithm for the encapsulating security protocol for phase 2 negotiations.
   1. **ESP perfect forward secrecy:** The Diffie-Hellman group for the encapsulating security protocol.
   1. **ESP lifetime:** The lifetime for the encapsulating security protocol. The default value is one hour.
   1. **Dead Peer Detection:** Whether or not to see if the other end of the VPN is alive, and if it isn't to reconnect.
   1. **Force encapsulation for NAT traversal:** Force NAT traversal for the VPN connection (UDP encapsulation).
   1. **Passive connection:** Check this box if the remote end has not yet been configured. Only one passive end should exist per site-to-site VPN.
1. Click on **Submit**.
1. If necessary, set up the other end of the VPN with the same pre-shared key as this one.

### Remote Access VPN

A remote access VPN allows you network access to resources within a VPC. You can see how to configure a remote access VPN for your OS [in this article](../vpn/cca-using-remote-access.md).
