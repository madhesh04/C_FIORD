# Explaining Application Types

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/explaining-application-types_cbee34f0-8b7c-41b7-9be0-e8f7a733441b*

Objectives
After completing this lesson, you will be able to:
  * Compare application types based on utilized technologies
  * Use SAP Fiori Apps Reference Library for searching product features of apps
  * Create SAP Fiori App Analyses based on utilization of apps.

## Application Types
![A graphic comparing Transactional \(task-based\), Analytical \(insights\), and Fact Sheet \(search\) features, showing their database requirements: Any DB or SAP HANA.SAP Fiori app types](../images/0889d645a5de8442.png)
All SAP Fiori apps utilize the technologies SAPUI5 and SAP Gateway. The three types of SAP Fiori apps are different in terms of their usage of additional technologies:

Transactional Apps

  * Usage of ABAP to provide the classic approach for functions of a business system
  * Available for SAP S/4HANA and SAP Business Suite on any database

Analytical Apps

  * Usage of analytical capabilities of SAP HANA to provide insights in business data
  * Available for SAP S/4HANA and SAP Business Suite powered by SAP HANA

Fact Sheet Apps

  * Usage of Enterprise Search capabilities of SAP HANA to provide search results
  * Available for SAP S/4HANA and SAP Business Suite powered by SAP HANA

![Diagram showing SAP Fiori app subtypes: Transactional with Any DB, and Analytical and Fact Sheet with SAP HANA; each uses SAP Fiori and SAPUI5, detailing pages, reports, and applications used.](../images/87d2d63221d31bd4.png)
_SAPUI5_ is used in all application types for development. This can be done by implementing JavaScript code directly or by defining metadata, which generates JavaScript code at runtime. These apps are called SAP Fiori elements. The complete UI is controlled by metadata annotations in _SAPUI5_ , _SAP Gateway_ , or CDS views.

List Report
    Enables users to view and work with items (objects) organized in list (table) format.

Object Page
    Provides functionality to view, edit, and create (business) objects.

Overview Page
    Visualizes large amount of data in cards with different formats for different types of content.

Analytical List Page
    Identifies relevant areas within data sets or significant single instances using data visualization and business intelligence.

Worklist
    Displays a collection of items that a user must process.
