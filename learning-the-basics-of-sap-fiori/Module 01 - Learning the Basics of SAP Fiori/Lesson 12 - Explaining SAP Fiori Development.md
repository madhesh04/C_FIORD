# Explaining SAP Fiori Development

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/explaining-sap-fiori-development_e7330fcf-e183-495b-8485-1b53b23595d6*

Objectives
After completing this lesson, you will be able to:
  * Explain ABAP programming models.
  * Use ABAP Development Tools.
  * Explain SAP Fiori elements.

## ABAP Programming Models
The three phases of the development of an SAP Fiori application are data modeling, service building, and UI development.
Watch the video explaining the key steps of SAP Fiori development.
![A system architecture diagram showing a programming model introducing code-based implementation with SAPUI5 in FLP on top connecting via HTTPS to BSPs and SAP Gateway in FES connecting via RFC to SAP Gateway, DPC/MPC, ABAP logic, and application table in S4H.](../images/2d26c41347f7e1fe.png)
Since SAP NetWeaver 7.0, it is possible to use SAP Gateway to build OData services that access arbitrary business data through existing ABAP frameworks (function modules, RFC, BAPI, SPI…). This can either be done through service development or through service generation using _SAP Gateway Service Builder_.
For the UI part, SAPUI5 apps are deployed as Business Server Pages (BSP) in the FES and run in the _SAP Fiori launchpad (FLP)_.
![A system architecture diagram showing the previous programming model extended by code-based implementation with SADL, CDS view, and calculation view in S4H.](../images/2ef9e6358f8c824f.png)
Since SAP NetWeaver 7.40, it is possible to use CDS views as data source. SAP Gateway uses the Service Adaptation Definition Language (SADL) to access CDS views. There, everything is defined to **read** data from application tables, so no additional (ABAP) code must be written by any developer.
Requests that perform changes can be implemented using code-based implementation of the create, update, and delete method in the data provider extension (DPC_EXT) class. In addition since 7.50, CDS views referenced as data source in the _SAP Gateway Service Builder_ can be combined with code-based implementation.
![A system architecture diagram showing the previous programming model extended by SADL with managed runtime and draft table in S4H.](../images/fde446d6434c245b.png)
Since SAP NetWeaver 7.51 SP01, a first managed runtime is supported that leverages the Business Objects Processing Framework (BOPF). The business objects (ABAP classes) are generated based on appropriate annotations in the CDS view. They are implemented using code-based implementations to call existing APIs performing change requests to business data. This model is called ABAP Programming Model for SAP Fiori (CDS-based BOPF).
Since ABAP Platform 7.54, an enhanced managed runtime is available that leverages CDS behaviors. Therefore, the business objects of CDS-based BOPF are replaced by behavior definitions (ABAP interfaces) and behavior implementations (ABAP classes). This model is called ABAP RESTful Application Programming Model (RAP).
Code-based implementation can still be used to call existing custom code or if CDS views are not suitable to solve the business scenario.
Note
For more information about this topic, see:
  * Acquiring Core ABAP Skills (Learning Journey)
<https://learning.sap.com/learning-journeys/acquiring-core-abap-skills>
  * Introduction to Application Programming on SAP S/4HANA (Classroom Training)
<https://training.sap.com/course/s4dev>

## ABAP Development Tools for On-Premise
![Screenshot of ABAP Development Tools in Eclipse with guides on managing projects, opening perspectives, managing perspectives, and views.](../images/6d0aab193d8c8ff0.png)
The _ABAP Development Tools (ADT)_ are a collection of plug-ins for _Eclipse_ supporting development projects reaching beyond pure ABAP. _Eclipse_ is a development environment, originally conceived for Java, that offers a framework for which vendors - including SAP - can provide plug-ins that support development in any given language.
Because different languages and platforms have different requirements, developers need a different set of tools within the same Eclipse window. Such a set of tools is called a perspective combining views and functions suiting for one purpose. There are views showing the source code, structural outline, properties, errors, and many more. Every perspective can be customized, new ones can be created, or existing ones can be reset to the last saved state.
The development objects or source code is organized in projects. Each project defines the frame for the (development) task. The files comprising this task are saved in a local folder.
![Step-by-step guide for installing ABAP Development Tools for Eclipse using the specified URL in Eclipse. Left shows navigating to Install New Software, right shows selection options in dialog box.](../images/2ce442fa423bf67c.png)
To install the plug-ins of ADT, proceed as follows:
  1. Get an installation of _Eclipse_ from <https://www.eclipse.org/downloads/packages> (for example, _Eclipse IDE for Java Developers_).
  2. In _Eclipse_ , choose _Help_ → _Install New Software..._.
  3. Enter the URI <https://tools.hana.ondemand.com/latest>.
  4. Choose **Enter** to display the available features.
  5. Select _ABAP Development Tools_ and choose _Next_.
  6. On the next wizard page, you get an overview of the features to be installed. Choose _Next_.
  7. Confirm the license agreements and choose _Finish_ to start the installation.

