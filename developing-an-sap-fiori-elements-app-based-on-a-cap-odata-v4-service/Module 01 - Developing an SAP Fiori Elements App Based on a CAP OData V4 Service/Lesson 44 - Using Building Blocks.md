# Using Building Blocks

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/using-building-blocks_b5fa3bd3-11de-428f-b6fc-e0668d2266ff*

Objective
After completing this lesson, you will be able to use building blocks provided by SAP Fiori elements to extend your apps with minimal custom coding.
## Building Blocks
Building blocks are reusable pieces of code that are consistently implemented in the SAP Fiori elements framework. If you use them, you can be sure that your app follows the SAP Fiori design guidelines and that the standard features, like draft handling or side effects, will be automatically supported in your building blocks. They are metadata driven, just like the floorplans.
Building blocks can also be used outside of the floorplans. You can use them in your custom applications, or in your custom extensions.
Building blocks are not SAPUI5 controls, but rather a set of templating instructions that are used to create a specific control tree, depending on the bound data structures.
Check the list of all available building blocks: [Overview of Building Blocks](https://sapui5.hana.ondemand.com/test-resources/sap/fe/core/fpmExplorer/index.html#/buildingBlocks/buildingBlockOverview)
You may also check [sap.fe.macros](https://sapui5.hana.ondemand.com/sdk/#/api/sap.fe.macros), a library of building blocks provided by SAP Fiori elements.
## Create a Table Using the Table Building Block in the Display Customers App
You may use a custom section when some parts of your UI cannot be built using annotations.
In this exercise, you want to display customer's own bookings as an object page table, in the _Display Customers_ app. Additionally, a message strip should be displayed above the table (this will be implemented in the next exercise). Thus, you will create a custom section using the Page Editor and add a table building block to it.
### Task Flow
You will first use the Page Editor to create a custom section on the app's object page. Then, you will add a custom table building block to it.
### Prerequisites
You have completed the exercise Add a Custom Column to the Table on the Object Page of the Manage Travels App in the unit Discovering the Flexibility of the Programming Model for SAP Fiori Elements for OData V4 (lesson: Using Extension Points). Alternatively, you can check out its solution branch: [solution/add-custom-column-to-table-on-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-custom-column-to-table-on-op).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B056F2022779AE:uebung)
### Steps
  1. Start the preview for the _Display Customers_ app. Select the first customer in the table.
You will add a table building block with customer's own bookings to the object page. The table will be added into a custom section. The custom section will be placed after the _General Information_ section.
  2. In SAP Business Application Studio, create a custom section by using the Page Editor.
    1. Right click on the _customer_ folder.
    2. Select the _Show Page Map_ option to open the Page Editor.
    3. Edit the passenger object page by clicking on the pencil icon.
    4. Click on the plus icon in _Section_.
    5. Choose _Add Custom Section_.
    6. Add _Own Bookings_ to the _Custom Section Title_.
    7. Click on the globe icon to add localization, and select _Apply_.
    8. Add bookings to the _fragment name_.
    9. Expand the _Anchor Section_ dropdown and choose _General Information_.
    10. Select the _Add_ button.
You can see that a _custom section_ called _Own Bookings_ has appeared under _Sections_ of the object page.
  3. Expand customer>webapp>ext in the file explorer. You can see that the Page Editor has generated the ext folder which includes the Bookings.fragment.xml file.
  4. Open the Bookings.fragment.xml file. You can see some pre-generated xml code in the file.
Add the following code snippet to it:
Code Snippet
Copy codeSwitch to dark mode

```

1

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" xmlns:macros="sap.fe.macros"> <macros:Table metaPath="to_Booking/@com.sap.vocabularies.UI.v1.PresentationVariant" header="Bookings" personalization="Column" readOnly="{ui>/isEditable}" id="OwnBookingsTable" > </macros:Table> </core:FragmentDefinition>

```

  5. Switch to the app window to see the new table.
     * Select the first customer from the table.
     * Navigate to the object page. You can see the custom section _Own Bookings_ containing a _Bookings_ table.
     * Select the _Own Bookings_ tab.
You can see that you can navigate to the custom section by selecting _Own Bookings_ in the anchor bar. Note that the table building block looks and behaves identical to an annotation-based table.

### Result
In this exercise you have created a custom section with the help of the Page Editor and added the table building block to it.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-table-building-block](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-table-building-block).
  * You can find the link to the direct comparison of the branch to the previous one on [Github](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-custom-column-to-table-on-op..solution/add-table-building-block).

### Next Steps
For more information, see:
  * [Video series on flexible programming model for SAP Fiori elements](https://blogs.sap.com/2022/12/08/video-series-on-flexible-programming-model-for-sap-fiori-elements/)
  * [The Table Building Block](https://sapui5.hana.ondemand.com/#/topic/3801656db27b4b7a9099b6ed5fa1d769)
