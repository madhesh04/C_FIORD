# Creating Technical Catalogs

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/creating-technical-catalogs_aaedcee4-2e13-4ab5-b2f3-21402b9fdf87*

Objective
After completing this lesson, you will be able to create technical catalogs.
## Technical Catalog Maintenance
Watch the video to understand more about technical catalog maintenance.
## SAPUI5 App Descriptor Elements
![Screenshot of configuration of Post General Journal Entries app in SAP Fiori apps reference library with BSP, ICF path, component ID, reuse components, and intent.](../images/3fb2c10b240a0db4.png)
In this example from the _SAP Fiori apps reference library_ , you see the technical name known as Business Server Page (BSP) of the SAPUI5 application, the ICF path, and the SAPUI5 component ID. For the target mapping, you see the semantic object and action forming the intent.
SAPUI5 apps can consist of multiple SAPUI5 components. One central component is the core of the app and represents the starting point. All other components are referenced or reused in this central component. The idea is that these other components consist of features and functions also valid or even needed for other apps. Therefore, these components are called reuse components.
Hint
The _SAP Fiori apps reference library_ offers an own filter for reuse components.
![Screenshot of app descriptor for SAPUI5 Fiori App in FLPAM with ICF path, component ID, and intent.](../images/df6f4b75c1e788d5.png)
In the _SAP Fiori launchpad application manager (FLPAM)_ , the intent, component ID, and ICF path can be found in the _Target Application Fields_ of an app descriptor. The application type _SAPUI5 Fiori App_ is set as the target.
### ICF Path
![Screenshot of path to ICF node in SICF.](../images/3fbb9e36e12bdff8.png)
In the SICF, the BSP name can be used as a filter for the _Service Name_. There will be two hits: One under the node _ui5_ui5_ and another one under the node _bsp_ , which can be ignored.
### SAPUI5 Component
![Screenshot of Component.js with reuse component in SE80 and component ID.](../images/b4f0d570026741bc.png)
An SAPUI5 app is saved as a BSP in the FES. The central file of an SAP Fiori app based on SAPUI5 is Component.js. Here, in most cases, a reuse component is extended using return <component>.extend. The path behind this statement is the component ID.
Hint
The same statement is used to extend apps delivered by SAP in the customer namespace.
![Screenshot of Component.js with declare component in SE80 and component ID.](../images/1e0d4a5a5579e594.png)
If the first statement in the Component.js is jQuery.sap.declare, the app consists of this one component and no other component is reused. There is no return <component>.extend. So, in that case, the component ID is behind of jQuery.sap.declare.
### Transaction Code
![Screenshots of transaction code for launchpad app descriptor item in FLPAM and SE93 with UIAD highlighted.](../images/6cab4a6aa8f60c65.png)
Since SAP S/4HANA 2021, it is possible to create and assign transaction codes to app descriptors. This allows you to expose your FLP content to _SAP Build Work Zone, standard edition_ and use the transaction codes as app IDs.
For launchpad app descriptor items of type _SAPUI5 Fiori App_ , you can create the transaction code in the FLPAM using the _Click for creation_ hyperlink. In read-only mode, this hyperlink changes to _Click for display_. Using these transactions allows customers to define their own app IDs in the customer namespace. Therefore, customer transactions must start with Z.
For Web Dynpro, Web Client UI, and URL apps, the transaction codes must be created manually in the SE93:
| Parameter  | Value  |
| --- | --- |
| _Transaction Type_  | **Transaction with parameters**  |
| _Default values for Transaction_  |  **/UI2/UIAD_APP** (Web Dynpro, Web Client UI) **/UI2/REMOTE_APP_FE** (URL)  |
| _GUI Support_  |  **SAP GUI for Java** **SAP GUI for Windows**  |
| _Default Values - Name of screen field_  | **UIAD**  |
| _Default Values - Value_  | (Launchpad App Descriptor Item ID)  |
## Tile Types
![Screenshot of tile types in FLPAM and FLP: App Launcher - Static, App Launcher - Dynamic, News Tile.](../images/f0e5067452aa5799.png)
There are three different types of tile in SAP Fiori:
  * The _App Launcher – Static_ or just static tile consists of a title and subtitle, an icon, keywords for search, and general information.
  * The _App Launcher – Dynamic_ or just dynamic tile has, in addition, the possibility to show a dynamic number. This number originates from an OData service request, providing a natural number such as a number of data sets. The refresh interval of the number can also be set.
  * The _News_ tile has the special purpose of showing news from Really Simple Syndication (RSS) feeds. It is twice as large as the other two tiles and shows a preview of the feeds listed in its tile definition. When you choose the tile, the news app starts showing all elements of the underlying RSS feeds.
