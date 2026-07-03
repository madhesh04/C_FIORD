# Architecture

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/describing-abap-platform_ac4d4abd-4761-4080-b707-e23a54b709c5*

Objectives
After completing this lesson, you will be able to:
  * Explain landscape of SAP Fiori for ABAP Platform.
  * Explain applications based on SAP Gateway projects.

## Landscape of SAP Fiori for ABAP Platform
![Visualization of the SAP Fiori system landscape – Any database: SAP Fiori launchpad at top, optional SAP Web Dispatcher in middle, SAP front-end server with any database below, SAP back-end server with any database at bottom.](../images/30e1ff0217c1cd2e.png)
The system landscape for SAP Fiori consists mainly of a Front-End Server (FES) and a Back-End Server (BES). These are system roles of an Application Server (AS) ABAP or ABAP Platform in this landscape. The back-end server is an SAP Business Suite or an SAP S/4HANA holding applications and data of any area based on an AS ABAP 7.40 or higher. The front-end server is a basic AS ABAP 7.40 or higher without any business products installed. Both systems can run on any database.
Note
Since release 7.53, Application Server ABAP is renamed ABAP Platform. The reason was the availability of SAP Business Technology Platform (BTP), ABAP environment.
Although the _SAP Fiori launchpad (FLP)_ running in any client is able to communicate with the FES directly, it is recommended to use an SAP Web Dispatcher or another reverse proxy between FLP and FES in external facing scenarios and also internally. The reason is that for some features of the FLP multiple systems must be reached, which is forbidden in web communication with good reason. A reverse proxy offers a single point of communication holding routing rules to forward requests to the correct target systems.
![Diagram compares SAP Fiori deployment options: Left shows embedded deployment with BES \(Product UI, Central UI, SAP Gateway, and ABAP\). Right shows central hub deployment with FES \(Product UI, Central UI, SAP Gateway\) and BES \(SAP Gateway, ABAP\).](../images/c2e24119c6cfdc0d.png)
In some scenarios, it is not necessary to operate separated front-end and back-end servers. It can even be counterproductive to do so. Therefore, you can deploy all components of SAP Fiori in one system, in an embedded deployment.
| Embedded Deployment  | Central Hub Deployment  |
| --- | --- |
| The tasks of the FES for providing SAP Fiori are embedded in the BES. There is only one system.  | The FES and BES are two separated systems splitting the tasks in providing SAP Fiori.  |
SAP Gateway, the only component in FES and BES, is the only part where you have to check carefully, which settings are in which system. As soon as there are multiple systems that want to provide SAP Fiori apps, the FES has many benefits in organizational and security terms.
Note
The recommended deployment option for SAP Business Suite is the central hub scenario. SAP FES 2023 is the last front-end server version, which is supported, and thus has end of maintenance in alignment with SAP Business Suite.
![Visualization of SAP Fiori system landscape – ABAP Platform on any DB showing the flow from FLP through SAP Web Dispatcher to FES and BES layers, displaying various protocols like HTTPS and OData, and database connections with AnyDB.](../images/ae934dc9b0fab955.png)
The SAP Fiori system landscape for a BES on any database supports transactional apps based on SAPUI5 and classic apps based on _Web Dynpro_ and ABAP transactions. Mandatory components of the FES are the SAP Gateway for OData communication, the central UI for general SAP Fiori functions, and product UIs for the apps. The SAP Gateway and ABAP code for the business logic of the apps are in the BES.
![Visualization of SAP Fiori system landscape – SAP Fiori launchpad showing the flow from FLP through SAP Web Dispatcher to SAP Gateway and Central UI in FES.](../images/e521b80038ef6cc9.png)
To use any SAP Fiori app, a running FLP is needed. The FLP is part of the central UI including all views, functions, and tools for personalization, customizing, and configuration of the contents. When thinking about personalization, this is performed by the user in a running FLP. Therefore, the FLP must read and write data from and to the FES using OData, not only for personalization, but also in other areas.
There is no communication to the BES by the FLP. All general settings for SAP Fiori are saved in the FES to be independent from the BES. Although this is not visible in the diagram, having multiple back ends is usual for many customers. Having only one place (system) for SAP Fiori settings is a huge benefit.
![Visualization of SAP Fiori system landscape – Transactional apps showing the flow from transactional app through SAP Web Dispatcher to SAP Gateway and Product UI in FES continuing to SAP Gateway with ABAP in BES.](../images/a8980b73a11f0a2d.png)
Disregarding the need for a running FLP, transactional apps consist of SAPUI5 apps and SAP Gateway services. SAPUI5 apps are saved in the ABAP repository as BSPs and delivered using product-specific UI add-ons. These are installed on the FES. The SAP Gateway services are delivered as part of updates of the BES solution and are written in ABAP.
The registration of the Gateway services is performed on the FES by the customer. So, when transactional apps need data, an OData request is performed via the SAP Web Dispatcher to the registration of the Gateway service on the FES. From there, the SAP Gateway framework creates an RFC request to the implementation of the SAP Gateway service on the BES. In the implementation, ABAP code is used to access the data in the database.
![Visualization of SAP Fiori system landscape – Classic applications showing the flow from classic application through Web Dispatcher to ABAP in BES.](../images/80536780571fbc83.png)
Classic applications are part of the BES solution and have no interaction with the FES besides the FLP itself. The UI and data directly originate from the ABAP code on the BES. The only task of the FES is to provide the connection information to the BES when a navigation request — such as clicking a tile — is initiated in the FLP. This connection information must be set in the FES by an administrator.
## Debug ABAP Transactions in SAP Fiori Launchpad
### Business Example
You want to debug an ABAP transaction in the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Enter Function Debugging in GUI for HTML
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_305FA0A654423BA:uebung)
#### Steps
  1. In a Web browser, open the _Data Browser_ (SE16) in your _SAP Fiori launchpad_. Activate the OK code field in the SAP GUI for HTML settings. Try to switch to debugging at runtime when selecting data from the database table **SCARR**.
    1. In the _SAP Fiori launchpad_ of your S4H, open the _Data Browser_ (SE16).
