---
title: "VMware: Networking"
slug: vmware-networking
---


Networking is a critical part of any cloud infrastructure. This article introduces the basic concepts of networking in VMware, and the corresponding features in the user interface.

All networking features are accessible via the **Networking** section of the selected VMware environment.

## Detailed overview

VMware provides a full set of virtual networking features. A basic, isolated network can be created with no other prerequisites. The network provides a DHCP server for automatically configuring devices that connect to the network, using an IP space that you define at creation time. You can also manually configure the interfaces connecting to the network, if desired. An isolated network will allow the creation of virtual machines that can communicate with each other, but they will have no connectivity to any other network. To be able to connect to other networks or to the public Internet, an edge gateway must be configured in your environment.

The following different types of networks are supported:

-   **Isolated**

    The most basic networking mode, an isolated network provides connectivity between interfaces attached to it. Isolated networks provide no connectivity to the outside world. Only virtual machines within the same environment as a isolated network can connect to that network.

-   **Routed**

    This is also known as a NAT routed network. A routed network provides external connectivity along with NAT, firewall, and VPN services.


## Network status

VMware networks have the following states:

-   **Realized**

    The network has been created and is ready for use.

-   **Pending**

    The network configuration has been submitted and is waiting to begin realization.

-   **Configuring**

    The network configuration is currently being realized.

-   **Realization failed**

    The system was unable to realize the network configuration.

-   **Unknown**

    The current state of the network is not known.