### ABAP Project
An ABAP project is like any other project in _Eclipse_ a folder with files comprising the development task. For ABAP these are the connection information to an ABAP system. ABAP is a server language, so all source code is saved in an ABAP repository of the ABAP platform.
Watch the video to see how to create ABAP project in ABAP development tools.
Settings
The developer needs suitable user authorizations to work via ADT in an ABAP system. A list of roles and authorization objects is available in the following guide:
<https://help.sap.com/doc/2e65ad9a26c84878b1413009f8ac07c3/202210.000/en-US/config_guide_system_backend_abap_development_tools.pdf>
To enable ABAP developers to share HTTP links between themselves, activate the /sap/bc/adt ICF service. The receiver of the link can then render the target development object in his or her default Web browser.
To make documentation available to ABAP developers connected to an AS ABAP **lower** 7.55, activate the following ICF-services:
  * /sap/bc/abap/docu
  * /sap/bc/abap/toolsdocu
  * /sap/public/bc/abap/docu
  * /sap/public/bc/abap/toolsdocu

![Screenshot of an ABAP project in ADT highlighting development objects, editor, outline, and transports.](../images/6b9cf4b532c2bb3d.png)
Expanding the _System Library_ in an ABAP project allows direct access to all development objects of an ABAP repository. Especially when accessing an SAP S/4HANA system, this can be quite overwhelming. Therefore, the developer can define favorite packages and objects in an ABAP project.
The _Open ABAP Development Object_ button provides a simple search for development objects based on their names. By choosing a development object from the list, it is opened in the suitable editor and connected views like _Outline_ or _Problems_.
Many more views allow additional information around developing ABAP. One important one is the _Transport Organizer_ view to open assigned transport requests or create new ones.
## Development Paradigm Shift
![Diagram showing ABAP Platform working on SAP HANA with most calculation taking place on ABAP Platform \(data to code\) versus most calculation taking place on SAP HANA \(code to data\).](../images/f95fce79daa99da1.png)
SAP HANA is more than just a database. SAP HANA can perform calculations on a data level much faster than any previous technology, including ABAP programs. In the SAP Business Suite, the data was brought to the code. It was read from the database and processed in ABAP. With SAP HANA, it is more efficient to bring the code to the data, by pushing down calculations from the ABAP Platform in SAP HANA and only returning the results.
![ABAP CDS view in S4H deployed as database view in DB, AMDP in S4H deployed as stored procedure in DB, CTS in S4H acting as lifecycle management.](../images/f5f593e7b3d5ac16.png)
Moving calculations to the database to benefit from its features is not new to SAP HANA. Stored procedures could be used previously for calculations in many databases. However, they were rarely used in ABAP. They only run in the database they are developed in and are not transportable. With SAP S/4HANA, the ABAP repository was extended with two new database objects: ABAP Core Data Services (CDS) Views and ABAP Managed Database Procedures (AMDP). ABAP CDS Views are deployed as SAP HANA views in the SAP HANA Database (HDB), and the AMDPs are deployed as stored procedures. This is comparable to deploying a transparent table of the ABAP repository as a database table in any DB.
![Screenshot of CDS data definition source code, outline, and data preview in ADT.](../images/1b48003f0dcab626.png)
CDS views are the next generation data definition and access for database-centric applications. CDS views provide a cross-platform unified abstraction layer - similar to OData for UI abstraction. For SAP S/4HANA, ABAP CDS views are used. Using CDS views provides a maximum transparency for different programing models. ABAP CDS views provide a consistent lifecycle management and extensibility as with all other ABAP artifacts and are transported using the correction and transport system.
On the one hand, ABAP CDS Views are classic database views compatible with any DB. On the other hand, they include side elements such as annotations, which can only be interpreted by an SAP HANA database. Although CDS Views are stored in the ABAP repository, they can only be viewed using transaction SE80 in the SAP GUI. CDS Views are developed using _ABAP Development Tools (ADT)_ in _Eclipse_.
![Screenshot of AMDP source code with method signature and marker interface in ADT.](../images/a97fcc4ff99a7754.png)
Like CDS Views, AMDPs are developed using ADT and can only be viewed using transaction SE80 in SAP GUI. An AMDP is a global class method containing SQLScript as the programming language. The set of SQL extensions for the SAP HANA database that allow developers to push data intensive logic into the database is called SQLScript. Conceptually, SQLScript is related to stored procedures as defined in the SQL standard, but SQLScript is designed to provide superior optimization possibilities. SQLScript is used in cases where CDS Views are not sufficient, for example, for complex selections or calculations.
AMDPs can be identified by the syntax BY DATABASE PROCEDURE FOR HDB LANGUAGE SQLSCRIPT behind the method name. Classes containing AMDPs implement the marker interface IF_AMDP_MARKER_HDB.
Note
For more information about this topic, see:
  * Data Modelling in ABAP Dictionary and ABAP CDS (Classroom Training)
