---
title: "Create a site-to-site VPN on a VPC"
slug: create-site-to-site-vpn-on-vpc
---


A site-to-site VPN is useful for interconnecting a VPC to a remote office, another data centre, or to another VPC.  For more details, see [Working with VPCs](../basic-concepts/working-with-vpcs.md).

The following example illustrates how to connect two VPCs with a site-to-site VPN.  Details will vary for your particular devices.

#### Example VPC details
| VPC name | Environment name | VPC CIDR | Source NAT IP |
| --- | --- | --- | --- |
| dmz | dmz-env | 10.0.0.0/22 | 172.30.200.106 |
| management | mgt-env| 10.0.4.0/22 | 172.30.200.107 |

#### Site-to-site VPN configuration
1. Go to **dmz-env** environment.
1. Go to *Networking* tab.
1. Click on the gear menu for *Site-to-site VPNs*.
1. Click on *Add site-to-site VPN*.
1. Enter the details for the tunnel from **dmz** to **management**:
   - **Name:** Tunnel to management
   - **Remote public IP:** 172.30.200.107
   - **Remote CIDR:** 10.0.4.0/22
   - **IPSec pre-shared key:** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
   - **Dead Peer Detection:** Enabled
   - **Force encapsulation:** Disabled
   - **Passive connection:** Enabled
   - Accept defaults for all other tunnel options.
1. Click *Submit*
1. Go to **mgt-env** environment and repeat steps 2 though 4.
1. Enter the details for the tunnel from **management** to **dmz**:
   - **Name:** Tunnel to dmz
   - **Remote public IP:** 172.30.200.106
   - **Remote CIDR:** 10.0.0.0/22
   - **IPSec pre-shared key:** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
   - **Dead peer detection:** Enabled
   - **Force encapsulation:** Disabled
   - **Passive connection:** Disabled
   - Accept defaults for all other tunnel options
1. Click *Submit*
1. The list of site-to-site VPNs now lists **Tunnel to dmz**.  The status will say **Connected**.  On the other side of the VPN, the list of site-to-site VPNs in **dmz-env** will have an entry, **Tunnel to management**, and will say **Connected**.
