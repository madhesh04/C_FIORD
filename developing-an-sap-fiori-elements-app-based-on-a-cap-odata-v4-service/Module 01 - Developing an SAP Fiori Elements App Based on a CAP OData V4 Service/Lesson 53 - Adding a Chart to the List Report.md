# Adding a Chart to the List Report

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/adding-a-chart-to-the-list-report_d228124b-1918-40be-b386-16d9e5af6897*

Objective
After completing this lesson, you will be able to enable an entity to support aggregation and add a chart to the list report.
## Transformation Aggregation
For the charts to work, the entity set must support aggregation. SAP Fiori elements supports the transformation aggregation methods such as standard aggregation and custom aggregation.
### Transformation Aggregation that Uses Standard Aggregation Methods
To enable the analytical capabilities the entity must be annotated with @Aggregation.ApplySupported. The collection of the @Analytics.AggregatedProperty annotation must list all the aggregatable measures or aggregation methods that are used. For more information, see [Transformation Aggregation](http://docs.oasis-open.org/odata/odata-data-aggregation-ext/v4.0/cs01/odata-data-aggregation-ext-v4.0-cs01.html#_Toc378326290). For more information on the CAP documentation, see [Transformations](https://cap.cloud.sap/docs/advanced/odata#transformations).
## Add a Chart to the List Report of the Manage Travels App
### Usage Scenario
In this exercise, the objective is to add aggregate capabilities to the service so that you can add analytical capabilities to the list report page and make it an analytical list page.
The user will be able to see the total number of distinct travels grouped by Customer country. The user can also filter the table by selecting visualization in the chart.
### Task Flow
First, you will enhance Travel service with the CDS @Aggregation.ApplySupported annotation, in which you can define GroupableProperties and AggregatableProperties. Once the service is enhanced, you can use the _Add Chart_ functionality in the Page Editor. Finally, you can add the i18n labels to the chart using the Page Editor.
### Prerequisites
You have to check out the branch [solution/initial-app-state-for-analytics](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/initial-app-state-for-analytics).
Note
To enable all features in the analytical list page in the Node.js runtime, we've switched on the new OData parser (odata_new_parser: true), which is still experimental.
Some features such as grouping in the analytical table is not available if you use the ALP with the standard OData parser. For more information, see [SAP Fiori Analytical List Page for SFlight](https://cap.cloud.sap/docs/releases/archive/2022/oct22#alp-sflight).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_52BAAD89821998A8:uebung)
### Steps
  1. Open your CAP project in SAP Business Application Studio.
  2. Annotate the Travel entity with the CDS @Aggregation.ApplySupported annotation to enable the analytical capabilities of the service.
    1. Select _Search Projects_.
    2. Choose **Go to File**.
    3. Choose **travel-service.cds**. The _travel-service.cds_ file opens.
    4. Annotate theTravel entity with the following annotation:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213141516171819202122232425

annotate TravelService.Travel with @Aggregation.ApplySupported: {
  Transformations       : [
    'aggregate',
    'topcount',
    'bottomcount',
    'identity',
    'concat',
    'groupby',
    'filter',
    'expand',
    'search'
  ],
  Rollup                : #None,
  PropertyRestrictions  : true,
  GroupableProperties   : [
    to_Customer_CustomerID,
    to_Agency_AgencyID,
    TravelStatus_code,
    BeginDate,
    PassengerCountry,
  ],
  AggregatableProperties: [
    {Property: TravelID, }
  ],
};

```

  3. Add the chart to the list report.
    1. In the Explorer view, select Projects\fiori-elements-v4-cap-advanced\app\travel_processor.
    2. Right-click on _travel_processor_.
    3. Select _Show Page Map_. The _Page Map-travel_ appears.
    4. Select the _Edit_ icon of the list report page. The Page Map of _TravelList_ appears.
    5. Select _Add Chart_. The _Add Analytical Chart_ dialog appears.
    6. From the _Chart Type_ dropdown, choose **Column**.
    7. From the _Dimension_ dropdown, choose **PassengerCountry**.
    8. From the _Measure_ button, choose **Create new measure**.
    9. From the _Aggregation Method_ dropdown, choose **Count Distinct Values**.
    10. Select _Add_.
  4. Define the label names for _Measures_ and _Dimensions_.
    1. On the _TravelList_ Page Map, select _Chart_.
    2. In the right pane, under _Title_ , enter the chart title as **Travels by Customer Country**.
    3. Select the globe icon corresponding to the chart title.
    4. Select _Apply_. The chart title is added to the i18n.properties file.
    5. Under _Measures_ , _Measure 1_ → _Label_ , select the globe icon.
    6. Select _Apply_. The existing label name is substituted by **i18n >Travels**.
    7. Under _Dimensions_ ,_Dimension 1_ → _Label_ , select the globe icon.
    8. Add the label name **Customer Country**.
    9. Select _Apply_. The dimension label is added to the i18n.properties file.
Note
You can configure additional dimensions by selecting the _Default_ toggle button.
  5. View the chart and group table data based on the chart.
    1. On the _Travels by Customer Country_ , select a bar chart. The count of the data on the _Travels_ table is refined based on the selected bar chart.
    2. Select the _View By_ icon.
    3. From the dropdown, choose **Customer**.
    4. Select the bar chart. The _Travels_ table displays the travels only of the selected customer.

### Result
You have successfully added a chart to the list report of the _Manage Travels_ app.
Note
  * You can find the files for this solution on [GitHub.](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-chart-to-listreport](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-chart-to-listreport).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/initial-app-state-for-analytics..solution/add-chart-to-listreport).

### Next Steps
For more information, see
  * [Analytical List Page](https://ui5.sap.com/#/topic/3d33684b08ca4490b26a844b6ce19b83)
  * [Configuring Charts](https://sapui5.hana.ondemand.com/sdk/#/topic/653ed0f4f0d743dbb33ace4f68886c4e.html)