<https://training.sap.com/course/s4d430>
  * Building Data Models with the ABAP Dictionary and ABAP Core Data (Online Course)
<https://learning.sap.com/courses/building-data-models-with-the-abap-dictionary-and-abap-core-data-services>

## Test ABAP CDS Views
### Business Example
You want to examine and test a DDL SQL and ABAP CDS view in the _ABAP Development Tools_ (_Eclipse_).
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Log on an SAP S/4HANA System in Eclipse
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_AB420EC3BF52C28B:uebung)
#### Steps
  1. Start _Eclipse_ and create an ABAP project connecting to your SAP S/4HANA (S4H) system.
    1. In the Windows start menu, choose _Eclipse IDE_.
    2. Close the _Welcome_ screen.
    3. Choose _Open Perspective_ in the upper right corner.
    4. Select _ABAP_ and choose _Open_.
    5. Choose _New_ → _ABAP Project_.
    6. In the _Connection Settings_ popup, in the _System ID_ field, enter the SID of your S4H.
    7. Select the _Activate Secure Network Communication (SNC)_ checkbox.
    8. Choose _Next >_.
    9. In the _Client_ field, enter the client of your S4H.
    10. In the _User_ field, enter your user.
    11. Choose _Finish_.

### Task 2: Examine and Test an ABAP CDS View
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_7833AF6D1B1E808A:uebung)
#### Steps
  1. Examine and test the CDS view **UX100_C_Product** in Eclipse on your S4H.
    1. In _Eclipse_ , choose _Navigate_ → _Open ABAP Development Object..._.
    2. In the _Search_ field, enter **ux100_c_product**.
    3. Select _UX100_C_Product (Data Definition)_ and choose _OK_.
    4. Examine the CDS view.
    5. Choose _Run_ → _Run As_ → _ABAP Application_.
#### Result
A list of products is displayed.

## SAP Fiori Elements
![Screenshot collage of SAP Fiori elements floorplans: List Report, Object Page, Overview Page, Analytical List Page, and Worklist.](../images/6b08b94147f8d512.png)
SAP Fiori elements is a metadata-driven development of SAPUI5 applications and distinguishes the following floorplans:

List Report
    Allows users to view and work with items (objects) organized in list (table) format.

Object Page
    Provides functionality to view, edit, and create (business) objects.

Overview Page
    Visualizes large amount of data in cards with different formats for different types of content.

Analytical List Page
    Identifies relevant areas within data sets or significant single instances using data visualization and business intelligence.

Worklist
    Displays a collection of items that a user must process.
