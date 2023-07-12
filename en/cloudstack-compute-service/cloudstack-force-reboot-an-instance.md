---
title: "CloudStack: Force shutdown an instance"
slug: cloudstack-force-reboot-an-instance
---


If an instance is becoming unresponsive, use those steps to force shutdown instance :

   - Gather instance ID: in the detailed view of an instance, take note of the field **ID**
   - Configure CloudMonkey environment: [procedure](../cloudstack-compute-service/install-and-config-cloudmonkey.md)
   - In CloudMonkey, run:  `stop virtualmachine id=ID forced=true`

To start the instance, use CloudMonkey and run: `start virtualmachine id=ID`
