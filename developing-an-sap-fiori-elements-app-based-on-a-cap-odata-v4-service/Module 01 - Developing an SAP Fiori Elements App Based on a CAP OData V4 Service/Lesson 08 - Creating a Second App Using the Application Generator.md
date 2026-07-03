# Creating a Second App Using the Application Generator

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/creating-a-second-app-using-the-application-generator_dddee177-70e0-43a8-a384-7fc40739e452*

Objective
After completing this lesson, you will be able to create an SAP Fiori elements app based on a CAP service and configure basic features such as table columns and form fields.
## Create the Display Customers App
In this exercise, you will create another app _Display Customers_ in the existing CAP project. This app displays the detailed information of customers. The main entity is the Passenger entity. To create the app, you will use the SAP Fiori tools - Application Generator.
This app is used in the exercises of Unit 12 Discovering the Flexible Programming Model of SAP Fiori Elements for OData V4 and Unit 13 Illustrating the Navigation Concept in SAP Fiori elements for OData V4.
Note
While there is a separate file for the annotations returned from the back end in SAP Fiori elements for OData V2, the $metadata file in SAP Fiori elements for OData V4 includes both metadata and back-end annotations.
### Prerequisites
You have completed the exercise Clone the Initial Application Project, Set Up and Run the Application in SAP Business Application Studio in the unit Getting an Overview of SAP Fiori Elements for OData V4 (lesson: Getting Started). Alternatively, you can check out its solution branch: [SAP-samples/fiori-elements-v4-cap-advanced at initial-app-state](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/initial-app-state).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_C359C30EFF6FC6BB:uebung)
### Steps
  1. Open your CAP project in SAP Business Application Studio.
  2. Select the _Menu_ icon, then _File > New Project from Template_, and then select _SAP Fiori application_ to create another app based on the same CAP service.
  3. On the _SAP Fiori application_ page, select the template _List Report Page_.
  4. On the _Data Source and Service Selection_ page, perform the following steps:
    1. From the _Data source_ dropdown, choose **Use a Local CAP Project**.
    2. From the _Choose your CAP project_ dropdown, choose **fiori-elements-v4-cap-advanced**.
    3. From the _OData service_ dropdown, choose **TravelService (Node.js)**.
  5. On the _Entity Selection_ page, perform the following steps:
    1. From the _Main entity_ dropdown, choose **Passenger**.
    2. From the _Navigation entity_ dropdown, choose **to_Booking**.
  6. On the _Project Attributes_ page, perform the following steps:
    1. In the _Module name_ field, enter **customer**.
    2. In the _Application title_ field, enter **Customers**.
    3. In the _Application namespace_ field, enter **sap.fe.cap**.
    4. In the _Description_ field, enter **Display Customers**.
    5. From the _Minimum SAPUI5 Version_ dropdown, choose the highest available version of 1.120, for example, **1.120.6.**
    6. Under _Add FLP configuration_ select _Yes_.
  7. On the _Deployment Configuration_ page, keep the suggested settings.
  8. On the _Fiori Launchpad Configuration_ page, perform the following steps:
    1. In the _Semantic Object_ field, enter **Customer**.
    2. In the _Action_ field, enter **display**.
    3. In the _Title_ field, enter **Display Passenger**.
#### Result
You can see that the _Application Information_ page appears. It displays the details of the _Display Customers_ app with useful links.
  9. Open the preview of the application in the browser.
    1. On the _Application Information_ page, select _Preview Application_.
    2. From the _projects_ dropdown, choose **watch-customer cds watch**.
  10. Navigate through the _Display Customers_ app
    1. Select _Go_. The page displays the customer details.
    2. Select the required customer to view additional information.

### Result
You have created a _Display Customers_ app utilizing the same CAP service. You have used SAP Fiori tools - Application Generator.
## Adjust the List Report of the Display Customers App
In this exercise, you will use the Page Editor provided by SAP Fiori tools. It allows you to easily configure features such as filter fields, table columns, and fields in sections for your app. This tool supports features based on annotations and manifest.json settings.
### Prerequisites
You have completed the exercise Create the Display Customers App in the unit Getting an Overview of SAP Fiori Tools (lesson: Creating a Second App Using the Application Generator).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_C34F21AEB12CB999:uebung)
### Steps
  1. Open your CAP project in SAP Business Application Studio.
  2. Select the _Menu_ icon.
  3. Select _View_ → _Command Palette..._.
  4. From the _projects_ dropdown, choose **Fiori: Open Application Info**.
  5. Choose **customer Customers**. The _Application Information_ of the _Display Customers_ app appears.
  6. Under _Pages_ , select _ListReport_. The _Page Editor_ appears.
  7. Add the filter fields in the filter bar.
    1. Under _Filter Bar_ , select the _Add_ icon corresponding to the _Filter Fields_. The _Add Filter Fields_ dialog appears.
    2. From the _Filter Field_ dropdown, choose **City** , **CountryCode_code** , and **PostalCode**.
    3. Select _Add_. The three fields are now added to the _Filter Fields_ of _PassengerList_.
    4. To change the position of the _Country Code_ field, select the move-up arrow next to the field.
  8. Delete the existing columns.
    1. Under _Tables_ , expand _Columns_.
    2. Select the Delete icon corresponding to the required column. The _Delete Confirmation_ dialog appears.
    3. Select _Delete_.
  9. Add new columns.
    1. Select the Add icon corresponding to _Columns_.
    2. Choose **Add Basic Columns**. The _Add Basic Columns_ dialog appears.
    3. From the _Columns_ dropdown, select the required columns.
    4. Select _Add_.
  10. To view the annotations of the _City_ column, select _Navigate to source code_. You can see that a new @UI.LineItem annotation is added by the tool for the selected columns.
  11. Launch the preview of the application in a browser window.
    1. In the left pane, under _Projects_ , right-click on _fiori-elemens-v4-cap-advanced_.
    2. Select _Open in integrated Terminal_. The _Terminal_ appears.
    3. Enter cds watch.
    4. Select _Open in a New Tab_. The _Welcome to @sap/cds Server_ page appears.
    5. Under _Web Applications_ , select **/customer/webapp/index.html**. The _Display Customers_ app appears in the browser window.
    6. Select _Go_.