![Diagram shows the data flow between SAP Fiori Elements, SAP Fiori launchpad, SAP Gateway framework, SAP Gateway service, Core Data Services, and Database Table through various files and services.](../images/f237ee640caf9961.png)
The main source of the metadata for SAP Fiori elements is metadata extensions in the Core Data Services (CDS). Although you can add UI-annotations directly in data definitions, it is recommended to separate the definition of the UI from the data model definition.
The metadata of the SAP Gateway service providing the business data provides the parts of the UI definition suitable to the OData standard. On top of that the /IWFND/CATALOGSERVICE of the SAP Gateway framework provides all other parts, which are not allowed to be part of the metadata of an OData service.
In the SAPUI5 development environment, you can enrich the UI definition by adding annotations in the annotation.xml or by mapping page config files. These JSON-files describe certain parts of the UI in more detail.
![Source code of a metadata extension for general header info, object page facet, and list report line item.](../images/cb26baee31180878.png)
This example shows the definition of a list report combined with an object page. At the top, some general header information for both SAP Fiori elements is set. Then an object page facet is created defining a frame for the data. The ProductUUID is hidden from the user. Product is the semantic key defined as line item in the list report. Finally, Price is set as an identifier in the object page.
![Screenshot of the Preview button of a service binding in the ADT and the result.](../images/a5e42d4ba7923f95.png)
Without using any SAPUI5 development environments, a preview of the list report can be provided via a service binding in the _ABAP Development Tools (ADT)_. This preview directly runs on the ABAP system that the ADT is connected to but does not perform any deployment. Only the UI-annotations in data definitions and metadata extensions are considered, the metadata available on the ABAP-level.
![Screenshot of guides and code snippet in SAP Fiori Tools – Guided Development in SAP Business Application Studio.](../images/e21772b013b24490.png)
The _SAP Fiori tools_ as part of the _SAP Business Application Studio_ and available in _Visual Studio Code_ are the recommended tool for developing the SAP Fiori elements artifacts on UI-level. The _Guided Development_ of the _SAP Fiori tools_ offers many guides to add more features to the application. A guide offers a documentation of steps, screenshots of the expected result, code snippets, and often a wizard for applying the feature directly in an application in the workspace.
Note
For more information about this topic, see:
Creating an SAP Fiori Elements App Based on an OData V4 RAP Service (Online Course)
<https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service>
## Test SAP Fiori Elements List Report
### Business Example
You want to examine the source of an SAP Fiori elements list report and test it in the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Examine the Source Code of a List Report
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2E18128F92C744A9:uebung)
#### Steps
  1. In _Eclipse_ connected to your SAP S/4HANA (S4H) system, examine the UI-definition in the metadata extension of the _UX100_C_PRODUCT_ data definition.
    1. In _Eclipse_ connected to your S4H, open the _UX100_C_PRODUCT_ data definition.
    2. In the _Outline_ , right-click _UX100_C_PRODUCT_.
    3. Choose _Get Where-used List_.
    4. In the _Search_ view, double-click _UX100_M_PRODUCT (Metadata Extension)_.
    5. Examine the @UI-tags in the metadata extension.
  2. Check the source name of the data exposed by the _UX100_UI_PRODUCT_LIST_ service definition. Examine the data provided by the list report preview of the _UX100_UI_PRODUCT_LIST_ service binding.
    1. In the _Search_ view, double-click _UX100_UI_PRODUCT_LIST (Service Definition)_.
    2. Check the exposed data source name.
    3. In the _Outline_ , right-click _UX100_UI_PRODUCT_LIST_.
    4. Choose _Get Where-used List_.
    5. In the _Search_ view, double-click _UX100_UI_PRODUCT_LIST (Service Binding)_.
    6. In the _Entity Set and Association_ list, select _Product_.
    7. Choose _Preview..._.
    8. In the _Select a certificate_ popup, select your certificate and choose _OK_.
    9. In the list report, choose _Go_.
    10. Examine the list of products.

### Task 2: Test a List Report in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_4AB0CE8A50453C8F:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your S4H, test the _Display Products_ app of the _UX100 - SAP Fiori Elements_ catalog.
    1. In the _SAP Fiori launchpad_ of your S4H, choose _Home_ in the upper left corner.
    2. In the _Navigation Menu_ , choose _UX100 - SAP Fiori Elements_ from the list of catalogs.
    3. Choose _Display Products_.
    4. Choose _Go_.
    5. Operate the app as you wish.

[Continue to quiz](https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/architecture_88ae48ea-70c6-30f6-b4d8-6124433a3d58)
