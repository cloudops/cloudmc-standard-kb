---
title: "CloudStack: Securing your network"
slug: cloudstack-securing-your-network
---

### Preventing Access to Your Instances

You may need to be able to access your instances, or allow access instances to be accessed by outside users. This page covers what you can do to allow access while still maintaining security.

### Remote Access VPN

A remote access VPN will allow you to access your instances without the need for connecting them to the outside world. If you don't require public access to your instances, this is suggested. [You can find how to set up a remote access VPN here.](../vpn/cca-using-remote-access.md)

### Network ACLs

You can configure an access control list (ACL) for your networks to allow external access to your instances, usually to display a website.

#### Create the ACL

1. Select **Services** from the left sidebar.
1. Select the appropriate compute environment.
1. Select the **Networking** tab.
1. From the target VPC, find the **Custom ACLs** item and click the gear menu.
1. In the top-right corner, select *Add network ACL*.
1. Fill in the name and description fields for your new ACL, and press *Submit*.
1. The VPC details page will appear, and the **Network ACLs** tab will be selected.  Your new ACL will appear in the list of ACLS.  Click on the new ACL.
1. In the top left corner, select *Add network ACL rule*.
1. Fill in the *Add network ACL rule* form:
   1. **Rule number:** The order of priority for the rule. Rules are evaluated in numerical order. If a *deny all ingress* rule is placed at position 1, no traffic will be allowed in. If it is placed last, all other rules will be evaluated before it is applied.
   1. **Description:** (Optional) A description of what the ACL rule is for.
   1. **Action:** Whether to allow or deny traffic for this rule.
   1. **Traffic type:** Whether this is for incoming or outgoing traffic.
   1. **CIDR:** The network CIDR that this rule applies to. For ingress, this applies to the source of the traffic. For egress, this applies to the destination traffic.
   1. **Protocol:** The protocol this network rule applies to.
   1. **Start port:** The starting port this ACL rule applies to.
   1. **End port:** The end port this ACL rule applies to.
1. Continue filling in network rules until the ACL is complete.
1. Select the **Networking** tab on the top of the page.
1. Select your network under the target VPC.
1. Select the *Action* menu for your network under the right side and choose *Replace ACL*.
1. Select your new ACL, and click *Submit*.
1. The network details page will appear, and the new ACL should be listed under **ACL**.
1. Select the **Networking** tab on the top of the page.
1. From the target VPC, find the **Public access** item and click the gear menu.
1. From the top right corner, select *Acquire IP address*.
1. A dialogue box will appear asking for confirmation.  Click *Submit*.  The **Public IPs** tab will appear.
1. Click on the new IP address, which will appear in the list titled **Public IPs**.
1. From the menu, select *Port forwarding rules*.
1. In the top right corner, select *Add port forwarding rule*.
1. Fill in the *Add port forwarding rule* form:
   1. **Public IP:** The public IP address that was allocated.  This field cannot be modified.
   1. **Instance:** Select the instance you want this public IP to port forward to.
   1. **Private IP:** The private IP of the instance to which this rule will forward traffic.
   1. **Protocol:** The protocol of the traffic to forward.
   1. **Public port start:** The lower port of a range of public ports for this port forwarding rule.
   1. **Public port end:** (Optional) The upper port of a range of public ports for this port forwarding rule. If you are only opening a single port, you can leave this empty.
   1. **Private port start:** The lower port of a range of private ports for this port forwarding rule.
   1. **Private port end:** (Optional) The upper port of a range of private ports for this port forwarding rule. If you are only opening a single port, you can leave this empty.
1. If needed, continue adding additional port forwarding rules for this public IP.

After this, traffic will be accessible over the allocated public IP, over the ports that you have forwarded to your instances, and traffic will only be allowed as you have specified in the ACL.

#### Example ACL List

The following list will allow for access to an instance for HTTP and HTTPS, while blocking all other traffic:

| Rule number | Description | CIDR | Action | Protocol | Traffic Type | Start Port | End Port |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | HTTPS In | 0.0.0.0/0 | Allow | TCP | Ingress | 443 | 443 |
| 2 | HTTPS Out | 0.0.0.0/0 | Allow | TCP | Egress | 443 | 443 |
| 3 | HTTP In | 0.0.0.0/0 | Allow | TCP | Ingress | 80 | 80 |
| 4 | HTTP Out | 0.0.0.0/0 | Allow | TCP | Egress | 80 | 80 |
| 98 | Deny All In | 0.0.0.0/0 | Deny | ALL | Ingress | 1 | 65535 |
| 99 | Deny All Out | 0.0.0.0/0 | Deny | ALL | Egress | 1 | 65535 |
