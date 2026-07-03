# Creating Visual Filters

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/creating-visual-filters_f382a86d-2a99-4098-b283-40253b9f46f9*

Objective
After completing this lesson, you will be able to configure visual filters in the list report.
## Visual Filters
The visual filter bar offers a unique way to filter large data sets through visualizations. This helps the users to recognize facts and situations, while reducing the number of interaction steps needed to gain insights or to identify significant single instances. The visual filter bar allows users to combine measures with filter values. For example, a "Product" might have the filter value "Product Name" and the measure might typically be "Revenue", "Cost", or "Quantity". If you opt for the measure "Revenue", the chart would show the "Revenue by Product", thus enabling the user to filter the data by choosing a particular product name and its revenue.
Chart visualization increases the joy of use and helps users to see relevant data more quickly. For filtering, the visual filter bar uses all of the three types of interactive chart: line chart, bar chart, and donut chart. For more information, see [interactive chart](https://experience.sap.com/fiori-design-web/interactive-chart/): [bar chart](https://experience.sap.com/fiori-design-web/interactive-bar-chart/), [line chart](https://experience.sap.com/fiori-design-web/interactive-line-chart/) and [donut chart](https://experience.sap.com/fiori-design-web/interactive-donut-chart/).
For more information about the design guidelines, see [Visual Filter Bar](https://experience.sap.com/fiori-design-web/visual-filter-bar/).
The best practice when using visual filters is to have visual filters for each compact filter.
## Add Visual Filters to the List Report of the Manage Travels App
### Usage Scenario
In this exercise, our objective is to add three visual filters, Customer, Agency, and Begin Date, with the help of the Page Editor. The user can then filter the table by selecting a visualization in the chart.
### Task Flow
With the help of the Page Editor, first you will add the visual filters Customer and Agency as they are already used as compact filters in the app. Then, you will add another visual filter Begin Date with a line chart as line charts are only enabled for date fields. To achieve this, we must remove the filter restrictions on the _Begin Date_ field.
### Prerequisites
You have completed the exercise Adding a Chart to the List Report in the unit Discovering the Analytical List Page (lesson: Discovering the Analytical List Page. Alternatively, you can check out its solution branch: [solution/add-chart-to-listreport](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-chart-to-listreport).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B89BF9EA51EB0C94:uebung)
### Steps
  1. Open your CAP project in the SAP Business Application Studio.
  2. In the Explorer view, select Projects\fiori-elements-v4-cap-advanced\app\travel_processor.
  3. Right-click on _travel_processor_.
  4. Select _Show Page Map_. The Page Map of the _Manage Travel_ app appears.
  5. On the _List Report_ , select the _Edit_ icon. The Page Map of the TravelList page appears.
  6. Under _Filter Bar_ , select the _Add_ icon corresponding to the _Filter Fields_.
  7. Add the filter bar Agency to the visual filters.
    1. Choose **Add Visual Filter**. The _Add Visual Filter_ dialog appears.
    2. From the _Filter Field_ dropdown, choose **to_Agency_AgencyID**.
    3. From the _Value Source Property_ dropdown, choose **to_Agency_AgencyID**.
    4. Select _Add_.
  8. Add the filter bar Customer to the visual filters.
    1. Select the _Add_ icon corresponding to _Visual Filters_.
    2. From the _Filter Field_ dropdown, choose **to_Customer_CustomerID**.
    3. From the _Value Source Property_ dropdown, choose **to_Customer_CustomerID**.
    4. Select _Add_.
  9. Remove the restriction on the BeginDate property.
    1. Select _projects_.
    2. From the list of options, choose **Go to File**.
    3. From the list of options, choose **schema.cds**. The _schema.cds_ file opens.
    4. Remove the BeginDate property from the @Capabilities.FilterRestrictions annotation.
  10. Add the filter bar Begin Date to the visual filters.
    1. Select _Page Editor - travel_. The Page Map of the _travel_ appears.
    2. On the _List Report_ , select the _Edit_ icon. The Page Map of the _TravelList_ page appears.
    3. Select the _Add_ icon corresponding to _Visual Filters_.
    4. From the _Filter Field_ dropdown, choose **BeginDate**.
    5. From the _Value Source Property_ dropdown, choose **BeginDate**.
    6. From the _Chart Type_ , choose **Line**.
    7. Select _Add_.
  11. View all three visual filters on the app.
    1. Open the app in the new tab on the web browser.
    2. On the right, select the _Visual Filters_ icon. You can see the three visual filters, _Travel by Agency_ , _Travel by Customer_ , and _Travel by Starting Date_ in the filter bar.
    3. On the _Travel by Agency_ , select the first component in the bar chart.
    4. Select _Go_.
    5. On the _Travel by Customer_ , select the first component in the bar chart.
    6. Select _Go_. You can see the data corresponding to the selected chart in the _Travels by Customer Country_ and _Travels_ table.
    7. On the _Travel by Starting Date_ , select the first component in the line chart.
    8. Select _Go_. You can see the data corresponding to the selected chart in the _Travels by Customer Country_ and _Travels_ table.
    9. On the _Travel by Customer Country_ , select a bar chart. You can see that the data in the _Travels_ table is filtered based on the selected bar chart.

### Result
You have added three visual filters to the app.
Note
  * You can find the files for this solution on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-visual-filters](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-visual-filters).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-chart-to-listreport..solution/add-visual-filters).

### Next Steps
For more information, see
  * [Visual Filters](https://ui5.sap.com/#/topic/1714720cae984ad8b9d9111937e7cd38)
  * [Visual Filter Bar](https://experience.sap.com/fiori-design-web/visual-filter-bar/)

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/discovering-the-analytical-list-page_2327de06-26e4-34e9-bd94-9164b0fb802f)
