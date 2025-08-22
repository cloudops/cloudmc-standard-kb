---
title: "Reporting in CloudOps"
slug: reporting-in-cloudops
---


This article provides an overview of the CloudOps reporting system.

## Overview

The system provides two general types of reports:

-   Usage
-   Infrastructure

As your customers consume cloud resources from the service connections that you have configured and made available to them, the system is metering this usage, processing it, and storing the resulting data. In order to help stakeholders and decision makers understand and track usage of these resources and associated costs, the system provides usage reports to present this data in a timely manner. These reports enable the visualization of consumption data, and to analyze it in different ways, such as over different time periods, or by grouping into product categories or billing types.

Infrastructure reports, on the other hand, allow cloud managers and other stakeholders to easily see the resources that have been deployed in their service connections. Additionally, they can see their current hardware capacity to assist with planning for future needs. At this time, these reports are limited to users of CloudStack services.

With increasing levels privilege, users can access more reports. Users with the **Guest** or **User** system role see no reports. Users with the **Administrator** system role see basic usage reports for their own organization only. Finally, users with the **Reseller** system role see usage and infrastructure reports for their own organization as well as for their sub-organizations. Keep in mind that \[custom roles\]\(../admin/rbac.md\) allow more nuanced access control than the defaults referred to here.

## Usage reports

CloudOps usage reports are very closely related to the monetization system. These reports are generated from usage data that has been collected, processed, and stored for the current and previous billing cycles. They provide cost data because charges have been calculated accordingly based on the usage and the configured monetization settings, as well as for any applicable commitments in the billing cycle. Billing cycles, dates, and other attributes that appear on reports are controlled from the **Admin** &gt; **Billing** section of the interface. The actual products and prices which appear on reports are controlled from the **Admin** &gt; **Monetization** section.

The system always attempts to provide the most recent data possible. However, the availability of data depends on the remote service, and there can always be some sort of delay in reporting usage. Some services do not guarantee the integrity of their billing data until several days after the close of their own billing cycles.

The usage reports are intended to help managers and resellers understand their spending trends and how their product offerings are being utilized. For example, it can be very useful to see fluctuations over a given year and to identify time frames where infrastructure might be spun down to save on costs. Conversely, it can help to see where sustained usage might mean that signing onto a commitment would be advisable. Usage reports can also be invaluable for troubleshooting problems, such as isolating spikes in usage or unexpected drops in consumption.

When looking at usage reports on a day-to-day basis, it is important to bear in mind that several events can skew the reporting. For example, some cloud providers might report the cost for all reserved instances at once. This would result in a one-day apparent spike in usage, instead of being evenly spread across the month. Similarly, because there may be a delay in reporting due to the policies of the cloud provider, a charge may suddenly appear on a day in the past where previously there had been no such charge. Familiarity with the nuances of each cloud provider can help understand these behaviors.

## Utility pricing versus commitment

CloudOps supports two models for allocating usage charges to customers:

-   **Utility pricing**

    Utility pricing calculates the appropriate charges for usage based on the prices defined by the reseller in the monetization settings. The defined rate is applied to the quantity of usage throughout the billing cycle, and any applicable discounts or credits are included in this calculation. If there is no usage, there is no charge.

    This model is also known as pay-as-you-go, or pay-per-use. Because it is variable, it is always post-paid \(invoiced at the end of the billing cycle\). Utility pricing allows a customer to pay only for what they use, and provides flexibility for increasing or decreasing workloads as needed.

-   **Commitment**

    Commitments are fixed-term agreements between a reseller and a customer. The customer agrees to purchase a fixed quantity of product every month for a specific price. Since this is guaranteed monthly recurring revenue, the reseller is incentivized to extend a more competitive rate on the commitment.

    When negotiating a commitment, it is important that the customer be able to forecast optimal usage of the product, because the customer will pay the agreed-upon price whether or not they use the full quantity during that month. Unused portions of a commitment do not carry over to the next billing cycle.


All usage reports indicate utility and commitment usage separately.

## Infrastructure reports

For users of the CloudStack plugin, the system provides two reports specific to this service:

-   **Infrastructure Entities**

    This report lists all entities in the selected CloudStack service connection. Select from public IPs, bare-metal machines, or instances. The report provides basic details for each entity.

-   **Capacity Report**

    Helps a reseller with a bare-metal offering to track and plan their resources more effectively. It lists the total capacity of each offering, the amount allocated and the amount available, along with its basic characteristics.