Note
If you do not have a tile or link, you can find it via the _User Menu_ in the _App Finder_.
    2. Choose _Menu_ → _Settings..._.
    3. In the menu on the left, choose _Interaction Design_ → _Visualization_.
    4. Activate the _Show OK Code field_ switch.
    5. Choose _Save_.
    6. In the _Table Name_ field, enter **SCARR**.
    7. Choose _Table Contents_.
    8. In the _OK code_ field in the upper left, enter **/h** and choose **Enter**.
Hint
You can also choose _More_ → _System_ → _Utilities_ → _Debug Dynpro_.
#### Result
In the footer, the error message _Action not possible in SAP GUI for HTML. Use external debugging._ appears.
    9. In the error message in the footer, choose _View Details_.
    10. Examine the error details.

### Task 2: Enter Function Debugging in GUI for Windows
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_A57162CD6235C592:uebung)
#### Steps
  1. Enable the _SAP GUI OK code_ in the _SAP Business Client_.
    1. Open the _SAP Business Client_.
    2. In the upper left corner, choose _Customize and Control SAP Business Client (three lines)_ → _Settings_ → _SAP GUI Interoperability_.
    3. Select _Enable SAP GUI OK code_.
    4. Choose _OK_.
    5. In the _SAP GUI OK Code Info_ , choose _OK_.
    6. Close the _SAP Business Client_.
  2. In the _SAP Business Client_ , open the _Data Browser_ (SE16) in your _SAP Fiori launchpad_. Switch to debugging at runtime when selecting data from the database table **SCARR**.
    1. Open the _SAP Business Client_.
    2. In the _SAP Business Client_ , double-click the _SAP Fiori launchpad_ entry of your SAP S/4HANA (S4H) system.
    3. Open the _Data Browser_ (SE16).
Note
If you do not have a tile or link, you can find it via the _User Menu_ in the _App Finder_.
    4. In the _Table Name_ field, enter **SCARR**.
    5. Choose _Table Contents_.
    6. In the _OK code_ field in the upper left, enter **/h** and choose **Enter**.
Hint
You can also choose _Menu_ → _System_ → _Utilities_ → _Debug Dynpro_.
#### Result
In the footer, the success message _Debugging switched on_ appears.
    7. Choose _Execute_.
    8. In the _ABAP Debugger_ , examine the ABAP code.
    9. Choose _Continue_.
#### Result
A list of carries is displayed.

