# Enriching the Object Page Header with Micro Charts

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/enriching-the-object-page-header-with-micro-charts_b41281e3-2997-4e04-96c9-2ad1258006cf*

Objective
After completing this lesson, you will be able to configure the bullet micro chart and progress indicator as object page header sections.
## Add the Bullet Micro Chart and the Progress Indicator to the Header Area
### Usage Scenario
The user must be able to see the progress indicator for each travel in the object page header, similar to that in the list report. Additionally, the user must be able to see the total supplements for each booking in the header of the subobject page.
### Task Flow
In this exercise, you will first add the progress indicator for a travel to the header section. You may have already created and implemented the method for calculating and updating the progress for a travel in your CAP service. You have added the progress indicator as a table column in one of the previous exercises. Here, you will use the Page Editor to add it to the travel object page as a header section. You can use the guided development aid named Add a header facet using Data Points as well.
Next, you will add a bullet micro chart. The bullet micro chart will display the total of supplements for each booking, as a header section in the subobject page. You can use the Page Editor to add the bullet micro chart.
### Prerequisites
You have completed the exercise Add Travel Status, Total Price, and the Deduct Discount Action to the Header Area in the unit Shaping the Header Area of the Object Page (lesson: Placing Key Figures in the Header Area). Alternatively, you can check out its solution branch: [solution/put-travel-status-total-price-deduct-discount-to-header-area-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/put-travel-status-total-price-deduct-discount-to-header-area-op).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_E91837E1B55818B0:uebung)
### Steps
  1. Add the progress indicator to the header.
    1. Open your CAP project in Business Application Studio.
    2. In the Explorer view, select Projects\fiori-elements-v4-cap-advanced\app\travel_processor\webapp.
    3. Right-click on _webapp_.
    4. Select _Show Page Map_. The _Page Map-travel_ appears.
    5. Select the _Edit_ icon of the object page. The Page Map of _TravelObjectPage_ appears.
    6. Expand _Header Sections_. You can see the available header sections: _Travel Status_ and _Total Price_.
    7. Select the Add icon corresponding to the _Header Sections_.
    8. Choose _Add Progress Section_. The _Add Progress Section_ dialog appears.
    9. From the _Value Source Property_ dropdown, choose **Progress**.
    10. Select _Add_.
    11. In the right pane, under _Label_ , enter the label name **Progress of Travel**.
    12. Select the globe icon corresponding to the label name.
    13. Select _Apply_. The label text is added to the i18n.properties file.
  2. Add the bullet micro chart to the header of the subobject page.
    1. Switch back to the SAP Business Application Studio. The Page Editor is open.
    2. Select _Page Map_ to go back to the Page Map.
    3. Select the _Edit_ icon of the subobject page. The page map of _BookingObjectPage_ appears.
    4. Select the _Add_ icon corresponding to the _Header Sections_.
    5. Choose _Add Micro Chart Section_. The _Add Chart Header Section_ appears.
    6. From the _Chart Type_ dropdown, select **Bullet**.
    7. Select _Add_.
    8. From the _Value_ dropdown, choose **TotalSupplPrice**.
    9. From the _Maximum Value_ dropdown, enter the value **120**.
    10. Select _Add_.
    11. In the right pane, under _Label_ , enter the label name **Total Supplements**.
    12. Select the globe icon corresponding to the label name.
    13. Select _Apply_. The label text is added to the i18n.properties file.
    14. Select _Edit in source file_. The layout.cds file opens.
    15. Add the TargetValue: 100 property to the @UI.DataPoint annotation.
    16. Add the values DeviationRangeLowValue: 20 and ToleranceRangeLowValue: 75 for the CriticalityCalulation.

### Result
You have learned to add a progress indicator to the header section of the _Travel_ object page. You have also learned to add a bullet micro chart to the header section of the _Booking_ object page (subobject page).
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-bullet-micro-chart-and-progress-indicator-to-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-bullet-micro-chart-and-progress-indicator-to-op).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/put-travel-status-total-price-deduct-discount-to-header-area-op..solution/add-bullet-micro-chart-and-progress-indicator-to-op).

### Next Steps
For more information, see
  * [Header Facets](https://sapui5.hana.ondemand.com/sdk/#/topic/17dbd5b7a61e4cdcb079062e976cd63f)
  * [Progress Indicator Facet](https://sapui5.hana.ondemand.com/sdk/#/topic/3b5e01c647f44ea98655b8c08feba780)
  * [Micro Chart Facet](https://sapui5.hana.ondemand.com/sdk/#/topic/e219fd0c85b842c69ac3a514e712ece5)
