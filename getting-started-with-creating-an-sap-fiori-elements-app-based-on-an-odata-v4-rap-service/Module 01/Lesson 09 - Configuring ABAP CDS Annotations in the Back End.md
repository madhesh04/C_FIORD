# Configuring ABAP CDS Annotations in the Back End

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/creating-a-list-report*

Objective
After completing this lesson, you will be able to create a metadata extension, add UI annotations for the list report to it.
## Create an ABAP CDS Metadata Extension for a Projection View
In this exercise, you will add an ABAP CDS metadata extension for the projection view of the _Travel_ entity. You can put all the UI relevant annotations in it.
### Prerequisites
You have completed the exercise Publish the OData V4 Service in the unit Getting an Overview of ABAP RESTful Application Programming Model (lesson: Creating an OData V4 Service).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_FD262B3D49876AAB:uebung)
### Steps
  1. You have the OData service package that you generated previously opened in ADT.
  2. Expand _Core Data Services_ within _ZFE_TRAVEL_######_ , where _ZFE_TRAVEL_######_ is the unique ID of your package.
  3. Select and expand _Data Definitions_. You can see the three projection views for which you can create UI annotations.
  4. Double-click _ZC_FE_TRAVEL_######_ from _Data Definitions_. The projection view for the _Travel_ entity opens.
  5. Create a metadata extension for the _Travel_ entity.
    1. Select and right-click _ZC_FE_TRAVEL_######_ .
    2. Choose _New Metadata Extension_. The _New Metadata Extension_ dialog opens.
    3. Ensure that the name of the metadata extension is entered as **ZC_FE_TRAVEL_######** .
    4. Enter the description as **UI annotations for the Travel entity**.
    5. Select _Next_. The _Select Transport Request_ opens.
    6. Select _Next_ again. The _Templates_ are displayed.
    7. Select _Finish_. You can see that a metadata extension has been generated. The annotation _ZC_FE_TRAVEL_######_ is your projection view. You can add all the UI relevant annotations for the _Travel_ entity into this file.
  6. Press CONTROL + SPACE. From the subsequent dropdown, select #CORE(annotation). You have selected #CORE as the value for the @Metadata.layer.
  7. Expand _Metadata Extensions_. You can see the newly created metadata _ZC_FE_TRAVEL_######_ extension in the _Metadata Extension_ folder.

### Result
You successfully created an ABAP CDS metadata extension for _ZC_FE_TRAVEL_######_ ABAP CDS projection view. In the upcoming exercises, you will add all the UI relevant annotations for the _Travel_ entity into this file.
## Add Columns to the List Report Table
In this exercise, you will learn how to add columns to the table displaying travels. To do so, you have to annotate the corresponding fields with the ABAP CDS @UI.lineItem annotation.
### Prerequisites
You have completed the exercise Create an ABAP CDS Metadata Extension for a Projection View in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_DF88A47CD0722287:uebung)
### Steps
  1. Open the app preview in your browser. The table is not displaying any columns.
  2. Open the _Travel_ entity projection view in ADT.
    1. You have the OData service package that you generated in a previous exercise opened in ADT.
    2. Select and double-click _ZC_FE_TRAVEL_######_ that is available within the _Data Definitions_. The projection view for the _Travel_ entity opens.
    3. Copy the following fields that you are going to use to add annotations:
       * TravelID
       * AgencyID
       * CustomerID
       * BeginDate
       * EndDate
       * BookingFee
       * TotalPrice
       * OverallStatus
       * LastChangedAt
  3. Paste all the selected fields from the projection view to the metadata extension.
    1. Double-click _ZC_FE_TRAVEL_######_ from within the _Metadata Extensions_.
    2. As shown in the following sample code, paste all the fields from the projection view of the _Travel_ entity for which you want to add the @UI.lineItem annotation.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011

{
TravelID;
AgencyID;
CustomerID;
BeginDate;
EndDate;
BookingFee;
TotalPrice;
OverallStatus;
LastChangedAt;
}