#### Result
You can see the newly added filter fields and the columns in the app.
  12. To view the $metadata file of the service, on the _Welcome to @sap/cds Server_ page, under _Service Endpoints:_ , select _$metadata_.
#### Result
The $metadata file of the service opens. Here, you can find the metadata information and all annotations of your CAP project in XML format.

### Result
You have learned how to add filter fields and columns to your application. You have also seen the $metadata file which contains the metadata and annotations of the service.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/generate-and-adjust-list-report-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/generate-and-adjust-list-report-customer-app).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/initial-app-state..solution/generate-and-adjust-list-report-customer-app).

## Adjust the Object Page of the Display Customers App
In this exercise, you will continue working with the Page Editor.
You will configure the object page of the _Display Customers_ app. The Application Generator adds some fields to the _General Information_ section of the object page by default. You will delete the technical fields that are not needed and change the sequence of the remaining fields on the UI. Additionally, you will create a header section and add the most important information such as a telephone number and email address of the customer.
### Prerequisites
You have completed the exercise Adjust the List Report of the Display Customers App in the unit Getting an Overview of SAP Fiori Tools (lesson: Creating a Second App Using the Application Generator). Alternatively, you can also check out its solution branch: [solution/generate-and-adjust-list-report-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/generate-and-adjust-list-report-customer-app) .
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_C3F9F54A856B37B3:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. In the left pane, select Projects\app\customer.
  3. Right-click on customer.
  4. Select _Show Page Map_. The _Page Map_ appears.
  5. On the _Object Page_ , select the _Edit_ icon. The object page structure appears.
  6. Add _FullName_ , _EmailAddress_ , and _PhoneNumber_ to an object page header section.
    1. Under _Header_ , select the Add icon corresponding to the _Header Sections_.
    2. Choose **Add Form Section**. The _Add Form Section_ dialog appears.
    3. In the _Label_ field, enter **Contact Details** as the name of the header.
    4. Select _Add_.
    5. Expand _Contact Details_.
    6. Expand _Form_.
    7. Select the _Add_ icon corresponding to the _Fields_.
    8. Choose **Add Basic Fields**. The _Add Basic Fields_ dialog appears.
    9. From the _Fields_ dropdown, select the fields to add to the header section.
    10. Click _Add_.
#### Result
You have added a header section and the three fields to it.
  7. Under _Sections_ , expand _General Information_.
  8. Expand _Form_.
  9. Remove the technical fields (_CreatedBy_ , _ChangedOn_ , and _ChangedBy_) from _Sections_.
    1. Select a field to be deleted.
    2. Select the _Delete_ icon. The _Delete confirmation_ dialog appears.
  10. To change the sequence of the fields, select the move-up or move-down arrows next to the field.
  11. To open the source code, select the _Navigate to source code_ icon next to the _Street_ field. The annotations.cds file opens.
#### Result
You can see that the Page Editor has added the records to the @UI.FieldGroup annotation for the fields you've added to the _General Information_ section.
  12. To see the annotation created for the header section, select the _Navigate to source code_ icon next to _Contact Details_. The annotation.cds file opens.
#### Result
You can see the @UI.HeaderFacets annotation added by the Page Editor to the _Passenger_ entity.
  13. Define the header name.
    1. Select _Header_.
    2. In the right pane, under the _Header_ section, in the _Type Name_ field, enter **Customer** as the name of the header.
    3. Select _Edit in source file_.
    4. Select _Apply_.
    5. In the _Type Name Plural_ field, enter **Customers** as the title of the list report table.
    6. Select _Edit in source file_.
    7. Select _Apply_.
    8. Under the _Title_ field, from the dropdown, choose **FullName**.
    9. To view the source code, select _Edit in source file_ next to _FullName_.
  14. Open the _Display Customers_ app in the browser window.
    1. In the _Display Customers_ app, select _Go_. The page displays the list of customers.
    2. Select any customer.
#### Result
You can see the full name of the customer as the title of the object page.

### Result
You have learned to configure the object page using the Page Editor.
### Next Steps
For more information, see [Configure Page Elements](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/047507c86afa4e96bb3d284adb9f4726.html).
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/configure-object-page-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/configure-object-page-customer-app).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/generate-and-adjust-list-report-customer-app..solution/configure-object-page-customer-app).

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/getting-an-overview-of-sap-fiori-tools_291a80e6-e9b5-3b6a-88be-9dac06a590f1)