Note
For more information about the news tile, please read SAP Note [2990265](https://me.sap.com/notes/2990265) – _News Tile application not displaying existing configured feed urls after moving to higher release or after the SP upgrade_.

![Screenshots about testing the service URL of a dynamic tile in SAP Gateway client and copying it in the service URL field of a tile in SAP Fiori launchpad application manager.](../images/8b8ecedc76b4b6cf.png)
There is no check for correctness of the OData service URL of a dynamic tile in the FLPAM. Therefore, you should test the URL in another tool before copying it in the _Service URL_ field.
Open the _SAP Gateway Client_ (/IWFND/GW_CLIENT) and enter the OData request in the _Request URI_ field, which should provide the data for the tile. If the status code is 200 and meaning full data is shown in the response body, you may copy and paste the URI without the server and port in the _Service URL_ field of the tile.
## How to Research Configuration Details in SAP Fiori Apps Reference Library
### Business Example
You want to open the _SAP Fiori apps reference library_ and search for technical details of apps used to define app descriptors in standard catalogs.
Watch the video to see how to research configuration details in the _SAP Fiori apps reference library_.
Settings
## Create Standard Catalogs
### Business Example
You want to create a standard catalog with app descriptors for SAPUI5 applications.

Solution:
    SAP_TC_UX100_S_SD_COMMON (Standard Catalog)
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names in this exercise include ##, replace ## with the number of your user.
### Prerequisites
A business catalog was created in exercise **Reference Tiles and Target Mappings**.
### Task 1: Search an App in a Standard Catalog in the SAP Fiori Launchpad Application Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_EC19B0C0716F3DA4:uebung)
#### Steps
  1. In the _SAP Fiori launchpad application manager_ of your SAP S/4HANA (S4H) system, search for the _Track Sales Orders_ app in the **SAP_TC_CEC_SD_COMMON** catalog. Note down the _SAP Fiori ID_.
SAP Fiori ID:_______________________________________________________________
Note
If you do not see a list of catalogs but just two input fields, execute the last task of the exercise **Create Replicable Catalogs** :
Allow Standard and Replicable Catalogs as Catalog Types in an ABAP System.
    1. In the _SAP Fiori launchpad_ of your S4H, choose the _Launchpad App Manager_ tile or start transaction /UI2/FLPAM.
    2. In the _Technical Catalog ID_ field, enter ***cec*** and choose _Go_.
    3. In the _Technical Catalogs_ table, choose the _SAP_TC_CEC_SD_COMMON_ catalog.
    4. Choose _Search_ (Magnifier) on the top right.
    5. In the _Search for_ field, enter **track sales orders** and choose **Enter**.
    6. Note down the _SAP Fiori ID_**F2577**.
    7. Close the Web browser tab.

### Task 2: Create a Standard Catalog and Copy an App Descriptor in the SAP Fiori Launchpad Application Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_97B85454C7C04AAC:uebung)
#### Steps
  1. In the _SAP Fiori launchpad application manager_ of your S4H, create the empty standard catalog **Z_##_TC_SD_COMMON** with title **Z## - Sales and Distribution** as local object.
    1. In the _SAP Fiori launchpad application manager_ , choose _New Technical Catalog_.
    2. In the _Technical Catalog ID_ field, enter **Z_##_TC_SD_COMMON**.
    3. In the _Technical Catalog Title_ field, enter **Z## - Sales and Distribution**.
    4. From the _Technical Catalog Type_ dropdown, select **Standard Catalog**.
    5. Select _Create empty technical catalog only_.
    6. Choose _Local Object_.
  2. Copy the _Track Sales Orders_ app to your _Z_##_TC_SD_COMMON_ catalog using the _SAP Fiori ID_ that you noted down. Change the action to **trackStatus##** and the tile title to **Track Sales Orders ##**.
    1. In the _Search Term_ field, enter **z_##** and choose _Go_.
    2. In the _Technical Catalogs_ table, choose _Z_##_TC_SD_COMMON_.
    3. Choose _Copy from Other Technical Catalog_.
    4. In the _Select Transport Request_ popup, choose _Local Object_.
    5. In the _Copy from Other Technical Catalog_ popup, choose _Adapt Filters_.
    6. In the _Adapt Filters_ popup, select _SAP Fiori ID_ and choose _OK_.
    7. In the _SAP Fiori ID_ field, enter **F2577** and choose _Go_.
    8. Select the _Semantic Object_**SalesOrder** with _Action_**trackStatus** and choose _Copy_.
#### Result
The warning _Transaction code exists but has a different launchpad app descriptor item ID assigned in SE93_. Unless you change the target application, this is fine.
    9. Close the warning message.
    10. In the _Action_ field, enter **trackStatus##**.
    11. In the _Details_ section, choose the _Tiles_ tab.
    12. In the _Title_ field, enter **Track Sales Orders ##**.
    13. Choose the _Target Application Fields_ tab.
    14. Choose _Save_.

### Task 3: Create an App Descriptor for an SAPUI5 Application in the SAP Fiori Launchpad Application Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_1033F1D92F541D86:uebung)
#### Steps
  1. In the _SAP Fiori launchpad application manager_ of your S4H, add an SAPUI5 Fiori app descriptor for the _Manage Sales Orders - Version 2_ app in your _Z_##_TC_SD_COMMON_ catalog using the following values:
| Field  | Value  |
| --- | --- |
| _Semantic Object_  | **SalesOrder**  |
| _Action_  | **manage##**  |
| _App Type_  | **SAPUI5 Fiori App**  |
| _SAPUI5 Component ID_  | **cus.sd.salesorderv2.manage**  |
| _ICF Path_  | **/sap/bc/ui5_ui5/sap/sd_sov2_mans1**  |
    1. In the _SAP Fiori launchpad application manager_ of your S4H, choose _Add App_ → _SAPUI5 Fiori App_.
    2. In the _Target Application Fields_ tab, enter the following values:
| Field  | Value  |
| --- | --- |
| _Semantic Object_  | **SalesOrder**  |
| _Action_  | **manage##**  |
    3. Open the value help for _SAPUI5 Component ID_.
    4. In the popup, in the _SAPUI5 Component ID_ field, enter **cus.sd.salesorder*** and choose _Go_.
    5. Select _Manage Sales Orders - Version 2_.
    6. Choose _Save_.
#### Result
The warning _Transaction code is not entered_ is displayed. This is solved in the next step.
    7. Close the warning message.
  2. For the _Manage Sales Orders ##_ app, create the transaction code **Z##_F3893**.
    1. Choose _Edit_ in the upper left.
    2. In the _SAP Fiori ID_ field, enter **Z##_F3893**.
    3. For the _Transaction Code_ , choose _Click for creation_.
    4. In the _Warning_ popup, choose _OK_.
    5. In the _Create / Display Transaction_ window, choose _Create Transaction_.
    6. Close the _Create / Display Transaction_ window.
    7. Choose _Save_.

### Task 4: Create a Dynamic Tile in an App Descriptor in the SAP Fiori Launchpad Application Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_8F42423D4923BB9B:uebung)
#### Steps
  1. In the _SAP Fiori launchpad application manager_ of your S4H, add a dynamic tile as default to your _Manage Sales Orders ##_ app using the following values:
| Field  | Value  |
| --- | --- |
| _Title_  | **Manage Sales Orders ##**  |
| _Tile Subtitle_  | **SAPUI5**  |
| _Tile Icon_  | **sales-order**  |
| _Service Root URI_  | **/sap/opu/odata4/sap/c_salesordermanage_srv/srvd/sap/c_salesordermanage_sd/0001/SalesOrderManage/$count**  |
    1. In the _SAP Fiori launchpad application manager_ of your S4H, in the _Details: SalesOrder-manage##_ pane, choose the _Tiles_ tab.
    2. In the _Tiles_ table, choose _Add Tile_ → _App – Launcher Dynamic_.
    3. In the new table entry, enter the following values:
| Field  | Value  |
| --- | --- |
| _Title_  | **Manage Sales Orders ##**  |
| _Tile Subtitle_  | **SAPUI5**  |
    4. For the _Tile Icon_ field, open the value help.
    5. In the popup, in the _Search_ field, enter **sales**.
    6. Select _sales-order_.
    7. Choose _Set Tile as Default_.
    8. Choose _Save_.
  2. To create a valid _Service URL_ for the dynamic tile, request the number of sales orders provided by the OData V4 services _C_SALESORDERMANAGE_SD_ of the service group _C_SALESORDERMANAGE_SRV_ in the _SAP Gateway Client_.
    1. In the _SAP Easy Access_ screen, search for _SAP Gateway Service Administration_ or start transaction /IWFND/V4_ADMIN.
    2. Expand _Service Groups_ on the left.
    3. Double-click _C_SALESORDERMANAGE_SRV_.
    4. In the _C_SALESORDERMANAGE_SRV_ table, select _C_SALESORDERMANAGE_SD_.
    5. Choose _Service Test_.
    6. In the _SAP Gateway Client_ , select _HTTPS_ as _Protocol_.
    7. Choose _Entity Set_.
    8. In the _Entity Sets_ popup, double-click _SalesOrderManage_.
    9. In the _Request URI_ field, replace ?sap-statistics with **/$count**.
    10. Choose _Execute_.
#### Result
There are **0** sales orders.
  3. Insert the valid request URI in the _Service URL_ field of the dynamic tile.
    1. In the _SAP Fiori launchpad application manager_ of your S4H, in the _Z_##_TC_SD_COMMON_ catalog, choose _Edit_ in the upper left.
    2. For the dynamic tile of your _Manage Sales Orders ##_ app, in the _Service URL_ field, enter **/sap/opu/odata4/sap/c_salesordermanage_srv/srvd/sap/c_salesordermanage_sd/0001/SalesOrderManage/$count**.
Hint
Copy the URI from the _SAP Gateway Client_ omitting the server information.
    3. Choose _Save_.

### Task 5: Reference Tiles and Target Mappings in a Business Catalog and Test it in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_804CA62C952208C:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, create a reference for tiles and target mappings of _Track Sales Orders ##_ and _Manage Sales Order ##_ of the _Z_##_TC_SD_COMMON_ catalog in your catalog _Z_##_BC_EMPLOYEE_.
    1. Re-/Start the _SAP Fiori launchpad content manager_ for customizing of your S4H.
    2. In the _Search Catalogs_ field, enter **z_##** and choose _Go_.
    3. In the _Catalogs_ table, select the _Z_##_TC_SD_COMMON_ catalog.
    4. In the _Content in Catalog Z_##_TC_SD_COMMON_ table, select the _Track Sales Orders ##_ and _Manage Sales Order ##_ apps.
    5. Choose _Add Tiles/Target Mappings_ → _Add Selected Tiles/TMs to Other Catalog_.
    6. In the _Search Catalogs_ field, enter **z_##** and choose _Go_.
    7. In the _Catalogs_ table, select the _Z_##_BC_EMPLOYEE_ catalog.
    8. Choose _Add Tile/TM Reference_.
  2. In the _SAP Fiori launchpad_ spaces of your S4H, add the _Track Sales Orders ##_ and _Manage Sales Orders ##_ tiles from the _Z## - Employee_ catalog to the _General_ page of the _Cross Topic_ space and test them.
    1. Start or reload the _SAP Fiori launchpad_ spaces of your S4H in the client of your choice.
    2. Choose your user in the upper right corner.
    3. In the _User Actions Menu_ , choose _App Finder_.
    4. In the list of catalogs on the left, choose _Z## - Employee_.
    5. Choose the plus of the _Manage Sales Orders ##_ tile.
    6. In the _Select Pages for This Tile_ popup, select _Cross Topic_ → _General_ and choose _OK_.
    7. Choose the plus of the _Track Sales Orders ##_ tile.
    8. In the _Select Pages for This Tile_ popup, select _Cross Topic_ → _General_ and choose _OK_.
    9. Choose _Navigate to Home_.
    10. Choose _Cross Topic_ → _General_.
    11. Operate the apps as you wish.