## Installation of SAP Fiori Apps
![Visualization of software components and products in FES and BES. FES: SAP Gateway, Central UI, Products UI. BES: SAP Gateway, Products. Various components are listed under each category.](../images/e90015a5eb638781.png)
Looking more closely at software components and products, SAP Gateway consists mainly of the software component SAP_GWFND in the FES and BES. This is part of every AS ABAP since 7.40. Up to 7.50, more features of SAP Gateway may be needed depending on the apps. When using SAP Workflow in SAP Fiori 1.0, the add-on IW_PGW is needed in the FES. When using data models of the Generic Interaction Layer (GENIL), the add-on IW_GIL is needed in the BES. When using Service Provider Infrastructure (SPI), IW_SPI is needed, and so on. All these SAP Gateway add-ons are deprecated since 7.51 and SAP Fiori 2.0 and can be uninstalled. Either the functionality was integrated in SAP_GWFND (for example, SAP Workflow) or it is no longer needed in SAP S/4HANA 1610.
The central UI consists of the software component SAP_UI, which is part of every AS ABAP since 7.40 and holds all UI technologies in the system, not just SAP Fiori.
The product-specific UI add-ons hold not one but all SAPUI5 apps of one solution area. The type and the release should fit to the solution implemented in the BES.
![Screenshot of installation details of Manage Chart of Accounts in SAP Fiori apps reference library.](../images/d487b0c72a68a4ad.png)
In this example of the _SAP Fiori apps reference library_ , you see the product-specific UI add-on must be installed on the FES and the update of the product solution is needed on the BES. The product-specific UI add-on is an add-on to the SAP Fiori FES 2023 for S/4HANA, consisting not only of this app, but all apps for SAP S/4HANA 2023. The update of the BES is the Feature Package Stack (FPS) 02 for SAP S/4HANA 2023. All SAP Fiori applications are installed in such a way.
## Applications Based on SAP Gateway Projects
An SAP Gateway service consists of ABAP classes and customizing elements in the BES, and a service catalog entry in the FES.
Watch this video explaining the architecture of an SAP Gateway service.
![Diagram showing SAP Gateway ABAP transactions: FES with SAP Gateway Service Maintenance leading to SAP Gateway Client; BES with SAP Gateway Service Builder leading to ABAP Workbench.](../images/eac9a0a471098e33.png)
All SAP Gateway transactions are connected to each other via navigation. The following are the most important transactions for SAP Gateway:

SAP Gateway Service Maintenance (/IWFND/MAINT_SERVICE)

Central SAP Gateway service management in the FES

SAP Gateway Client (/IWFND/GW_CLIENT)

SAP Gateway service test environment in the FES

SAP Gateway Service Builder (SEGW)

Central SAP Gateway development environment in the BES

ABAP Workbench (SE80)

Central ABAP development environment in the BES
Let's look at the transaction _SAP Gateway Service Builder_ (SEGW) in detail.
![Screenshot of a project in SAP Gateway Service Builder displaying a data model, runtime artifacts, SAP Gateway alias, and entity type properties like product ID, name, and price with corresponding ABAP field names.](../images/96c3e9e4d455ae9e.png)
The transaction _SAP Gateway Service Builder_ (SEGW) uses projects to bundle all artifacts of a service in one central place, which helps to organize the service development and modeling process. Since projects consolidate all related data, developers can easily work on multiple projects in parallel and reuse data between projects before generating and activating the actual service.
Note
For more information about this topic, see:
Building OData Services with SAP Gateway (Online Course)
<https://learning.sap.com/courses/building-odata-services-with-sap-gateway>
## Debug Apps Based on SAP Gateway Projects
### Business Example
You want to examine an SAP Gateway project of an SAP Fiori app and debug a GET_ENTITYSET-method.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Examine an SAP Gateway Project
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B0E9DD1A209E19B9:uebung)
#### Steps
  1. Log on to your SAP S/4HANA (S4H) system using _SAP GUI_.
    1. In the _SAP Business Client_ or _SAP Logon_ , choose the SAP GUI SNC system entry of your S4H.
    2. Choose _Log On_.
  2. Examine the **EPM_REF_APPS_SHOP** project in the _SAP Gateway Service Builder_ (SEGW) on your S4H.
    1. In the _SAP Easy Access_ screen, search for _SAP Gateway Service Builder_ or start transaction SEGW.
    2. Choose _Open Project_.
    3. In the _Project_ field, enter **EPM_REF***.
    4. Open the value help (**F4**).
    5. Double-click the _Project_**EPM_REF_APPS_SHOP**.
    6. Choose _Execute_ (**F8**).
    7. Examine the EPM_REF_APPS_SHOP project.

### Task 2: Debug the ABAP Code of an SAPUI5 App in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_8C13C73FADFE67B8:uebung)
#### Steps
  1. Set an external breakpoint in the method **PRODUCTS_GET_ENTITYSET** of the class EPM_REF_APPS_SHOP on your S4H.
    1. In the _SAP Gateway Service Builder_ , double-click _Runtime Artifacts_ of the _EPM_REF_APPS_SHOP_ project.
    2. Right-click _CL_EPM_REF_APPS_SHOP_DPC_ and choose _Go to ABAP Workbench_.
    3. Double-click the _PRODUCTS_GET_ENTITYSET_ method.
    4. In the menu, choose _Set/Delete External Breakpoint_.
  2. Start the SAP Fiori reference app _Shop_ in your _SAP Fiori launchpad_ and examine the code in the ABAP Debugger.
    1. In the _SAP Fiori launchpad_ , choose the _Shop_ tile in the _Reference Apps_ page.
    2. In the _ABAP Debugger_ , choose _Single Step_.
    3. Examine the ABAP code.
    4. In the menu, choose _Breakpoints_ → _Delete all BPs_.
    5. Choose _Continue_.
