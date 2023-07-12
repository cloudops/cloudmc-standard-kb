---
title: "CloudStack: Move an instance to a different VPC"
slug: cloudstack-move-instance-to-different-vpc
---


Once created, an instance is bound to the zone in which it is deployed.  However, instances can be moved between VPCs in the same zone.

After moving to a different VPC:
   - The instance will be rebooted for the changes to take effect.
   - The instance will have a new private IP.
   - All port forwarding rules to the instance will be deleted and will have to be recreated.
   - The instance will be removed from all load balancer rules in the old VPC.
   - The instance will be dissociated from any public IP address from the old VPC, and an address will have to be allocated from the new VPC.

### Move the instance

1. Navigate to the environment where the instance is located.
1. From the *Instances* page, find the desired instance and click on the *Action* menu on the far right hand side of the entry.
1. Select *Change network*.
1. The *Change network* page will appear.  The instance name and its current network will be listed.
1. The *Destination network* pop-up menu will list the available networks, grouped by VPC, to which the instance may be connected.  Select the desired network.
1. Check the box *I understand that the instance will be restarted*.
1. The instance will be stopped, connected to the new network, and will start.
1. When the instance is booted and in the **running** state, verify network connectivity.
