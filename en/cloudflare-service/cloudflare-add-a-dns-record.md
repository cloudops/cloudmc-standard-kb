---
title: "Cloudflare: Add a DNS record"
slug: cloudflare-add-dns-record
---


## About this task

This article will guide you through the process of adding a new DNS record to a Cloudflare DNS domain.

## Before you begin

-   Your Cloudflare environment must already exist
-   The target domain must already exist in the environment
-   The registrar where this domain name is hosted must point to the Cloudflare name servers
-   The state of the domain must be `Active`

## Procedure

1.  Navigate to your Cloudflare service using the **Services** menu, click on the target environment from the service page, then click on the target domain.

2.  Click the **Add DNS record** button.

3.  On the **Add DNS record** page, select the record type and enter the values for your record.

    Each resource record type has its own fields, therefore changing the **Type** field will change the displayed fields.

4.  Select a time to live \(TTL\) value for this record.

    This option controls how long a DNS client will cache the record before requesting it again from the DNS system.

5.  \(Optional\) Enter a comment to be appended to the record. This is internal to the record and will not be displayed in the list of records.

6.  Click the **Submit** button.


## Results

-   The new DNS record is now listed in the target domain page.
-   The record now resolves when queried through the DNS system

