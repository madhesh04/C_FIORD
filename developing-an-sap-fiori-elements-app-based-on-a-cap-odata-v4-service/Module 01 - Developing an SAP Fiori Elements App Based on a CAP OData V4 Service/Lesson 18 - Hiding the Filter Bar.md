# Hiding the Filter Bar

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/hiding-the-filter-bar_d63a9e05-85ff-41f9-a9bb-0890c86d4369*

Objective
After completing this lesson, you will be able to create a worklist from the list report.
## The Worklist
The worklist floorplan is a simplified list report without a filter bar. It displays a collection of items that are to be processed by the user. The processing of the items includes reviewing details of the list items and taking actions. This differs from the list report floorplan, which focuses on finding and acting on relevant items from a large dataset.
You can create a worklist page using the SAP Fiori application generator. You can also hide the filter bar in the list report to create a worklist. To hide the filter bar, you can either change the setting directly in the manifest.json file or use the Page Map to make the necessary changes to the manifest.json file.
### Further Reading
  * [Worklist](https://sapui5.hana.ondemand.com/sdk/#/topic/d1d588f1061b4bac96a1facb80d3f3a2)
  * [Configuring Filter Bars](https://sapui5.hana.ondemand.com/sdk/#/topic/4bd7590569c74c61a0124c6e370030f6.html)
  * [SAP Fiori Design Guidelines](https://experience.sap.com/fiori-design-web/)

## Hide the Filter Bar in the List Report
### Context
In this exercise, you will modify the list report to create a worklist. You can do this in SAP Business Application Studio.
### Task Flow
In the Manage Travels application, you will hide the filter bar available in the list report.
### Prerequisites
You have completed the exercise Add Fields to the List Report Filter Bar in the unit Configuring the List Report Filter Bar (lesson: Adding Fields to the Filter Bar). Alternatively, you can check out its solution branch: [solution/add-semantic-fields-to-filterbar](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-semantic-fields-to-filterbar).
### Watch the Steps and Perform the Simulation
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2E9E3ACD13F5AA9C:uebung)
### Steps
  1. Open the _Manage Travels_ application in SAP Business Application Studio.
    1. In the Explorer view, select Projects/app.
    2. Right-click on app and select Show Page Map. The Page Map of the Travels application appears.
  2. Hide the filter bar of the list report.
    1. On the list report page, select the _Edit_ option. The TravelList Page Editor appears.
    2. Select _Filter Bar_. The filter bar properties appear on the right pane.
    3. Under _Hide Filter Bar_ , from the dropdown, select _True_.
  3. In the Explorer view, select Projects/app/webapp/manifest.json. In the manifest.json file, the following code appears under settings:
Code Snippet
Copy codeSwitch to dark mode

```

1

"hideFilterBar": true

```

  4. View the worklist in the _Manage Travels_ application.
    1. Open the _Manage Travels_ application.
    2. Refresh the browser tab on which the _Manage Travels_ application is displayed.
#### Result
You can see that the filter bar is hidden.

### Result
In this lesson, you have learned that you can disable the filter bar of the list report. By doing so, you have modified the list report to a worklist.
Note
  * You can find the files for this solution on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/hide-filter-bar](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/hide-filter-bar).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-semantic-fields-to-filterbar..solution/hide-filter-bar).

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-the-list-report-filter-bar_6dc70eef-8ee4-3119-8891-e9e2cdb08cd3)
