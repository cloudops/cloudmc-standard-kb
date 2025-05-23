---
title: "Azure: Service Overview"
slug: azure-service-overview
---


CloudOps allows cloud operators to access and manage infrastructure and resources that have been deployed on the Microsoft Azure platform. This article will introduce basic concepts of Azure and working with Azure resources in CloudOps.

## Detailed overview

The Microsoft Azure platform is a public cloud, where customers can allocate resources to build an infrastructure for their applications. CloudOps provides a unified interface to access Azure and other services from a single portal. Through CloudOps, users can manage:

-   [Instances](azure-instances.md)
-   [Disks](azure-disks.md)
-   Networks

Because CloudOps acts as a portal to Azure services, you may find that some operations appear to behave differently than when interacting with Azure directly. However, behind the scenes, all operations execute exactly as they normally would. Changes made to Azure entities in CloudOps will be reflected immediately in the actual resources. For example, Azure manages resources within resource groups. CloudOps, on the other hand, exposes resources to users inside of environments, which is a concept that is already familiar to CloudOps users.

CloudOps provides users the ability to manage access to resources and to generate detailed usage reports. In addition, user activity in the Web user interface as well as via the API is captured and made available via the Activity Log. To ensure proper governance, CloudOps automatically creates a user account on the Azure service for every member of an environment. Any operation performed by a user in CloudOps is executed on the Azure service with that user's Azure account, providing complete accountability.