```

  4. Add the ABAP CDS @UI.lineItem one line above the field.
    1. Start typing @UI.lineItem one line above the field.
    2. Press CTRL + SPACE on your keyboard to see annotation suggestions.
    3. Select and double-click @lineItem: [{}] (annotation).
  5. Add the position property of the @UI.lineItem annotation.
    1. Press CTRL + SPACE on your keyboard.
    2. Select and double-click @position: (annotation).
    3. Enter 10 as the position value. The TravelID field will be displayed as the first column of the table.
    4. Follow these steps for each field. Ensure that you enter the position value in consecutive order for the rest of the fields. In this case, the position value for the second field is 20, for the third field it is 30, and so on.
  6. Click _Activate_ from the menu bar to save and activate your changes.
  7. Open the app preview in your browser to see all the annotated fields.
    1. Expand the _Business Services_ folder from the _Project Explorer_.
    2. Expand the option _Service Bindings_ from within the _Business Services_.
    3. Double-click _ZUI_FE_TRAVEL_######_O4_.
    4. Select _Travel_ from _Entity Set and Association_ of the _Service Version Details_ tab in the opened service binding.
    5. Select _Preview_. The app preview displays all the fields that were annotated with @UI.lineItem as table columns.
  8. Select _Go_. The table data is displayed.
  9. Select and click the first entry in the table. The object page of the selected table entry gets displayed. This object page is empty as the corresponding annotations have not been maintained yet.

### Result
You successfully added columns to the table, where all the annotated fields are displayed. You also successfully viewed the data within the table and navigated to an object page.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/a1f4aab427dc97fe450c070b41124e98ae5d5f19/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson1CreatingAListReport/exercise2AddColumnsToTheListReportTable.md).
## Add Filter Fields to the List Report
In this exercise, you will add theTravelID, AgencyID, and CustomerID fields to the filter bar of the list report.
### Prerequisites
You have completed the exercise Add Columns to the List Report Table in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B7DE9D4004B3E299:uebung)
### Steps
  1. You have the metadata extension open for the _Travel_ projection view in ADT.
  2. Annotate TravelID with @UI.selectionField.
    1. Start typing @UI.selection before the TravelID field.
    2. Select and double-click @selectionField: [{}] (annotation) from the subsequent list.
  3. Make TravelID the first filter field on the UI.
    1. Place the cursor within the curly brackets for @UI. selectionField: [{}].
    2. Select and double-click @position: (annotation) from the options.
    3. Enter 10 as the position property of the @UI.selectionField annotation. This way, TravelID becomes the first filter field on the UI.
  4. Annotate the AgencyID and CustomerID with @UI.selectionField in the same way as described for TravelID. Ensure that you enter the position value in consecutive order for the rest of the fields. In this case, the position value for the second field is 20, for the third field it is 30, and so on.
  5. Click _Activate_ from the menu bar to save and activate your changes.
  6. Open the app preview in your browser to see all the annotated filter fields.
    1. Double-click _ZUI_FE_TRAVEL_######_O4_.
    2. Select _Travel_ from the _Entity Set and Association_ of the _Service Version Details_ tab in the opened service binding.
    3. Select _Preview_. The app preview displays the _Travel ID_ , _Agency ID_ , and _Customer ID_ as filter bar fields now. The _Search_ field and _Editing Status_ are added to the filter bar by default.
  7. Select _Go_. The table data is displayed.
  8. Filter the table data from the _Agency ID_ field.
    1. Select the value help option for _Agency ID_.
    2. Choose the first item from the generated list within the _Search and Select_ tab.
    3. Select _OK_.
    4. Select _Go_ from the list report. You can see that the table data is filtered according to the filter criteria you've selected before.

### Result
You successfully added _Travel ID_ , _Agency ID_ and _Customer ID_ to the filter bar of the list report. You filtered data based on the filter criteria you had selected.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson1CreatingAListReport/exercise3AddFilterFieldsToTheListReport.md).
## Add Criticality to the Travel Status Column
In this exercise, you will add criticality color to the _Overall Status_ values. The _Overall Status_ column displays the overall status of the travel, where _O_ is open, _A_ is accepted, and _X_ is canceled. Based on the criticality colors, the accepted status is displayed in green, open status - in orange, and canceled status - in red. You will also add corresponding icons to these values.
### Prerequisites
You have completed the exercise Add Filter Fields to Your List Report in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_65FEA6919E7C0696:uebung)
### Steps
  1. The [Highlighting Line Items Based on Criticality](https://ui5.sap.com/#/topic/0d501b16e43d45d0a19ae54a3be883d3) document of SAP Fiori elements is opened. You can see the possible values for criticality.
  2. You have the metadata extension open for the _Travel_ projection view in ADT.
  3. Double-click _ZI_FE_TRAVEL_######_ from within the _Data Definitions_. The ABAP CDS view for the _Travel_ entity is opened. The _OVERALL_STATUS_ field is available in the generated view.
  4. As shown in the following sample code, add a virtual element called OverallStatusCriticality containing the mapped values of the _OVERALL_STATUS_.
Code Snippet
Copy codeSwitch to dark mode

```

123456

case OVERALL_STATUS
   when 'O' then 2
   when 'A' then 3
   when 'X' then 1
   else 0
