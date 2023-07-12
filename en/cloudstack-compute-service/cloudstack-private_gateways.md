---
title: "CloudStack: Private gateways"
slug: cloudstack-private-gateways
---


This article introduces the concept of a private gateway, and includes details on managing their ACLs and static routes.

## Detailed overview

Instances in separate VPCs are isolated from each other. Often, setting up a [site-to-site VPN](create-site-to-site-vpn-on-vpc.md) is a convenient way to establish a connection between two VPCs, allow their instances to communicate with each other. There are limitations with this approach, however. A VPN encrypts the network traffic, which can reduce performance. Also, VPN connections may unexpectedly terminate and need to be reset, affecting availability and performance.

To address these issues, service providers can offer dedicated private networking infrastructure to allow two VPCs to be peered. Network traffic between the VPCs traverses an internal path instead of the public network. This is useful when a reliable and fast connection is needed, such as for real-time applications or for monitoring and management. In such a scenario, CloudMC is able to take advantage of the internal path by creating a private gateway between the VPCs.

![Simplified illustration of two VPCs peered by a private gateway over an internal network connection](/assets/private-gateways-diagram-en.jpg)

The diagram above illustrates one possible topology, where two VPCs are peered and either side can talk to the other. A virtual router in VPC 1 connects to the private gateway via a dedicated network interface. The red boxes contain the IP address that could be assigned to each interface. The IP addresses are for illustration purposes only. A private gateway is set up in both VPCs, and is identified on each side by the IP address of the terminating interface on the virtual router. In this illustration, the private gateway in VPC 1 would be listed as 10.0.5.2, and the private gateway for VPC 2 would be 10.0.2.2. The diagram does not include details of the underlying physical network, and it also omits the networks within each VPC.

Because setting up a private gateway requires specific knowledge of how the physical network is configured, only a CloudMC account with reseller-level privilege can configure this feature. However, users and administrators have permission to see private gateways in their environments, and they can configure access and routing. The private gateway configuration on each side has its own set of static routes. These define, based on destination IP, the traffic that will be routed via the private gateway. Access control is established via the network ACLs you have defined, see [Securing your network](securing-your-network.md) for more information.

Private gateways can be seen by navigating to your desired environment, then **Networking** \> **Private gateways**.

![A screenshot of the VPC overview page, with numbered dots indicating the private gateway features](/assets/private-gateways-vpc-en.png)

1.  **List of private gateways**

    A list of all private gateways in this VPC, along with their status, appears in this section. Each gateway is identified by the IP address of the terminating interface \(the other end of the connection\).

2.  **Gear icon**

    Click on the gear icon to navigate to the **Private gateways** page for this VPC.


## Private gateways and ACLs

![Screenshot of the Private Gateways details paged, with numbered dots on the major features](/assets/private-gateways-list-en.png)

1.  **List of private gateways**

    In the main area of the workspace, a list of all private gateways in the selected VPC appears.

2.  **Search box**

    Type in the search box to filter the list of private gateways. The system will search through all fields in the private gateway, including name, gateway IP address, ACL names, and internal UUID strings, and returns any private gateway that matched the string in the search box.

3.  **Private gateway row**

    Each row includes the IP address and subnet mask of the virtual router interface connected to the private gateway, the IP address of the private gateway itself, its status, and the ACL currently applied.

    Click on a private gateway to see its details, including static routes.

4.  **Hidden Actions menu**

    Each entry in the private gateways list has a Hidden Actions menu. Click on the Hidden Actions menu to access the **Replace ACL** command.

    To apply a different ACL to a private gateway, click the **Replace ACL** command. A dialogue box will appear, where you may select one to apply from a list of network ACLs that have been defined for your VPC.


## Static routes

![A screenshot of the Static Routes page, with numbered dots on the major features](/assets/private-gateways-static-routes-en.png)

1.  **List of static routes**

    In the main area of the workspace, a list appears of all static routes that have been defined for the selected private gateway.

2.  **Search box**

    Type in the search box to filter the list of static routes. The system will search through the CIDR field and returns any static route that matched the string in the search box.

3.  **Add static route**

    Clicking this button will open a dialog box where you can add a new static route to the private gateway. Enter the CIDR of the destination network or host, and traffic to that destination will be routed through the private gateway.

4.  **Static route row**

    Each row includes the CIDR of the destination route, its status, and a Hidden Actions menu with the **Delete** command to remove this static route.


