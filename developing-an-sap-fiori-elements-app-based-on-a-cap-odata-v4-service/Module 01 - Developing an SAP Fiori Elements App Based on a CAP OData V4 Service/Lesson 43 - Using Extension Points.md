# Using Extension Points

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/using-extension-points_d613eea6-2548-4db3-a7c1-2ef9b52653b5*

Objective
After completing this lesson, you will be able to integrate front-end components that are not available with annotations.
## Extension Points
SAP Fiori elements framework is based on SAPUI5 technology. You may be familiar with the [Model View Controller](https://sapui5.hana.ondemand.com/sdk/#/topic/91f233476f4d1014b6dd926db0e91070.html) concept in SAPUI5.
In the _view_ , you can define the UI controls to be used in the UI.
The _controller_ contains methods that define how models and views interact.
A _model_ holds the data and provides methods to retrieve the data from the database and to set and update the data.
Thus, in a freestyle SAPUI5 app, you have to define the views and implement the methods needed in the controllers, for example, an event handler for a button if a user selects a button.
SAP Fiori elements framework generates views at runtime based on the predefined floorplans and your app-specific metadata and annotations. Thus, in the standard SAP Fiori elements applications, you do not have any static views or controllers in your project in the development environment.
If you use the extension points, a static xml fragment has to be added to the webapp/ext folder of your project. If needed, a controller will also be added. The Page Editor can generate both files, including an ext folder if not present yet.
Extension points are containers provided by SAP Fiori elements framework, which hook into the standard SAP Fiori elements runtime. There, you can add your specific UI controls or behaviors using the standard SAPUI5 programming model based on HTML5 and JavaScript.
In custom extensions, you can provide features that SAP Fiori elements does not offer, for example, process diagrams or maps.
Note: you can find the list of all extension points provided by SAP Fiori elements at [Overview of Extension Points](https://sapui5.hana.ondemand.com/test-resources/sap/fe/core/fpmExplorer/index.html#/customElements/customElementsOverview)
## Add a Custom Column to the Table on the Object Page of the Manage Travels App
If the standard floorplans don't quite fit, you can use the extension points provided by SAP Fiori elements. There you can add your own code.
In this exercise, you will add a custom column to the _Booking Supplements_ table on the subobject page. It will help the users choose when to serve their in-flight meal. To do this, you will create a custom column and add the SegmentedButton control to it.
For more information, see the API reference at [sap.m.SegmentedButton - API Reference - Demo Kit - SAPUI5 SDK (ondemand.com)](https://sapui5.hana.ondemand.com/#/api/sap.m.SegmentedButton%23overview).
### Task Flow
You will first add a new property to your CAP data model to ensure the UI-side selection is persisted in the back end. Then, you will use the Page Editor to add a custom column in the UI.
Next, you will add the SegmentedButton control. Finally, you will implement a method in the controller extension for updating the new property.
For more information and samples, see [sap.m.SegmentedButton - Samples - Demo Kit - SAPUI5 SDK (ondemand.com)](https://sapui5.hana.ondemand.com/#/entity/sap.m.SegmentedButton).
### Prerequisites
You have completed the exercise Add the Validation for the Field Agency on the Object Page in the unit Applying Dynamic Field Control and Validating User Input on the Object Page (lesson: Verifying the User Input). Alternatively, you can check out its solution branch: [solution/add-validation-for-field-agency-on-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-validation-for-field-agency-on-op).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2AF481F33141F497:uebung)
### Steps
  1. Add a new property to the Booking entity which will persist the choice of the meal time.
    1. Open the db/schema.cds file.
    2. Add the following code snippet at the end of the file:
Code Snippet
Copy codeSwitch to dark mode

```

1

entity MealOptionDeliveryPreference: CodeList { key code : String enum { SoonAfterTakeoff = 'S'; Midflight = 'M'; Late = 'L'; } default 'M' };

```

    3. Add a new property DeliveryPreference to the BookingSupplement entity which is an association to the previously defined MealOptionDeliveryPreference entity. It will persist the user choice.
Code Snippet
Copy codeSwitch to dark mode

```

1

DeliveryPreference : Association to MealOptionDeliveryPreference;

```

  2. Create a new file sap.fe.cap.travel-MealOptionDeliveryPreference.csv in the db/data folder and add the following code snippet to it:
Code Snippet
Copy codeSwitch to dark mode

```

1

code;name;descr S;SoonAfterTakeoff;Delivery as early as possible after the take-off M;Midflight;Not too early not too late L;Late;Late in the flight while still allowing you to finish the meal or drink before the landing

```

  3. Add a custom column to the _Booking Supplements_ table on the subobject page using the Page Editor.
    1. Open the Page Editor for the travel_processor app.
    2. Select _Booking Object Page_ > _Booking Supplements_ > _Table_ > _Columns_ > _Add Custom Column_.
    3. Add _Serving Time of Meals_ to the header text of the new column.
    4. Select the globe icon and _Apply_ to add localization.
    5. Add ServingTimeOfMeals to the _Column Fragment Name_.
    6. Choose _Product Price_ from the _Anchor Column_ dropdown menu.
    7. Select _True_ in _Generate Event Handler Controller_.
    8. A new custom column _Serving Time of Meals_ has been added to the _Columns_ section.
  4. Add the XML code for the custom column content to the app/travel_processor/webapp/ext/fragment/ServingTimeOfMeals.fragment.xml. This file has been generated by the Page Editor and includes some initial XML code.
    1. Substitute the XML code with this code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m"> <SegmentedButton core:require="{handler: 'sap/fe/cap/travel/ext/fragment/ServingTimeOfMeals'}" id="SB1" selectionChange="handler.onSelectionChange" enabled="{ui>/isEditable}" selectedKey="{= ${DeliveryPreference_code}}"> <items> <SegmentedButtonItem id="_IDGenSegmentedButtonItem1" text="{i18n>early}" key="S" /> <SegmentedButtonItem id="_IDGenSegmentedButtonItem2" text="{i18n>mid}" key="M" /> <SegmentedButtonItem id="_IDGenSegmentedButtonItem3" text="{i18n>late}" key="L" /> </items> </SegmentedButton> </core:FragmentDefinition>

```

As you can see in the API documentation, sap.m.SegmentedButton control has an aggregation items of type sap.m.SegmentedButtonItem. The latter is derived from the sap.ui.core.Item and you can use any of its artifacts, like properties. In the code snippet above you have used its key and text properties.
You can use a selectionChange event of sap.m.SegmentedButton in the XML fragment and bind it to the method which you will implement in your custom controller. The method will update the property in the back end after the selection changes on the UI side.
You can see two properties of sap.m.SegmentedButton being used in the XML fragment: enabled and selectedKey. The selectedKey property of sap.m.SegmentedButton is bound to the value of DeliveryPreference_code you introduced in the back end. It influences which key of the segmented button is selected.
Enabled is another property of the sap.m.SegmentedButton. In the code snippet above the enabled, control property is bound to the value of the ui model's property isEditable. The Ui model is an SAPUI5 JSON model containing UI information. It is managed by SAP Fiori elements. You are not allowed to change its values but you may access it from your custom fragments and custom controllers and you may evaluate its public property isEditable. If it is set to true, the application is in edit mode. In this case, the segmented button is enabled.
  5. In the file explorer, open the app/travel_processor/webapp/i18n/i18n.properties file and paste the texts for the threeSegmentedButtonItems you previously added to the XML fragment.
Code Snippet
Copy codeSwitch to dark mode

```

1

#XCOL: Custom column header text servingTimeOfMeals=Serving Time of Meals #XTIT: Delivery preference of the Meal during the flight deliveryPreference=Delivery Preference #XTIT: Early time of meal delivery during the flight early=early #XTIT: Mid time of meal delivery during the flight mid=mid #XTIT: Later time of meal delivery during the flight late=late

```

  6. Open app/travel_processor/webapp/ext/fragment/ServingTimeOfMeals.js and paste this code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

sap.ui.define([ "sap/m/MessageToast" ], function(MessageToast) { 'use strict'; return { onSelectionChange: function(oEvent) { var sNewDeliveryPreferenceCode = oEvent.getParameter("item").getKey(); var oSegmBtn = oEvent.getSource(); oSegmBtn.getBindingContext().setProperty("DeliveryPreference_code", sNewDeliveryPreferenceCode); } }; });

```

The method onSelectionChange will be called once the segmented button selection changes.
  7. Switch to the app. You can see a new column in the _Booking Supplements_ table. It is read-only in the display mode.
    1. Navigate to the object page to change to the _Edit_ mode.
    2. Select _Edit_ on the top right of the object page.
    3. Select the first row in the _Bookings_ table.
    4. Select "early" for the first meal and "late" for the second meal.
    5. Select _Apply_ on the bottom right of the subobject page.
    6. Select _Save_ on the object page.
  8. Select the first row in the _Bookings_ table. Notice that your selection of meal times has been saved and you have added a custom column to the subobject page table.
The Page Editor helps you position your custom control on the page by selecting an anchor element and positioning your custom element in respect to it (before or after). The Page Editor adds the corresponding settings to the manifest.json file. The code snippet below has been generated by the Page Editor.
Code Snippet
Copy codeSwitch to dark mode

```

1

 "controlConfiguration": { "to_BookSupplement/@com.sap.vocabularies.UI.v1.LineItem": { "columns": { "ServingTimeOfMeals": { "header": "{i18n>servingTimeOfMeals}", "position": { "anchor": "DataField::Price", "placement": "After" }, "template": "sap.fe.cap.travel.ext.fragment.ServingTimeOfMeals" } } } }

```

### Result
You have learned how to use extension points in your SAP Fiori elements applications.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-custom-column-to-table-on-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-custom-column-to-table-on-op).
  * You can find the link to the direct comparison of the branch to the previous one on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-validation-for-field-agency-on-op..solution/add-custom-column-to-table-on-op).

### Next Steps
For more information, see
  * [Example: Adding Columns to a Responsive Table in the List Report](https://sapui5.hana.ondemand.com/#/topic/28e95702b5854b938ac51c4bc2d078ab)
  * [Extension Points for Tables](https://sapui5.hana.ondemand.com/#/topic/d525522c1bf54672ae4e02d66b38e60c)
