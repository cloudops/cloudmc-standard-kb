---
title: "Daily Cost Overview report"
slug: reporting-daily-cost-overview
---


This article provides details on how to use the Daily Cost Overview report, and its various options.

## General description

The Daily Cost Overview is an interactive report intended for a financial, accounting, and executive audience, to enable them to understand the evolution of their usage costs over time. The default report provides a high-level view of all costs in a billing cycle. The user may then select from various filtering criteria to focus on interesting aspects of the cost data. If desired, the report can compare against the cost data from another billing cycle, or drill down to see more details.

The first section of the report presents the full-month \(billing cycle\) aggregation of cost data in a donut chart and an accompanying legend, with all data for the selected billing cycle aggregated using the selected grouping. The second section of the report has a stacked bar chart presenting a daily aggregation of cost data using the same grouping, for every day in the billing cycle. Using these two charts, users can drill into specific categories, plan types, or days to isolate the target data.

The final section of the report is a list of events which occurred during the selected time period. This enables a user to potentially correspond events and changes in spend, and to find root causes for trends.

![A screenshot of the Daily Cost Overview Report](/assets/reporting-daily-cost-overview.png)

1.  **Group by**

    Determines the aggregation method for the charts in the first and second sections of the report.

    -   Product category: Cost data for all products will be grouped by the category \(and by extension, the product catalog\) in which each product is located.
    -   Plan type: Cost data for all products will be grouped into either utility usage or commitments. On the daily aggregation chart, costs attributable to commitments will be evenly spread across every day in the month.
    Note that the default grouping for a reseller can be set in **Admin** &gt; **Reporting**.

2.  **Organization**

    This field is available only when your user account has access to more than your own organization. It contains an alphabetically-sorted list of organizations to which you have access. Select an organization to see its cost data.

3.  **Service Connection**

    By default, the Daily Cost Overview shows cost data for all service connections in the selected organization. To narrow down the displayed data to only a single service, select the desired service from the **Service Connection** field.

    Selecting the **Others** item will display cost data that cannot be associated with any single connection, such as commitments that are scoped to the selected organization.

    Click on the **X** icon to clear the field. Upon clearing, data for all service connections and all environments will be displayed.

4.  **Environment**

    By default, the Daily Cost Overview shows cost data for all environments in the selected organization. However, when a specific service has been selected in the Service Connection field, you can further narrow down the data to a single environment in the selected service using the **Environment** field.

    Click on the **X** icon to clear the field and display data for all environments in the selected service.

5.  **Selected period**

    Use this filter to select the desired billing cycle for the report. The current period is selected by default.

6.  **Compared to**

    Use this field to select a billing cycle to compare against the cycle in the **Selected period** filter. The comparison data will appear as an additional column in the monthly aggregation table to show the difference in value, and will also appear as a horizontal marker in the stacked bars for each day in the daily aggregation.

7.  **Monthly aggregation**

    This section of the report contains a donut chart and a table, which display the cost data targeted by the organization, service connection, environment, and selected period filters. The data will be grouped either by product category or by utility versus commitment, as specified in the **Group by** option.

    Clicking on a category or plan type will toggle its visibility on the monthly aggregation as well as on the daily aggregation, making it easier to focus on particular items.

    When comparing against another billing cycle, each item in the table will have a column showing the difference in totals between the two selected billing cycles.

8.  **Daily aggregation**

    This section of the report shows a stacked bar chart, which displays the data targeted by the organization, service connection, environment, and selected period filters. Each stacked bar shows the cost data for a single day in the selected period, and each region in the bar represents the relative portion of cost attributable either to utility versus commitment, or to each product category.

    When comparing against another billing cycle, the total cost for a given day from the comparison month will appear as a horizontal line overlaid on the stacked bar.

    Clicking on a bar will refresh the user activity section to display only activities with a timestamp matching that day. Clicking the bar again will expand the user activity section to the entire selected period.

9.  **User activity**

    This section of the report provides a list of activities that occurred in the billing cycle chosen in the **Selected period** filter. These activities are pulled from the Activity Log. The report will show only events that are related to the service connections that are included in the report. If a stacked bar in the daily aggregation has been clicked, this section will show only activity from that day. To expand the view to the entire selected period, click on the bar again.


