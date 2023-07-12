---
title: "CloudStack: What is a VPC?"
slug: cloudstack-what-is-a-vpc
---


A Virtual Private Cloud (VPC) is a logically isolated section in an environment, where you can build a multi-tier application architecture.

Typically, in most of the public clouds on the market, you deploy your instances on what we like to call a *basic network*. In other words, your instance and other tenants' instances are all connected on the same huge network.

![Basic network](/assets/what-is-a-vpc-1.png)

Network access control is then accomplished by security groups or ACLs at the hypervisor level. We acknowledge that this model is way simpler to deploy for service providers and customers, too, but security and tenant isolation is a big issue.

In the VPC model, there might be a little more complexity related to management. However, you gain much more control and isolation. For this reason, we selected this model over more traditional methods.

![VPC network model](/assets/what-is-a-vpc-2.png)

A VPC is comprised of the following network components:

- **VPC:** A VPC acts as a container for multiple isolated networks that can communicate with each other via a virtual router.
- **Network Tiers:** Each tier acts as an isolated network with its own VLANs and CIDR list, where you can place groups of resources, such as VMs. Tiers are segmented by means of VLANs. The NIC of each tier acts as its gateway.
- **Virtual Router:** A virtual router is automatically created and started when you create a VPC. The virtual router connects the tiers and directs traffic among the public gateway, VPN gateways, and NAT instances. For each tier, a corresponding NIC and IP exists in the virtual router. The virtual router provides DNS and DHCP services through its IP.
- **Public Gateway:** Traffic to and from the Internet is routed to the VPC through a public gateway. In a VPC, the public gateway is not exposed to the end user; therefore, static routes are not supported for the public gateway.
- **Private Gateway:** All traffic to and from a private network is routed to the VPC through the private gateway.
- **VPN Gateway:** The VPC side of a VPN connection.
- **Site-to-Site VPN Connection:** A hardware-based VPN connection between your VPC and the datacenter, home network, or co-location facility.
- **Customer Gateway:** The customer side of a VPN Connection.
- **NAT Instance:** An instance that provides Port-Address Translation for instances to access the Internet via the public gateway.
- **Network ACL:** Ordered rules that determine whether traffic is allowed in or out of any tier associated with the network ACL

### Network architecture in a VPC
In a VPC, the following network architectures are the basic options:

- VPC with a public gateway only
- VPC with public and private gateways
- VPC with public and private gateways and site-to-site VPN access
- VPC with a private gateway only and site-to-site VPN access

### Connectivity options for a VPC
You can connect your VPC to:

- The Internet through the public gateway
- A corporate datacenter by using a site-to-site VPN connection through a VPN gateway
- Both the Internet and your corporate datacenter, using both the public gateway and a VPN gateway

### VPC network considerations
Consider the following when you create a VPC:

- The maximum number of tiers you can create within a VPC is 4.
- Each tier must have an unique CIDR in the VPC. The Web interface enforces this requirement.
- A tier belongs to only one VPC.
- When a VPC is created, by default, a Source NAT IP is allocated to it. The Source NAT IP is released only when the VPC is removed.
- A public IP can be used for only one purpose at a time. If the IP is a Source NAT, it cannot be used for Static NAT or port forwarding.
- **Static NAT** is a one-to-one mapping between a public IP and an instance in a VPC.  All traffic sent to the public IP will be sent to the designated instance, and all traffic from the instance will be sent out from the public IP.  Use static NAT when you need to have ingress traffic always go to the same instance, or when you need all traffic from an instance to egress from the same public IP.
- **Port forwarding** is a mapping of a port on a public IP address to a port on a private IP in a VPC.  Different ports on the public IP can be forwarded to ports on separate instances, as long as the instances are in the same VPC.  All traffic from the instances will use the source NAT IP address of the VPC for egress traffic.  Use port forwarding when all you need is for ingress traffic on specific ports to be forwarded to an instance.  This allows for efficient use of IP address space.
- Instances can only have one private IP address, hence be connected to only one tier at the time.
- The public load-balancing service can be supported by only one tier inside the VPC.
- If an IP address is assigned to a tier:
   - That IP can’t be used by more than one tier at a time in the VPC. For example, if you have tiers A and B, and a public IP, you can create a port-forwarding rule by using the IP either for A or B, but not for both.
   - That IP can’t be used for Static NAT, load balancing, or port forwarding rules for another guest network inside the VPC.
