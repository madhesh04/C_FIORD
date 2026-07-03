# Configuring the General Features of List Reports and Object Pages

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-the-flexible-column-layout_b5066855-aa7c-4943-a64b-64050ccfea75*

Objective
After completing this lesson, you will be able to enable the flexible column layout on the UI for your app.
## The Flexible Column Layout
In SAP Fiori elements, the flexible column layout allows you to view both the list report and the object page in the same screen, without navigating back and forth between them.
![TwoColumnsBeginExpanded option of the flexible column layout](../images/54dba6ff846d54ab.png)
You can also display two object pages next to a list report. Each page is displayed in its own column, and you can adjust the column width if necessary.
![ThreeColumnsMidExpanded option of the flexible column layout](../images/dc90d832fe7b2ea6.png)
The flexible column layout can be configured manually in the manifest.json file. You can also configure the layout using the Page Map. For more information, please refer to the SAP Fiori elements documentation: [Enabling the Flexible Column Layout](https://sapui5.hana.ondemand.com/sdk/#/topic/e762257125b34513b0859faa1610b09e)
## Enable the Flexible Column Layout
In this exercise, you will first configure different options for the flexible column layout. Then, you will check the results on the UI.
### Prerequisites
You have completed the exercise Adjust the Object Page of the Display Customers App in the unit Getting an Overview of SAP Fiori Tools (lesson: Creating a Second App using the Application Generator). Alternatively, you can check out its solution branch: [configure-object-page-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/configure-object-page-customer-app).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2676850464C0CFB0:uebung)
### Steps
  1. Open your project in SAP Business Application Studio.
  2. Open the Page Map.
    1. Right-click on _travel_processor_.
    2. Select _Show Page Map_.
  3. Configure the flexible column layout in the _Page Map_.
    1. Select the _Flexible Column Layout_ option.
    2. Scroll down to _Select Layout for 2 Columns_ and select _Mid-Expanded_.
    3. In _Select Layout for 3 Columns_ , select _End-Expanded_.
  4. The flexible column layout is now enabled. Switch back to the app to see how it works.
    1. Select _Travel_ to navigate to its object page.
    2. Note how the object page opens next to the list report on the same screen. As you've selected the _Mid-Expanded_ layout, the object page is wider than the list report.
    3. Select a _Booking_ to navigate to its subobject page. The subobject page opens next to the object page. As you've selected the _End-Expanded_ layout, the last column is wider than the first two columns.

### Result
In this lesson, you have learned how to enable and configure the flexible column layout.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/flexible-column-layout).
  * The solution branch is [solution/flexible-column-layout](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/flexible-column-layout).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/configure-object-page-customer-app..solution/flexible-column-layout).
