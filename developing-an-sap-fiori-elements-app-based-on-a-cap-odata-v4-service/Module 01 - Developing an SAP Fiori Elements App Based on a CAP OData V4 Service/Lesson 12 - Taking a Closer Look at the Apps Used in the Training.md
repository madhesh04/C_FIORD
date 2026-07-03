# Taking a Closer Look at the Apps Used in the Training

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/taking-a-closer-look-at-the-apps-used-in-the-training_fb813e5d-7cec-4719-b192-a71a826314b8*

Objective
After completing this lesson, you will be able to discover essential apps and features in your training journey.
## Discover the Manage Travels App
In this lesson, you will explore the _Manage Travels_ app that is mainly used throughout the training, in addition to the _Display Customers_ app. Furthermore, you will also gain insights into the structure of the CAP project, which you've previously cloned. This exploration involves taking a closer look at the files where you will extend your data model or implement the back-end methods in the following exercises. You will also see the files of your SAP Fiori elements apps.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2491F5D4E50E3BE:uebung)
Note
To launch the app preview in the browser window, select either cds run or cds watch. In the following exercises, you will use cds watch to immediately update the preview after making some changes in the project.
## Get to Know the Structure of the CAP Project Used in the Training
### Usage Scenario
In this lesson, you will examine the structure of the CAP project that you've previously cloned.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_5BCD7458EF646C95:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. In the Explorer view, under _Projects_ , expand _fiori-elements-v4-cap-advanced_.
  3. Expand _app_. You can see the two folders, _customer_ and _travel_processor,_ corresponding to the two apps, _Display Customer_ and _Manage Travels_ , respectively.
  4. Explore the _customer_ folder.
    1. Expand _customer_.
    2. To see the application files of SAP Fiori elements, expand _webapp_.
    3. Select _i18n_ → _i18n.properties_. The _i18n.properties_ file opens. It contains the UI texts for translation.
    4. Select _localService_ → _metadata.xml_. The _metadata.xml_ file opens. It contains the metadata information of the service in XML format.
    5. Select _test_. The _test_ folder contains the initial files for the tests. You need to implement the tests if you have added some custom JavaScript code or custom controls to your SAP Fiori elements application.
    6. Select _manifest.json_. The _manifest.json_ file is the main configuration file for your app settings.
    7. Select _annotations.cds_. The annotations.cds file opens. It contains the annotations in CDS format.
  5. Explore the _travel_processor_ folder.
    1. Expand _travel_processor_.
    2. Expand _webapp_. The webapp folder also has the same structure as that of the _customer_ folder.
    3. Select _manifest.json_. The _manifest.json_ file is the main configuration file for the _Manage Travels_ app.
    4. Select _capabilities.cds_. In the capabilities.cds file, you can see that the service is draft-enabled and that semantic keys are specified in the file.
    5. Select _field-control.cds_. The field-control.cds file contains the annotations that influence the availability and editability of the fields and actions on the UI.
    6. Select _labels.cds_. The labels.cds file contains the label annotations for the fields.
    7. Select _layouts.cds_. The layouts.cds file contains the main UI annotations such as the @UI.Identification and @UI.LineItem.
    8. Select _value-helps.cds_. The value-helps.cds file contains the value help definition for the _Manage Travels_ app. It also has the value help definitions of the filter bar and the table fields in Edit mode.
    9. Select _service.cds_. The service.cds file contains the references to all files containing CDS annotations.
  6. Explore the data modeling of the CAP service.
    1. Select _db_ → _schema.cds_. The schema.cds file contains the definition of the entities and the relations between them. Some of them are associated to other entities such as TravelStatus, to_Agency, to_Customer, and to_Booking. Some of the entities are defined in the master-data.cds file.
    2. Select _master-data.cds_. The master-data.cds file contains the definition of master data entities such as _Airline_ , _Airport_ , and _Supplement_.
    3. Select _common.cds_. In the common.cds file, sap.common.Currencies is extended and the technical fields are mapped. These technical fields are added to the entities which are denoted as managed.
    4. Select _data_ → _sap.fe.cap.travel-Travel.csv_. The data folder contains CSV files with initial data for each entity of the service. For example, the sap.fe.cap.travel-Travel.csv file contains all fields of the Travel entity.
    5. Expand _srv_. The srv folder contains the entities and actions for the services.
    6. Select _travel-service.js_. The _travel-service.js_ file contains the Node.js methods for the service. These methods are invoked during runtime by CAP.
  7. Start the CDS server.
    1. In the Explorer view, under _Projects_ , right-click on _fiori-elements-v4-cap-advanced_.
    2. Select _Open in Integrated Terminal_. The _Terminal_ view opens.
    3. Enter **cds watch**.
    4. Select _Open in a New Tab_. The _Welcome to @sap/cds Server_ appears.
    5. Select _Service Endpoints_ → _/processor_ → _$metadata_. The $metadata file opens in XML format. It contains the metadata of your service as well as the annotations. You can also see the definition of the Travel entity in XML format.

### Result
In this exercise, you have examined the structure of the CAP project you are going to use in this training. You have seen the data modeling, which includes entities and associations, as well as the service layer where entities and actions are exposed, and the necessary Node.js methods are implemented.
​Each app requires at least one annotation file. In the CAP projects, the annotations are typically written in CAP CDS format. These CDS annotations are then transformed into OData annotations in XML format and are available, along with the metadata information, in the generated $metadata file. The SAP Fiori elements framework utilizes the data from the $metadata file to generate the user interfaces (UIs).
### Next Steps
You can also create a data model using the low-code functionality. For more information, see [Create a Data Model and Expose It as a Service](https://developers.sap.com/tutorials/appstudio-lcap-create-db-service.html#b5d3a126-e7bf-4cc3-8447-808969888b20).
## Get an Overview of the Features Which Will Be Implemented in the Training
### Explore the Features Which will Be Implemented
You will explore the features that you will implement in the _Manage Travels_ and _Display Customers_ apps.
### Watch the Simulation
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_391C705BBB699490:uebung)
[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/understanding-sap-fiori-elements-templates_b0bacf78-6cda-3d60-bddf-8f7b015f315e)