end   as OverallStatusCriticality,

```

  5. Click _Activate_ from the menu bar to save and activate your changes.
  6. Add the newly created field to the draft table for the _Travel_ entity.
    1. Expand _Behavior Definitions_ from the _Project Explorer_.
    2. Double-click _ZI_FE_TRAVEL_######_. Click _Activate_ from the menu bar.
    3. You can see an error icon for the draft table.
    4. Select the error icon. The error message is expanded.
    5. Double-click on the message. The overallstatuscriticality field is added to the draft table of the _Travel_ entity.
  7. Click _Activate_ again from the menu bar to save and activate your changes.
  8. Add the newly created field to the projection view.
    1. Double-click _ZC_FE_TRAVEL_######_ from the _Project Explorer_.
    2. Scroll down to OverallStatus and add the OverallStatusCriticality field to the projection view.
    3. Click _Activate_ from the menu bar to save and activate your changes.
  9. Add the criticality property as OverallStatusCriticality to the @UI.lineItem annotation for the OverallStatus field.
    1. Double-click _ZC_FE_TRAVEL_######_ from within the _Metadata Extensions_ folder of _Project Explorer_. The metadata extension opens for the _Travel_ entity.
    2. Add the criticality: 'OverallStatusCriticality' property of the @UI.lineItem annotation to OverallStatus. This property is to be added right after the position property. You can annotate it as shown in the following sample code:
Code Snippet
Copy codeSwitch to dark mode

```

12

@UI.lineItem: [{position: ##, criticality: 'OverallStatusCriticality'}]
OverallStatus;

```

    3. Click _Activate_ from the menu bar to save and activate your changes.
  10. The changes in ADT are now complete. Switch to the app preview in your browser.
  11. Select _Go_. The _Overall Status_ column displays the criticality color and overall status values.

### Result
You successfully added the criticality color as well as the criticality icons for the _Overall Status_ column of the _Travel_ entity. You have viewed the changes in your app preview.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson1CreatingAListReport/exercise4AddCriticalityToTheTravelStatusColumn.md).
## Add a Description Text Instead of Codes for the Overall Status
In this exercise, you will replace the codes in the _Overall Status_ column of the list report with meaningful texts.
### Prerequisites
You have completed the exercise Add Criticality to the Travel Status Column in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_E846BBAFEAF94CB5:uebung)
### Steps
  1. In ADT, you have _Data Definitions_ open in the _Project Explorer_.
  2. Check the text provider view.
    1. Double-click _ZI_FE_TRAVEL_######_ from within _Data Definitions_.
    2. You can see that the association to the text provider view for TravelStatus is already defined.
    3. Scroll down. You can see that the association _TravelStatus is exposed in the _Travel_ CDS view.
  3. Add the text field from the text provider view to the projection view of the _Travel_ entity.
    1. Ensure that the text provider view is open for travel status by double-clicking _ZI_FE_STAT_######_.
    2. Press the F8 function key to display the text value of the view.
    3. Double-click _ZC_FE_TRAVEL_######_. The projection view of the _Travel_ entity opens.
    4. Add a new field _TravelStatus.TravelStatusText as TravelStatusText containing a travel status text to the projection view.
  4. Annotate OverallStatus with @ObjectModel.text.element in the project view.
    1. You have the projection view of the _Travel_ entity opened.
    2. Add the @ObjectModel.text.element: ['TravelStatusText'] annotation to the OverallStatus field. Note that the @ObjectModel annotation is required by the CDS runtime and is therefore added directly in the projection view and not in the metadata extension.
  5. Click _Activate_ from the menu bar to save and activate your changes.
  6. Switch to the app preview in your browser. You can see the texts in addition to the codes for _Overall Status_ column. You must now hide the codes so that only the required text is visible.
  7. Add the @UI.textArrangement annotation to display just a text without the code.
    1. Expand the _Metadata Extensions_ from the _Project Explorer_ in ADT.
    2. Double-click _ZC_FE_TRAVEL_######_. The metadata extension opens for the _Travel_ projection view.
    3. Focus on the OverallStatus line item.
    4. Add the @UI.textArrangement: #TEXT_ONLY annotation to the OverallStatus. This value ensures that only text is visible on the UI and the code appearing in brackets remains hidden.
  8. Click _Activate_ again from the menu bar to save and activate your changes.
  9. Switch to the app preview in your browser. You can now see that the codes are hidden.

### Result
You successfully added the text to the _Overall Status_ column for _Travel_ entity. You have also hidden the codes of status appearing in brackets.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson1CreatingAListReport/exercise5AddADescriptionTextInsteadOfCodesForTheOverallStatus.md).
