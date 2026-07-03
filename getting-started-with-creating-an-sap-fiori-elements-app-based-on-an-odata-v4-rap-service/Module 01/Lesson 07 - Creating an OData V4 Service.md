# Creating an OData V4 Service

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/creating-an-odata-v4-service*

Objective
After completing this lesson, you will be able to generate the RAP artifacts using the ABAP generator class, publish the service, and preview the application in the browser.
## ABAP RESTful Application Programming Model (RAP)
ABAP RESTful Application Programming Model (in short RAP) is the evolutionary successor of the ABAP Programming Model for SAP Fiori. RAP is a programming model for efficient development of SAP HANA-optimized OData services in SAP BTP ABAP Environment and SAP S/4HANA, on premise as well as in the cloud.
RAP consists of a set of concepts, tools, languages, and powerful frameworks that help developers to build innovative, cloud-ready SAP Fiori applications, local and Web APIs. Developers can easily extend SAP standard applications on the ABAP platform, in the cloud as well as on premise.
RAP provides a standardized development flow based on Core Data Services (CDS), the ABAP language, and business services in the modern, Eclipse-based ABAP Development Tools (ADT).
You can develop and model different types of services, local APIs, and business events using RAP.
CDS enables developers to work in the ABAP layer with ABAP Development Tools, while the code execution is pushed down to the database.
For RAP availability, check [State-of-the-Art ABAP Development with the ABAP RESTful Application Programming Model (RAP)](https://pages.community.sap.com/topics/abap/rap).
### Further Reading
  * [ABAP RESTful Application Programming Model](https://help.sap.com/docs/ABAP_PLATFORM_NEW/fc4c71aa50014fd1b43721701471913d/289477a81eec4d4e84c0302fb6835035.html)
  * [Acquiring Core ABAP Skills](https://learning.sap.com/learning-journeys/acquire-core-abap-skills)

## RAP Development Artifacts
Watch the video to get an overview of the most important RAP artifacts.
## Generate RAP Artifacts for Your Service Using the ABAP Generator Class
The focus of this course is on developing SAP Fiori elements apps, rather than the creation of an OData service. For this purpose, a generator was developed for the course that creates all the required RAP development artifacts for you. In this exercise, you will do the following:
  * Open ABAP perspective in Eclipse.
  * Execute the ABAP generator class _ZDMO_CL_FE_TRAVEL_GENERATOR_ that will generate RAP development artifacts in a package with a unique ID.
  * Add the generated package to the favorite packages in the project explorer of the ABAP view.
  * Execute the ABAP data generator class ZFE_DATA_GENERATOR_##### where ##### is the unique ID of the previously generated package.

### Prerequisites
You have completed the exercise Set Up Development Environment in this unit (lesson: Getting Started).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_993CFB0731DF0586:uebung)
### Steps
  1. Open ADT.
  2. Open the _ABAP_ perspective in ADT.
    1. Select _Window_ from the menu bar.
    2. Choose _Perspective_ from the dropdown list.
    3. Choose _Open Perspective_ from the subsequent list.
    4. Choose _Other_ from the list of _Open Perspective_.
    5. Select _ABAP_ from the _Open Perspective_ dialog.
    6. Select _Open_ from the bottom of the _Open Perspective_ dialog. The _ABAP_ perspective is opened. You can see the corresponding icon in the top right corner of the ADT.
  3. Open the _ABAP_ generator class _ZDMO_CL_FE_TRAVEL_GENERATOR_.
    1. Select _Open ABAP Development Object_.
    2. Enter **ZDMO_CL_FE_TRAVEL_GENERATOR** as the search string name of the _ABAP_ generator class in the _Open ABAP Development Object_ dialog.
    3. Select _OK_ from the bottom of the _Open ABAP Development Object_ dialog. The _zdmo_cl_fe_travel_generator_ class opens.
  4. Open the _Console_ view.
    1. Select _Window_ from the menu bar.
    2. Choose _Show View_ from the dropdown list.
    3. Choose _Other_ from the _Show View_ option list.
    4. Expand the _General_ menu from the subsequent _Show View_ dialog.
    5. Choose _Console_ from the expanded view.
    6. Select _Open_ from the bottom of the _Show View_ dialog. The _Console_ view opens.
  5. Generate a package with a unique ID.
    1. Right-click _Global Class_ tab of the _ZDMO_CL_FE_TRAVEL_GENERATOR_ string.
    2. Choose _Run As_ from the subsequent menu.
    3. Choose _1 ABAP Application (Console) F9_ from the subsequent menu. After a minute or so, the package with a unique ID gets generated, and you can see the package name within the ABAP console.
    4. Use the keyboard copy option CTRL+C to copy the name of the generated package.
  6. Add the generated package to your _Favorite Packages_.
    1. Go to the _Project Explorer_ tab.
    2. Expand the available folder. Note that this folder may differ for everyone.
    3. Right-click the _Favorite Packages_ option.
    4. Select _Add Package_ from the subsequent list.
    5. Paste the name of the generated package in the _Select an ABAP Package_ dialog box.
    6. Select _OK_ from the bottom of the _Select an ABAP Package_ dialog box.
  7. View the generated RAP artifacts.
    1. Expand your _Favorite Packages_.
    2. Expand the _ZFE_TRAVEL_######_ package from the subsequent list of packages. Note that the package ID is unique for everyone.
    3. You can see the generated RAP artifacts.
  8. Open the _CDS_ view for a travel entity.
    1. Expand _Core Data Services_ from the generated RAP artifacts list.
    2. Expand _Data Definitions_.
    3. Double-click _ZI_FE_TRAVEL_######_.
  9. Execute the ABAP class ZFE_DATA_GENERATOR_##### to generate application data for your RAP service.
    1. Expand the _Source Code Library_ folder in your package.
    2. In its _Classes_ sub folder you can see the class called _ZFE_DATA_GENERATOR_#####_ where ##### is the unique ID of your package.
    3. Right-click the class name and select from the context menu _Run As- > ABAP Application (Console)_. The corresponding DB tables are filled with the application data.

### Result
You have successfully generated a package with a unique ID containing RAP artifacts. You have also added the package to the list of your _Favorite Packages_. You have generated the application data for your RAP service.
## Publish the OData V4 Service
In this exercise, you will learn how you can publish your OData V4 service.
### Prerequisites
You have completed the exercise Generate RAP Artifacts for your Service using the ABAP Generator Class in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_4C2D3A5826681E9E:uebung)
### Steps
  1. You have your generated package with the unique ID containing RAP artifacts open in ADT.
  2. Check the service definition that you generated using the _ABAP_ generator class in the previous exercise.
    1. Find your _Favorite Packages_ and expand _Business Services_ within the _ZFE_TRAVEL_######_.
    2. Expand _Service Definitions_.
    3. Double-click _ZFE_TRAVEL_######_ to open the service definition.
  3. Open the service binding for your OData V4 service.
    1. Expand _Service Bindings_.
    2. Double-click _ZUI_FE_TRAVEL_######_O4_ from the expanded list.
  4. Select _Publish_ to publish the service.
Note
If the service binding is already published, skip this step.

### Result
You successfully published an OData V4 service. Once published, you can see the _Service URL_ and the _Entities and Associations_ exposed by the service.
## Preview Your Service in ABAP Development Tools (ADT)
In this exercise, you will preview the service that you have already published in the previous exercise in a browser.
### Prerequisites
You have completed the exercise Publish the OData V4 Service in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_CBCDDB1143AFCB82:uebung)
### Steps
  1. You have the OData service package that you generated in a previous exercise opened in ADT.
  2. Ensure that the _Service Binding: ZUI_FE_TRAVEL_######_O4_ is displayed.
  3. Select _Travel_ from the _Entity Set and Association list_ of _Service Version Details_.
  4. Select _Preview_ once _Travel_ is highlighted. The preview of the service gets launched in your browser.

### Result
You successfully viewed filter bar and a table. Note that you were not able to see any columns, as the corresponding annotations have not been added. You will add filter bar fields and table columns in the upcoming exercises.
## Get an Overview of the Features That Will Be Implemented in the Training
### Watch the Simulation
Here, you will explore the features that you will implement in this training.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_425039ABD4E93D9D:uebung)
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/getting-an-overview-of-abap-restful-application-programming-model)
