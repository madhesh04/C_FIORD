# Configuring the List Report Filter Bar

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/adding-fields-to-the-filter-bar_e7c5b6ac-dc2c-44a5-8ee0-a1c7922da00c*

Objective
After completing this lesson, you will be able to configure the value help dialog for the semantic fields of type Date.
## Add Fields to the List Report Filter Bar
The filter bar on top of the list report allows you to filter entries using the specified parameters. You can add new fields to the filter bar, enabling new parameters. For example, you can only show entries that start and finish on a certain date.
You can configure the filter bar fields by adding com.sap.vocabularies.UI.v1.SelectionFields to your annotation file.
You can also use SAP Fiori tools. You can choose between two options:
  1. Use the guide _Add and edit filter fields_ from guided development. You will look at this option in this exercise.
  2. Open the Page Map and add a filter field there. You have already covered this in the unit Getting an Overview of SAP Fiori Tools (lesson: Creating a Second App using the Application Generator).

### Task Flow
You will first check how the list report looks before the changes. Then, you will use guided development to add the filter fields. Finally, you will check the results.
### Prerequisites
You have completed the exercise Change the Standard UI Texts in the unit Configuring the General Features of List Reports and Object Pages (lesson: Adjusting the Standard SAP Fiori Elements UI Texts). Alternatively, you can check out its solution branch: [solution/change-standard-ui-texts](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/change-standard-ui-texts).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B6F1E7C7813E1A2:uebung)
### Steps
  1. Open _Adapt Filters_ in the list report. You can see the **End Date** and **Starting Date** fields in the popup menu. Select _Cancel_.
  2. Add the fields using guided development.
    1. Switch to SAP Business Application Studio and choose travel_processor > Open Guided Development. Enter **filter** in the search field to narrow down the number of guides displayed.
    2. Select _Add and edit filter fields_ and choose _Start Guide_.
    3. Select **app/travel_processor/layouts.cds** from the **CDS File** dropdown menu, **TravelService** from the **Service** menu and **Travel** from the **Entity** menu.
    4. Choose _Add selection field_ and select **BeginDate** from the **Property** menu.
    5. Scroll up to add another field. Choose _Add selection field_ and select **EndDate** from the **Property** menu.
    6. Scroll down to see the CAP CDS @UI.SelectionFields annotation for your layouts.cds file. Select _Insert Snippet_ to add it.
    7. Open the schema.cds file to see the code that has been added.
  3. Check the results.
    1. Switch to the app preview. You can see the **Starting Date** and **End Date** fields that have been added to the filter bar.
    2. Note how you can see calendar dates, single dates like **Today** or **Tomorrow** and date ranges in the dropdown menus for both fields.
  4. Check the mapping of the CAP CDS Date type to OData Edm.Date type. The fields BeginDate and EndDate are of type Date, which is a [CAP CDS built-in type](https://cap.cloud.sap/docs/cds/types). You can see the CAP CDS types for each property in the schema.cds file. The CAP CDS type Date is mapped to the OData EDM type Edm.Date, as you can see in the $metadata file.

### Result
Below you can see the definition of the Travel entity in the schema.cds file and the corresponding OData representation of the Travel entity.
![Schema.cds file highlighting the BeginDate and EndDate](../images/7cc1c8435a646f27.png)![Travel Entity metadata highlighting the BeginDate and EndDate](../images/a2982ec7ca0b2c89.png)
For other examples of mapping CAP CDS types to OData types, see [OData type mapping](https://cap.cloud.sap/docs/advanced/odata#type-mapping).
You have seen that Edm.Date-based fields are rendered with a calendar in the value help dropdown menu out of the box. Semantic operators, such as **yesterday** and **today** , are enabled by default in the value help dropdown menu because the @Capabilites.FilterRestrictions annotation was part of your service from the very beginning.
In this lesson, you have learned how to add new filter fields using guided development.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-semantic-fields-to-filterbar](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-semantic-fields-to-filterbar).
  * You can find the link to the direct comparison of the branch to the previous one on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/change-standard-ui-texts..solution/add-semantic-fields-to-filterbar).
