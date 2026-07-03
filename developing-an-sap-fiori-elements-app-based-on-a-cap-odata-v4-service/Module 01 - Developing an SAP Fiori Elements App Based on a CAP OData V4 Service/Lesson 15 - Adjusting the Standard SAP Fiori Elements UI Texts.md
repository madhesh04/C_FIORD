# Adjusting the Standard SAP Fiori Elements UI Texts

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/adjusting-the-standard-sap-fiori-elements-ui-texts_d774f6f4-4765-4ac8-8f42-ab7b75930355*

Objective
After completing this lesson, you will be able to adapt standard SAP Fiori elements UI texts.
## Replacement of Standard UI Texts
An SAP Fiori elements application generates various controls such as tables, buttons, and fields at runtime, based on the predefined templates, annotations, and settings.
SAP Fiori elements provides standard texts for UI controls. Standard texts are available in the generic framework (for example, the button texts for delete or create actions) and belong to the template components (for example, list report and object page).
However, you can replace some standard UI texts for apps that you have created with SAP Fiori elements to suit the application-specific needs.
For example, an application with a button named _Create a Travel_ improves the user experience more than a button named _Create_.
For more information about the texts that can be overwritten, see [Localization of UI Texts](https://sapui5.hana.ondemand.com/sdk/#/topic/b8cb649973534f08a6047692f8c6830d).
## Change the Standard UI Texts
In this exercise, you will adapt the standard UI texts provided by SAP Fiori elements with custom UI texts.
### Task Flow
In the Manage Travels application, you will adapt the standard UI text that appears on the Delete confirmation dialog when you try to delete multiple items.
### Prerequisites
You have completed the exercise Adjust the Object Page of the Display Customers App in the unit Getting an Overview of SAP Fiori Tools (lesson: Creating a Second App using the Application Generator).Alternatively, you can check out its solution branch: [configure-object-page-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/configure-object-page-customer-app). Note that the flexible column layout configured in the previous exercise Enable the Flexible Column Layout has been disabled for this exercise and all upcoming exercises of this training. You can keep the flexible column layout enabled if you wish.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that guides you through the list of steps below. Performing these steps allows you to follow the simulation in your trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_85652254A3B5E586:uebung)
### Steps
  1. Replace the standard UI text used in the confirmation popup for deleting several items in the list report.
    1. Open _SAP Business Application Studio_.
    2. In the _Explorer_ window, select the Projects/webapp/i18n folder.
    3. Create a new file named customTravel.properties. For that right-click on _i18n_ and select _New File_. Enter customTravel.properties.
Note
The file name must end with .properties.
    4. Add the following application-specific text to the customTravel.properties file:
Code Snippet
Copy codeSwitch to dark mode

```

1

C_TRANSACTION_HELPER_CONFIRM_DELETE_WITH_OBJECTTITLE_PLURAL=Do you really want to delete these travels?

```

Note
You can overwrite the standard UI texts provided by SAP Fiori elements with your application-specific texts. You must add the new UI text to the custom resource bundle. Use the technical key specified by SAP Fiori elements for a certain UI text. These keys are provided in the documentation of SAP Fiori elements. For more information, see [Localization of UI Texts](https://ui5.sap.com/#/topic/b8cb649973534f08a6047692f8c6830d).
    5. Register your newly created _i18n_ file in manifest.json. For that add the following code snippet to the manifest.json file under _sap.ui5_ > _routing_ > _targets_ > _TravelList_ > _options_ > _settings_ :
Code Snippet
Copy codeSwitch to dark mode

```

1

"enhanceI18n" : "i18n/customTravel.properties",

```

  2. Check the adapted UI text that appears on the _Delete_ confirmation dialog for deleting several items.
    1. Open the _Manage Travels_ application.
    2. Select the items in the _Travels_ table that you want to delete.
    3. Choose _Delete_ to delete the selected items.
#### Result
The _Delete_ confirmation dialog now appears with the adapted UI text, _Do you really want to delete these travels?_

### Result
You have replaced the standard UI text provided by SAP Fiori elements with a custom text.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/change-standard-ui-texts).
  * The solution branch is [solution/change-standard-ui-texts](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/change-standard-ui-texts).
  * You can see the code changes compared to the previous branch on [GitHub.](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/configure-object-page-customer-app..solution/change-standard-ui-texts)

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-the-general-features-of-list-reports-and-object-pages_7ee3e1d6-a7a0-3374-9696-eecf2c843a7e)