In addition, classic applications are part of transactional apps. These are ABAP transactions, _Web Dynpro ABAP_ , and _WebClient UI Framework_ applications, which already existed before SAP Fiori was announced. Customers can choose which classic applications they want to have in their _SAP Fiori launchpad_ using the configuration and customizing of SAP Fiori.
SAP Business Warehouse (BW) queries can be used as a foundation for SAP Fiori applications. These applications are created through SAP Analytics Cloud, the tool _Design Studio_ , or by developing _Web Dynpro ABAP_ applications.
Caution
Most Design Studio apps are obsolete since SAP S/4HANA 2021 and will be deleted from the system in SAP S/4HANA 2022. The successor apps are already available as Web Dynpro ABAP applications. For more details, please read SAP Note [3081996](https://me.sap.com/notes/3081996) – _Deprecation of SAP Design Studio Apps in SAP S/4HANA 2021_.
## Transactional Examples
![Screenshot of My Quotations in SAP Fiori apps reference library. SAP Business Suite highlighted next to dropdowns for selecting business suite and delivery. Transactional \(SAP Fiori\) and Any DB highlighted.](../images/37642b48009accbd.png)
All transactional apps perform transactional tasks, such as creating a leave request for an employee or managing quotations. SAP Fiori transactional apps represent simplified views and interactions with existing business processes and solutions. They generally run on any database except if they are developed and shipped with SAP S/4HANA.
![Screenshot of Manage Sales Orders in SAP Fiori apps reference library. Transactional \(SAP Fiori elements\) and list highlighted meaning List Report.](../images/3d7e880c9bf82205.png)
Transactional apps can be generated based on _SAP Fiori elements_. These are dynamic _SAPUI5_ apps controlled by metadata annotations in _SAPUI5_ , _SAP Gateway_ , or CDS views. The most common transactional _SAP Fiori element_ is the list report.
![Screenshot of Create Material in SAP Fiori apps reference library. SAP GUI and MM01 highlighted meaning transaction code as app ID.](../images/2d73f26b25b2312c.png)
Since the release of SAP S/4HANA 1610, SAP GUI transactions can be found in the _SAP Fiori apps reference library_. Due to SAP Fiori 2.0 and the SAP Belize theme, they are an official part of SAP Fiori. The transactions are limited to those targeting end users and those available in SAP S/4HANA 1610 or later.
![Screenshot of Process Maintenance Plan in SAP Fiori apps reference library. Web Dynpro and HANA DB exclusive highlighted meaning transactional apps may also by SAP HANA DB exclusive.](../images/88b9c74aa60e47af.png)
Similar to the SAP GUI transactions, transactional _Web Dynpro ABAP_ applications are also part of SAP Fiori since SAP Fiori 2.0. All transactions and _Web Dynpro_ applications are shown as exclusive to the SAP HANA database in the _SAP Fiori apps reference library_. The reason for this is that the documented release is SAP S/4HANA 1610 or later – and this one is exclusive to the SAP HANA database.
## Analytical Examples
![Screenshot of Material Documents Overview in SAP Fiori apps reference library. Analytical \(SAP Fiori elements\) and HANA DB exclusive highlighted meaning Analytical List Page.](../images/e2388404b4d27a04.png)
Analytical apps give a role-based insight into real-time operations of your business by collecting and displaying key figures directly in your browser. They can be SAP Smart Business applications or other analytical, predictive, and planning applications. Analytical apps combine the data and analytical power of SAP HANA with the integration and interface components of SAP Business Suite or SAP S/4HANA. They provide real-time information on large volume data in a simplified front end for enterprise control. With SAP Smart Business, you can closely monitor your most important Key Performance Indicators (KPIs) in real time and react immediately to changes in market conditions or operations.
![Screenshot of Grant Overview in SAP Fiori apps reference library. Analytical, BW Query used \(SAP Fiori: Analytics Cloud story\) and HANA DB or HANA side-by-side highlighted meaning only SAP S/4HANA Cloud.](../images/d89f6d01a94dc2ec.png)
As the analytics and planning solution within SAP Business Technology Platform (BTP), SAP Analytics Cloud supports trusted insights and integrated planning processes enterprise-wide. It is a single solution for business intelligence and collaborative enterprise planning, augmented with the predictive analytics and machine learning.
SAP Fiori apps based on SAP Analytics Cloud are only shipped for SAP S/4HANA Cloud by SAP. But like all SAP BTP services, SAP Analytics Cloud can be integrated with on-premise systems like SAP S/4HANA. Two kinds of SAP Analytics Cloud apps are shipped:

Data Analyzer

The _Data Analyzer_ provides ad-hoc query analysis for end-users based on SAP Analytics Cloud models, SAP Business Warehouse (BW) queries, and SAP HANA live views. It allows end-users to navigate, analyze, and filter data as an insight.

Story

A _Story_ is where you bring data and visualizations together to tell the story of your business or organization and help you discover insights hidden within your data. A _Story_ can also be referred to as a dashboard.
![Screenshot of Sales Quotations in SAP Fiori apps reference library. Analytical, Web Dynpro, BW Query used \(Web Dynpro\) and HANA DB exclusive highlighted.](../images/7e10ca8b932d31d3.png)
Web Dynpro ABAP applications are stateful, which means that the state of the client application is saved on the server for a certain time. This allows ongoing analysis by just selecting the data once and saving it in the application memory. It is especially helpful when the pure selection of the data costs much runtime but the user does not want to wait after each adjustment of the analysis.
## Fact Sheet Examples
![Screenshot of Shopping Cart Item in SAP Fiori apps reference library. Fact sheet \(SAP Fiori \(SAPUI5\)\) and HANA DB exclusive highlighted meaning only SAP Business Suite.](../images/3b58411333b89a90.png)
Fact sheet apps display contextual information and key facts about central objects used in business operations. Fact sheets are designed to be intuitive and harmonized. From a fact sheet area (tile), you can drill down into its details. You can easily navigate from one fact sheet to its related fact sheets. For example, you can navigate from a document to the related business partner or the master data.
From fact sheets, you can start transactions by navigating to transactional apps, or by accessing the back-end system directly. For example, from a document fact sheet, you can access the back-end system to display document details or edit the document in SAP GUI or _Web Dynpro_.
![Screenshot of Purchase Contract item in SAP Fiori apps reference library. Fact sheet \(SAP Fiori elements\) and Object Page highlighted.](../images/60b303b97b2018cd.png)
Object pages can change or create the data found via search directly in the app without opening other applications. The changes are performed in place. Fact sheet and object pages do not have tiles delivered by SAP. That is a task for customizing or configuration, or for the user when saving their search result as a tile.
## SAP Fiori Apps Reference Library
![Screenshot of the entry page of SAP Fiori apps reference library featuring navigation categories, SAP Fiori app recommendations, and upgrade impact analysis buttons with informational icons and text.](../images/faa5fc27b92c3f49.png)
SAP Fiori is foremost a collection of apps representing the new user experience of SAP and the face of SAP S/4HANA. SAP Fiori apps can be categorized by line of business, industry, and most important user role, as well as technical foundation.
All available apps can be explored using the _SAP Fiori apps reference library_. See <https://www.sap.com/fiori-apps-library>.
Watch the video to see how to filter apps in the SAP Fiori apps reference library.
Watch the video to see how to find apps via App ID.
Hint
The _App ID_ of a transaction is its transaction code.
![Screenshot of Procurement Overview Page in SAP Fiori apps reference library. Steps highlighted: 1. Select Product, 2. Select Release, 3. Choose Information.](../images/67d21c4c9ce96e3a.png)
In the details for an SAP Fiori app, you should first set the product suite followed by the release at the top of the page. Although an app is available in several products and releases, the implementation can differ between these. The header information, product features, implementation information, and related apps change depending on the selected product and release.
This is an example of an overview page. It is based on _SAP Fiori elements_ technology and uses annotated views of app data. Thus, the app content can be tailored to the domain or role.
The overview page acts as a UI framework for organizing multiple cards on a single page. Each card can deliver transactional, analytical, or search data. Therefore, overview pages are often a mixture of application types.
## Operate SAP Fiori Apps Reference Library
### Business Example
You want to open the _SAP Fiori apps reference library_ and search for product features of apps using filters.
### Task 1: Search Product Features of Apps
#### Steps
  1. In a Web browser, open the _SAP Fiori apps reference library_ (<https://www.sap.com/fiori-apps-library>).
Note
If you are using an SAP Learning system, you may use the favorite _SAP Fiori_ → _SAP Fiori Apps Reference Library_.
    1. Open <https://www.sap.com/fiori-apps-library> in a browser of your choice.
    2. Decide on the cookie settings.
  2. Open the product features of the SAPUI5 app _Post General Journal Entries_. Use the following information:
| Field  | Value  |
| --- | --- |
| _Back-End Product_  | **SAP S/4HANA**  |
| _Line of Business_  | **Budget and Finance**  |
| _Application Type_  | **Transactional**  |
    1. In the _SAP Fiori apps reference library_ , choose _SAP Fiori apps for SAP S/4HANA (Private Cloud and On-Premise)_.
    2. Choose _by Line of Business_.
    3. Choose _Budget and Finance_.
    4. Choose _Filter_.
    5. In the _Filter_ popup, open the _Application Type_ dropdown.
    6. Select _SAP Fiori - Transactional_.
    7. Close the _Application Type_ dropdown.
    8. Open the value help for _UI Technology_.
    9. In the _Select: UI Technology_ popup, select _SAP Fiori (SAPUI5)_ and choose _OK_.
    10. Choose _Go_.
    11. In the _Search_ field, enter **general journal** and choose **Enter**.
    12. Choose _Post G/L Document / Post General Journal Entries_.
    13. Examine the product features of _Post General Journal Entries_.
  3. Open the product features of the successor of the _Sales Order Fulfillment Issues_ app for _SAP Business Suite_ in the newest _SAP S/4HANA_. Use the following information:
| Field  | Value  |
| --- | --- |
| _Back-End Product_  | **SAP ERP**  |
| _Application Type_  | **Analytical**  |
    1. Choose _Home_.
    2. Choose _SAP Fiori apps for SAP Business Suite_.
    3. Choose _by Back-End Product_.
    4. In the _Search by Back-End Product_ field, enter **erp**.
    5. Choose _SAP ERP_.
    6. Choose _Filter_.
    7. In the _Filter_ popup, open the _Application Type_ dropdown.
    8. Select _SAP Fiori - Analytical_.
    9. Close the _Application Type_ dropdown.
    10. Choose _Go_.
    11. In the _Search_ field, enter **sales** and choose **Enter**.
    12. Choose _Sales Order Fulfillment Issues_.
    13. Examine the product features of _Sales Order Fulfillment Issues_ for SAP Business Suite.
    14. Beneath the heading, open the _SAP Business Suite_ dropdown.
    15. Choose _SAP S/4HANA_.
#### Result
The app is deprecated and was last shipped with SAP S/4HANA 2021 FPS02.
    16. Choose the _Related Apps_ tab.
    17. Choose _Sales Order Fulfillment Issues (Version 2) (SAP S/4HANA (Private Cloud and On-Premise))_.
    18. Choose the _Product Features_ tab
    19. Examine the product features of _Sales Order Fulfillment Issues (Version 2)_.
  4. Open the product features of the _Create Material_ app. Use the following information:
| Field  | Value  |
| --- | --- |
| _Roles_  | **Master Data Specialist — Product Data**  |
| _Application Type_  | **SAP GUI**  |
    1. Choose _Home_.
    2. Choose _All Apps_.
    3. Choose _Filter_ at the bottom.
    4. In the _Filter_ popup, open the _Application Type_ dropdown.
    5. Select _SAP GUI_.
    6. Close the _Application Type_ dropdown.
    7. Open the value help for _Role_.
    8. In the _Select: Role_ popup, in the _Search_ field, enter **product data** and choose _Go_.
    9. Select _Master Data Specialist - Product Data_ and choose _OK_.
    10. Choose _Go_.
    11. In the _Search_ field, enter **create** and choose **Enter**.
    12. Choose _Create Material, Create Material & (MM01)_.
    13. Examine the product features of _Create Material_.

## SAP Fiori App Analyses
![Screenshot flow about logging in SAP Fiori apps reference library showing the available additional features.](../images/a7565597dce67a5d.png)
The _SAP Fiori apps reference library_ offers additional features when signing-in with an SAP user. For example, you can save filters and selections or navigate to related resources like the _Maintenance Planer_. In addition, you can:
  * Identify the impact an upgrade will have on SAP Fiori apps
  * Get recommendations for SAP Fiori apps

by analyzing the usage of an existing system landscape.
Watch the video to get an overview of SAP Fiori Upgrade Impact Analysis.
Settings
### SAP Fiori App Recommendations Analysis
![Screenshot flow about selecting usage and system profiles in SAP Fiori app recommendations analysis.](../images/874fa0b173c06556.png)
The _SAP Fiori App Recommendations_ analysis can be started on the main page by choosing _Get SAP Fiori App Recommendations_. It needs a usage and system profiles as input:

Usage Profile
    A usage profile is a list of the most used transactions in a system. These can be collected based on end-user feedback or by tracing the used transactions in the system, for example, through the _Workload Monitor_ (ST03).

System Profile
    A system profile is a list of installed software components in an SAP system. These can be collected using the system information of a system or functions of the SAP Solution Manager, for example, the _Landscape Management Database (LMDB)_.
![Screenshot of the SAP Fiori recommendations analysis list view. Areas labeled: Relevance, Requirements, Details, Views, Filter, Other Analysis, and Download.](../images/998b8683dc3abe85.png)
The analysis results in a table of apps with information about their relevance and system requirements depending on the usage and system profiles. The table can be filtered in many ways, for example, by application types, line of business, or roles. Views can be created to save changes to the layout of the table. The following views are predefined:
  * _Overview_
  * _Installation Details_
  * _Fiori Launchpad Content_
  * _Configuration Details_

Details of each app can be accessed by just clicking on one entry in the table or you can switch from the list view to the detail view, which jumps to a filtered view of the _SAP Fiori apps reference library_.
## Create SAP Fiori App Recommendations
### Business Example
You want to open the _SAP Fiori apps reference library_ and operate the _SAP Fiori App Recommendations_.
This exercise requires an SAP account.
### Task 1: Create an SAP Fiori App Recommendations Analysis
#### Steps
  1. In a Web browser, log on to the _SAP Fiori apps reference library_ (<https://www.sap.com/fiori-apps-library>) using your SAP account.
Note
If you are using an SAP Learning system, you may use the favorite _SAP Fiori_ → _SAP Fiori Apps Reference Library_.
    1. Open <https://www.sap.com/fiori-apps-library> in a browser of your choice.
    2. Decide on the cookie settings.
    3. In the top right, choose _Sign In_.
    4. Log on using your SAP account.
  2. Create a new analysis **Sample Analysis (UX100)** for the product suite **SAP S/4HANA** using the **Sample Usage Profile (Shared)**.
    1. On the home page, choose _Get SAP Fiori App Recommendations_.
    2. Select _Create new analysis_.
    3. Choose _Step 2_.
    4. In the _Usage Profile_ dropdown, select **Sample Usage Profile (Shared)**.
    5. Choose _Step 3_.
    6. In the _Analysis for Product Suite_ dropdown, select **SAP S/4HANA (Private Cloud and On-Premise)**.
    7. In the _Front-End System Profile_ dropdown, select **Sample Frontend Profile (Share)**.
    8. In the _Back-End System Profile_ dropdown, select **Sample Backend Profile (Shared)**.
    9. Choose _Step 4_.
    10. In the _Analysis Name_ field, enter **Sample Analysis (UX100)**.
    11. Choose _Get SAP Fiori App Recommendations_.
  3. Filter the list of apps of your analysis by _Application Type_ _Fiori - Analytical_ and _Role_ _Accounts Payable Accountant_. Switch to the detail view and examine the feedback options.
    1. Choose _Application Type_.
    2. In the popup, select _Fiori - Analytical_ and choose _OK_.
    3. Choose _Role_.
    4. In the popup, select _Accounts Payable Accountant_ and choose _OK_.
    5. Choose _Detail View_ at the bottom.
    6. Choose the speech balloons in the lower right corner and mention the feedback options.

[Continue to quiz](https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/technology_c7774c6f-fd9a-376b-b158-20eca37aa74e)
