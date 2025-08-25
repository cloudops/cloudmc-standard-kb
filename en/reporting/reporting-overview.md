---
title: "Overview of reporting"
slug: overview-of-reporting
---


The CloudOps platform provides two general types of reports:

-   Usage
-   Infrastructure

As your customers consume cloud resources from the service connections that you have configured and made available to them, the system is metering this usage, processing it, and storing the resulting data. In order to help stakeholders and decision makers understand and track usage of these resources and associated costs, the system provides usage reports to present this data in a timely manner. These reports enable the visualization of consumption data, and to analyze it in different ways, such as over different time periods, or by grouping into product categories or billing types.

Infrastructure reports, on the other hand, allow cloud managers and other stakeholders to easily see the resources that have been deployed in their service connections. Additionally, they can see their current hardware capacity to assist with planning for future needs. At this time, these reports are limited to users of CloudStack services.

With increasing levels privilege, users can access more reports. Users with the **Guest** or **User** system role see no reports. Users with the **Administrator** system role see basic usage reports for their own organization only. Finally, users with the **Reseller** system role see usage and infrastructure reports for their own organization as well as for their sub-organizations. Keep in mind that [custom roles](../administration/rbac.md) allow more nuanced access control than the defaults referred to here.


