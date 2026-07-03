# Using Building Blocks

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/using-building-blocks*

Objective
After completing this lesson, you will be able to use building blocks provided by SAP Fiori elements to extend your apps with minimal custom coding.
## Building Blocks
Building blocks are reusable pieces of code that are consistently implemented in the SAP Fiori elements framework. If you use them, you can be sure that your app follows the SAP Fiori design guidelines and that the standard features, like draft handling or side effects, will be automatically supported in your building blocks. They are metadata driven, just like the floorplans.
Building blocks can also be used outside of the floorplans. You can use them in your custom applications, or in your custom extensions.
Building blocks are not SAPUI5 controls, but rather a set of templating instructions that are used to create a specific control tree, depending on the bound data structures.
Check the list of all available building blocks: [Overview of Building Blocks](https://sapui5.hana.ondemand.com/test-resources/sap/fe/core/fpmExplorer/index.html#/buildingBlocks/buildingBlockOverview)
You may also check [sap.fe.macros](https://sapui5.hana.ondemand.com/sdk/#/api/sap.fe.macros), a library of building blocks provided by SAP Fiori elements.
## Add a Field Building Block to Your Custom Section
In this exercise, you will add an information message to the _Itinerary_ custom section. The message will be displayed above the geo map. You will use a field building block for it.
### Prerequisites
You have completed the exercise Add a Custom Section to the Object Page in the same unit (lesson: Using Extension Points).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_6FB0DD9BEA9A33A5:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Select _GeoMap.fragment.xml_ from the _webapp/ext_ folder of your _travels_ project.
  3. Add the following sample code inside the VBox control to add an information message:
Code Snippet
Copy codeSwitch to dark mode

```

123456

<HBox class="">
   <Text text="The bookings were confirmed on" class="sapUiTinyMarginEnd"/>
   <macros:Field readOnly="true" metaPath="CreatedAt" id="custom-flightdate"/>
   <Text text="by" class="sapUiTinyMarginBeginEnd"/>
   <macros:Field readOnly="true" metaPath="AgencyID" id="custom-airline"/>
</HBox>

```

  4. The IDs for the newly added UI controls are missing . Select <HBox line from the code.
  5. Select the _Quick Fix_ icon from the selected <HBox line.
  6. Select the _Generate IDs for the entire file_ option from the list. The IDs get generated for the newly added UI controls.
  7. Switch to the app preview in your browser.
  8. Select the _Itinerary_ tab from the object page. You can see that the information message is added to the custom section.

### Result
You successfully added an information message to the _Itinerary_ custom section. The message is displayed above the geo map. You used a field building block for it.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit10ExaminingTheFlexibleProgrammingModel/lesson3UsingBuildingBlocks/exercise1AddAFieldBuildingBlockToYourCustomSection.md).
