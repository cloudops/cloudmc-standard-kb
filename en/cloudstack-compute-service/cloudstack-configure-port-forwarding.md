---
title:  "CloudStack: Configure Port Forwarding"
slug:  cloudstack-configure-port-forwarding
---

Port forwarding provide inbound connectivity from the Internet to a specific Instance Port or Protocol. It is configured through a VPC's public IP address dedicated to the purpose of port forwarding.

Note: you cannot configure port forwarding rules on a public IP address already being used for **Source NAT**, **VPN** or **Load Balancing**.

In the following example, we will enable port forwarding for HTTP (TCP port 80) to instance *acme-web-01* to the private IP on port 8080.  This instance is running a Web server that is listening on port 8080.

1. Click on **Services** in the sidebar.
1. Select the desired compute environment.
1. Select the **Networking** tab.
1. From the target VPC's list item, click the **Public access** button.
1. Click on *Acquire IP address*.
![Acquire IP address](/assets/config-port-fwd-1-en.png)
1. You will be prompted to confirm the acquisition of a new IP address.  Click *Confirm*.  The new IP address will be allocated and listed under **Public IPs**.
1. Click on the entry for the new IP address:
![Address acquired](/assets/config-port-fwd-2-en.png)
1. The **Port forwarding rules** screen will appear.  Click on *Add port forwarding rule*:
![Port forwarding rules](/assets/config-port-fwd-3-en.png)
1. Select the target instance *acme-web-01*, and its corresponding private IP address from the pop-up list, and select **TCP** as the protocol.
1. Enter **80** into the **Public port start** field, and enter **8080** into the **Private port start** field.  Because we are entering only a single port and not a range of ports, we may leave the port end fields blank.
![Add port forwarding rule](/assets/config-port-fwd-4-en.png)
1. Click on *Submit*. The **Port forwarding rules** screen will appear, and the new rule will be listed:
![Port forwarding rule added](/assets/config-port-fwd-5-en.png)
1. Validate that the port forwarding rule is working by connecting to the instance on via the public IP on port 80:
![Validate with HTTP](/assets/config-port-fwd-6.png)
