---
title: "Cloudflare: Add a domain"
slug: cloudflare-add-domain
---


## About this task

This article will guide you through the process of adding a new domain to a Cloudflare environment.

## Before you begin

-   Your Cloudflare environment must already exist

## Procedure

1.  Navigate to your Cloudflare service using the **Services** menu, and click on the target environment from the service page.

2.  Click on the **Add Domain** button. The **Add Domain** page will appear.

3.  Enter the fully qualified domain name to add.

    It is not necessary to have the trailing period at the end of the domain name. The system will automatically add it for you.

    Optionally, mark the **Quick Scan for Records** checkbox to have the system import any existing resource records, by querying the current name servers.

4.  Click **Submit**.

5.  If you marked the **Quick Scan for Records** checkbox, click on your domain when the environment page appears, and then verify that all the required resource records were successfully imported.

    It is possible that some records may be missed during the scanning process. If any records are missing, add the missing records manually.


## Results

-   The domain is now listed in the target environment
-   If importing was selected, you have verified that all records have been imported, and any missing records have been added manually

