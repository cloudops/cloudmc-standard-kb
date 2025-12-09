
This article provides details on how to use the Organization Usage report, and its various options.

## Overview

The Organization Usage report is the first place to look when you need to see exactly what resources your organization is consuming and to understand your spend. For the selected time range, the report provides an itemized list of every product that was used, how much was consumed, and the associated cost. The full report includes both utility usage data and commitments for all service connections in the organization.

If your user account has been granted access to multiple organizations, the Organization Usage will provide a view of the usage for any organization which is visible to you. This report is visible only with the **Administrator** role, or with a custom role that has the **Usage: View** permission.

![A screenshot of the Organization Usage Report](/assets/reporting-organization-usage.png)

The Organization Usage report is divided into the following sections:

-   **Filters**
-   **Commitment usage**
-   **Utility usage**

See the corresponding sections below for details.

When multiple currencies are configured for one or more of the selected service connections:

-   Utility usage will be displayed in separate sub-sections
-   Each sub-section will have a total displayed accordingly for the currency
-   Each currency will have its own set of product category filters.

When only a single currency is configured, the total of the usage costs for the selected time period appears at the bottom of the report. It is important to note that the Organization Report is not an invoice, and it does not include any discounts, credits, or taxes. Also, the charges within the current billing cycle are estimates and are subject to change until the final invoice is issued.

## Filters

![Screenshot of the filters available for the Organization Usage report, with the Where and What tab selected](/assets/reporting-organization-usage-filters.png)

1.  **List of currently selected filters**

    The list contains all the criteria that have been selected for the currently displayed report. Click on the **×** button to remove a single criterion, or click the **Clear all filters** to eliminate all criteria.

2.  **Time filters**

    Click on the **When?** tab to display a date selector and choose the desired period for the report. Use the preset buttons, or click on **Custom** to select an exact range.

3.  **Data filters**

    Click on the **Where and What?** tab to display filters for choosing the source of data:

    -   The **Organization** popup menu controls which organization will have usage data displayed on the report. The menu will list the current organization and any sub-organizations to which your user account has been granted access. Only one organization at a time may be selected.
    -   The **Service Connection** popup menu lists all service connections for the selected organization. If desired, choose a service connection to narrow down the displayed usage data for just that connection. Only a single service connection may be selected. If no service connection is selected, usage data for all service connections will be displayed.
    -   If a service connection is selected, a popup menu for **Environment** will appear, enabling you to further narrow down the data to a specific environment. Only a single environment may be selected. If no environment is selected, usage data for all environments in the selected service connection will be displayed.

![Screenshot of the selector to hide and show product categories in the report](/assets/reporting-organization-usage-categories.png)

1.  **Report header**

    The header lists the selected date range and organization, as well as the currency or currencies which appear in the currently configured report.

2.  **Currency for this sub-section**

    This appears only when a report contains usage data for multiple currencies, to indicate the currency for charges up to the next currency sub-section.

3.  **Product category selector**

    A list of buttons appears, each with a product category and a sum of the charges for that product category. Click on any button to display only usage data associated with that product category. In the provided screenshot, the **Compute** category is selected. Multiple categories may be selected. The first button is marked **Total**, and clicking on it will reset the product category selector to include all categories.

    Note that when multiple currencies appear on a report, each currency sub-section will have its own product category selector.


## Commitment usage

![Commitment usage](/assets/reporting-organization-usage-commitment.png)

Every commitment that has been configured for the selected organization and is active is the selected time frame will be listed here. The commitment name, product name, SKU, committed usage, rate, and cost appear, along with a total for each commitment. If more than one billing cycle is selected in the time period, each product in each commitment will display the committed quantities for each billing cycle within the span of the selected time period.

## Utility usage

![Utility usage](/assets/reporting-organization-usage-utility.png)

This section displays a total of the usage seen in the selected time period. Every product appears as a line-item with the quantity used, rate, and cost, and are grouped by product category. Each product category will have a sub-total.


