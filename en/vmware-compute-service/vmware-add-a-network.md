---
title: "VMware: Add a network"
slug: vmware-add-a-network
---

## About this task

This article will guide you through the process of adding a new network to a VMware environment. The CloudMC interface provides a single-page wizard for selecting and deploying a new network configuration.

## Before you begin

-   Your VMware environment must already exist
-   To create a routed network, you must have an edge gateway already configured

## Procedure

1.  Navigate to the desired environment. The **Virtual Machines** page appears.

2.  Click on the **Networking** tab.

3.  Click on the **Add Network** button. The **Add Network** wizard appears.

4.  Configure the new network:

    1.  Enter a name into the **Name** field, or accept the default.

    2.  *\(Optional\)* Enter a description into the **Description** field.

    3.  Enter an IP address in CIDR format for the gateway into the **Gateway CIDR** field.

        The system will interpret this entry for network number and subnet mask and use them to configure the network address and size. The IP address itself will be automatically assigned to the gateway that will be created for this network.

    4.  Select the desired type of network from the **Network Type** popup menu.

        To provide external connectivity to your network, choose **Routed**. You will be asked to specify an Edge gateway from the **Edge Gateways** popup menu. If no edge gateway is configured for this environment, the new network will be unable to connect to the public Internet.

        If you do not need external connectivity for your network, choose **Isolated**. This is useful for networks that have privileged or sensitive information, or for compliance with access restrictions and other business rules.

    5.  Enter one or more IP addresses, or IP ranges, into the **Static IP Pools** field to reserve for static assignment.

        These addresses will not be offered by the new network's DHCP server. This is useful for manually assigning IP addresses to interfaces on the network. All of the addresses must be within the address space of the new network, as specified in the **Gateway CIDR** field.

        You may enter a single IP address or a single contiguous range \(specify the lowest and highest IP addresses in the range, separated by a hyphen\). To specify multiple individual IP addresses or ranges, use the **+** button to reveal additional input fields.

    6.  *\(Optional\)* To override the default primary \(and, if desired, secondary\) DNS servers that will be offered by the DHCP server, enter the IP addresses of your name servers into the **Primary DNS** and **Secondary DNS** fields.

5.  Click the **Submit** button.


## Results

-   The network with the specified configuration is realized in the active environment
-   The address space, network size, and gateway IP address are as specified in the **Gateway CIDR** field
-   The network is listed in the **Networking** tab



