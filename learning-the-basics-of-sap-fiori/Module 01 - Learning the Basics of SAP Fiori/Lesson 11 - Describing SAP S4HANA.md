# Describing SAP S/4HANA

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/describing-sap-s-4hana_b1260c05-e47c-4e46-914d-3b4cf1cde5d5*

Objectives
After completing this lesson, you will be able to:
  * Explain landscape of SAP Fiori for SAP S/4HANA.
  * Explain SAP S/4HANA Embedded Analytics
  * Explain SAP HANA Enterprise Search.

## SAP S/4HANA
![Timeline showing evolution of SAP products: R/2 in 1979, R/3 in 1992, ERP in 2004, and S/4 HANA in 2015. Each stage is represented by a circle with the respective year below.](../images/54a1251f121d0ea9.png)
In SAP R/2, SAP started to deliver screens to specialists in order to enter information into the system. These users were experts in their fields, highly skilled, and well-trained to use the system. Today, even the operation of an MRP Run is more like controlling a machine or using an interface to a business function than an intuitive and self-explaining UI.
With SAP S/4HANA, SAP is executing the vision to empower every customer employee to use SAP business software. The "S" in S/4HANA stands for Suite, the "4" stands for fourth generation. The complete name is SAP Business Suite 4 (for) SAP HANA (S/4HANA).
![Timeline of SAP HANA's development to SAP S/4HANA: 2011 - SAP HANA, 2012 - SAP Business Warehouse powered by SAP HANA, 2013 - SAP Business Suite powered by SAP HANA, 2014 - SAP Simple Finance, 2015 - SAP S/4HANA.](../images/5b3d9932d17914d1.png)
SAP S/4HANA is the next-generation business suite to help lines of business and industries to run simply, with all that only SAP HANA can do. SAP S/4HANA combines recent innovations (SAP HANA platform and SAP Fiori UX) with over 40 years of experience in mastering complex industry challenges in a new suite that caters to a digital, networked economy. The first part of SAP S/4HANA that was available was SAP Simple Finance, the first optimized solution.
SAP S/4HANA delivers the simplicity that users must succeed.
![Diagram of SAP S/4HANA features, including reimagined user experience with SAP Fiori UX, reimagined data models using in-memory tech, and reimagined system configuration for simplicity.](../images/fd62068556da47a3.png)
From an IT value perspective, SAP S/4HANA creates unique opportunities to dramatically simplify the landscape and reduce the total cost of ownership (TCO), with SAP HANA as the great simplifier. Business users can leverage a simple and role-based user experience based on modern design principles, minimizing training efforts while increasing productivity. Rapid activation eases the creation of settings in areas from system administration to application customizing. Enterprises can now significantly reduce their data footprint and work with larger data sets in one system to reduce hardware and operational costs and save time.
### SAP S/4HANA Key Facts
The following are key facts about SAP S/4HANA:
  * Faster analytics and reporting
  * Fewer process steps
  * ERP, CRM, SRM, SCM, and PLM co-deployed
  * All data: social, text, geo, graph, and processing
  * No locking, parallelism
  * Actual data (25%) and historical (75%)
  * Smaller total data footprint
  * SAP Fiori UX for any device

### Data Footprint Reduction
One of the key features of SAP S/4HANA includes smaller total data footprint. Watch the video to understand how SAP HANA reduces its data footprint.
## Landscape of SAP Fiori for SAP S/4HANA
![Visualization of SAP Fiori system landscape – SAP S/4HANA: SAP Fiori launchpad at the top, optional Web Dispatcher in the middle, and SAP front-end server with SAP DB and SAP S/4HANA with SAP HANA at the bottom.](../images/99979e85cdfbecd8.png)
The general system roles in the SAP Fiori system landscape do not change when moving to SAP S/4HANA. The _SAP Fiori launchpad_ running in a client still connects to the FES via the SAP Web Dispatcher. What changes are the capabilities of the BES, which now has optimized code for SAP HANA as an SAP S/4HANA. General information about the FES can be found in the SAP Note [2590653](https://me.sap.com/notes/2590653) – _SAP Fiori front-end server deployment for SAP S/4HANA_.
![Visualization of SAP Fiori system landscape – Hub deployment showing the flow from FLP through SAP Web Dispatcher to FES and BES layers, displaying various protocols like HTTPS and OData, and database connections with SAP HANA.](../images/63cbf47b523339bf.png)
All application types are available for SAP S/4HANA (S4H). The important difference to the SAP Business Suite is that there is only one architecture type for all application types. All applications act like transactional apps communicating via SAP Gateway over the FES with the BES now an S4H. Only the classic applications and in some scenarios the SAP Fiori search connect directly to the S4H.
The hub deployment option will be supported also for SAP S/4HANA 2025. Nevertheless, there might be restrictions regarding the availability of future new features. Some features might only be available in the embedded deployment due to technical reasons.
![Visualization of SAP Fiori system landscape – Embedded deployment showing the flow from FLP through SAP Web Dispatcher to SAP S/4HANA, displaying various protocols like HTTPS and OData, and database connections with AnyDB.](../images/c4922a53153971df.png)
The recommended deployment option for SAP S/4HANA is the embedded deployment. The main reason is that with SAP S/4HANA all data and functions reside in one system. A hub system for routing requests to certain back-ends is no longer needed. In addition, many configuration steps for SAP Fiori get easier when having everything in one system.
Note
For more details, please check the document "SAP Fiori Deployment Options and System Landscape Recommendations": <https://www.sap.com/documents/2018/02/f0148939-f27c-0010-82c7-eda71af511fa.html>
## SAP S/4HANA Embedded Analytics
![Visualization of SAP Fiori system landscape – Analytical apps \(S4H\) showing the flow from an analytical app through SAP Web Dispatcher to product UI and SAP Gateway connected to Embedded Analytics in SAP S/4HANA.](../images/ab34e50afaff1dab.png)
The UIs for analytical apps are part of the same product-specific UI add-ons that provide transactional apps. SAP Gateway again manages the OData services for the apps, but the source is now different. ABAP Core Data Services (CDS) Views are the basis for all analytical applications in S4H. ABAP CDS Views are able to integrate with SAP S/4HANA Embedded Analytics, which originated from SAP Business Warehouse (BW).
Note
When using ABAP CDS Views, there is no need to access data views via the SAP HANA Extended Application Services (XS) like in the SAP Business Suite.
![Screenshots of Manage KPIs and Reports in FLP showing KPI definition, tile, and report highlighting KPIs, reports, and stories.](../images/16c334c5b2ae1f01.png)
The area of business analytics specifically used in SAP Fiori is called SAP Smart Business. The core element there is the Key Performance Indicator (KPI). A KPI is built on top of ABAP CDS Views and defines data source, semantics, and tiles. Related KPIs can be managed in groups.
A report (formally known as drill-down) is the visualization of a KPI offering predefined ways for the user to interact with the data. Customers can organize multiple reports in stories, for example, to tell the story of a product.
Since SAP S/4HANA 1909, _Manage KPIs and Reports [F2814]_ is the central app for managing KPIs, reports, and stories. It is the successor of the _KPI Workspace [F0818]_ , introduced in SAP S/4HANA 1511 and deprecated since SAP S/4HANA 2020.
Note
A predecessor of the _KPI Workspace_ having the same name was already available in SAP Business Suite. The main difference is that not ABAP CDS Views but SAP HANA XS OData services are used as data source. This results in different and extra steps in managing KPIs such as authorizations.
![Screenshot of installation details and OData services of Overdue Payables \(SAP S/4HANA\) in SAP Fiori apps reference library.](../images/e192da55b0f7399a.png)
In this example from the _SAP Fiori apps reference library_ , you see the SAP S/4HANA 2023 as the product solution. Generic drill-down apps like this one need the /SSB/SMART_BUSINESS_RUNTIME_SRVOData service for generating the visualization. In addition, there is an OData service for the actual app data containing "CDS" in its name.
Hint
SAP Gateway services ending in "_CDS" are based directly on an ABAP CDS View. Omitting "_CDS" leaves the view name behind.
![Screenshots of analytical queries in Query Browser and ABAP CDS Views in View Browser in FLP.](../images/59064eb5630411e4.png)
The entry points for users to create their own evaluations are the _Query Browser [F1068]_ available since SAP S/4HANA 1511 and the _View Browser [2170]_ available since SAP S/4HANA 1610. Both show a list of ABAP CDS Views, which are available in the system. The difference is that the _Query Browser_ limits the list on pure analytical views whereas the _View Browser_ is used by more advanced users offering a list of all ABAP CDS Views. Not only the consumption views providing data for applications but all views of the whole virtual data model (VDM) are visible. This enables a more detailed view on the data source but also demands more knowledge of the topic.
No matter which browser is used, after selecting an ABAP CDS View as data source, the _Custom Analytical Queries [F1572]_ app can be started to actually define a query handling dimension, tables, and charts. The result can be saved as a tile to access the query directly in the _SAP Fiori launchpad_.
Note
For more information about this topic, see:
  * SAP S/4HANA Embedded Analytics Foundation (Classroom Training):
<https://training.sap.com/course/s4h400>
  * Discovering SAP S/4HANA embedded analytics (Online Course):
<https://learning.sap.com/courses/discovering-sap-s-4hana-embedded-analytics>

## How to Find Apps for Managing Embedded Analytics
### Business Example
You want to analyze apps managing Embedded Analytics in the _SAP Fiori apps reference library_ and _SAP Fiori launchpad_.
Watch the video to see how to find apps for managing Embedded Analytics.
## Open a Query for Analysis
### Business Example
You want to search for views as a source for analytical queries and create an analysis in the _View Browser_ app.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Examine a Query in the View Browser
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B8D5CD101CE8182:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system, check in the _View Browser_ if the consumption view _UX100_C_FlightByAirportQry_ can be used for analytical queries.
    1. In the _SAP Fiori launchpad_ of your S4H, open the _Cross Topic_ → _Analytics_ page.
    2. Choose the _View Browser_ tile.
    3. In the _Search_ field, enter **ux100** and choose **Enter**.
    4. Choose _Consumption_ at the top.
    5. Choose the view _UX100_C_FlightByAirportQry_.
    6. Choose the _Annotation_ anchor.
    7. Check that the value for _ANALYTICS.QUERY_ is _true_.

### Task 2: Save a Query as Tile
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_92B31B4200367489:uebung)
#### Steps
  1. In the _View Browser_ , show the content of the _UX100_C_FlightByAirportQry_ view. Change the graphical display to show the seats information per airline and plane type.
    1. In the _View Browser_ , choose _Show Content_ in the upper right.
    2. Drag and drop _Airline_ and _Plane Type_ from _Available Fields_ to _Rows_.
    3. Drag and drop _Departure Airport_ and _Destination Airport_ from _Rows_ to _Available Fields_.
    4. Choose _Graphical Display_.
    5. Examine the _Graphical Display_.
  2. In the _View Browser_ , save a suitable visualization as tile in your _My Home_ page.
    1. In the _View Browser_ , choose _Share_ → _Save as Tile_ in the upper right corner.
    2. In the _Save as Tile_ popup, in the _Title_ field, enter **Flight Seats**.
    3. In the _Subtitle_ field, enter **Airline / Plane Type**.
    4. For the _Pages_ dropdown, select **My Home**.
    5. Choose _Save_.
    6. Choose _Navigate to Home_.
    7. In the _Apps_ section, choose the _Flight Seats_ tile.
    8. Continue to operate the app as you wish.

## SAP HANA Enterprise Search
![Visualization of SAP Fiori system landscape – SAP Fiori search \(S4H\) showing the flow from SAP Fiori search through SAP Web Dispatcher to central UI and SAP Gateway connected to Enterprise Search in SAP S/4HANA.](../images/3100c491e022624c.png)
When users want to search for data in the _SAP Fiori launchpad_ , the SAP Fiori search accesses the SAP HANA enterprise search, a successor of the SAP NetWeaver enterprise search. The protocol used for a direct network communication is the SAP proprietary Information Access (InA) protocol, which has some parallels to OData but is specialized for search requests and responses. Since SAP S/4HANA 1809, you can also use the SAP Gateway service ESH_SEARCH_SRV instead. So both, InA and OData are suitable ways of accessing the SAP HANA enterprise search depending on the network landscape.
Hint
Just by registering ESH_SEARCH_SRV, all search requests of the SAP Fiori search are routed through this service.
![Screenshot of search connectors in Connector Administration Cockpit displaying details like name, status, and last update.](../images/32152dc8ed0a630e.png)
Fact sheet apps use search models developed for SAP HANA enterprise search. These search models use the search capabilities of SAP HANA and, therefore, do not run on an SAP Search and Classification (TREX) used by SAP NetWeaver enterprise search. The administration and handling is mainly the same when using SAP HANA or TREX. The following important transactions and applications work for both search engines:

Connector Administration Cockpit (ESH_COCKPIT)
    Connector administration cockpit for connectors of search models to the search engine

Search and Analytics Modeler (ESH_MODELER)
    Modeler for search and analytic for managing search object connector models

Enterprise Search Test (ESH_TEST_SEARCH)
    Test environment for enterprise search checking consistency of connectors and search results

Search and Operational Analytics Implementation Guide (ESH_IMG)
    Area of the Implementation Guide (IMG) containing administration and configuration of the enterprise search
Search models are shipped by SAP and are the basis for search connectors used by apps. Search connectors are indexed (generated) once the search models are available in a system. Therefore, the search connector ID contains the system and client in which it was generated.
Hint
If you encounter duplicates of search connectors in the _SAP Fiori launchpad_ search, please read SAP Note [3007113](https://me.sap.com/notes/3007113) – _Connector name in Fiori search shows word 'Duplicate'_ for possible solutions.
![Visualization of SAP Fiori system landscape – Object pages showing the flow from an object page through SAP Web Dispatcher to product UI and SAP Gateway connected to Enterprise Search in SAP S/4HANA.](../images/b05951aee905cc65.png)
The UIs for object pages are part of the same product-specific UI add-ons that provide transactional and analytical apps. SAP Gateway manages again the OData services for the apps. ABAP Core Data Services (CDS) Views are the basis for all object pages in S4H. ABAP CDS Views utilize the search capabilities of the SAP HANA database by integrating with the SAP HANA enterprise search. That results in generated so-called CDS-based enterprise search (ES) connectors. Similar to the search connectors based on search models, they can be managed in the _Connector Administration Cockpit_. But the details about the source tables, views, and fields are not visible.
Hint
When using ABAP CDS Views, there is no need to access search connectors directly via InA such as in the SAP Business Suite.
![Screenshots of search model list and detail in Manage Search Models in FLP.](../images/cbfb4e09c48aac7f.png)
These details are available in the _Manage Search Models [F3036]_ app since SAP S/4HANA 1909. There, everything concerning a CDS-based ES-connector can be viewed such as fields, filters, relations, or even the source code of the ABAP CDS View.
Note
For more information about CDS-based ES-connectors, please read SAP Note [2399860](https://me.sap.com/notes/2399860) – _ES: Behavior of CDS-based search connectors_.
### Processing CDS-based Enterprise Search Connectors
![Screenshots of Analyze Query Log, Define Search Behavior, and Fine-Tune Ranking in FLP.](../images/477b5edcd0c5c9ee.png)
Since SAP S/4HANA 1809, more SAP Fiori apps are available for managing the processing of CDS-based ES-connectors:

Analyze Query Log [F2571]
    Evaluate log data containing user activities collected during searches, graphically in bar charts, or in tables.

Define Search Behavior (Synonyms) [F2700]
    Display search configurations of business objects, create synonym and stop-word lists, and display where-used lists for configuration settings.

Fine-Tune (Search) Ranking [F2777]
    Create and edit ranking factors and boosts, and test their effects immediately in a simulation.
Let's look at an example of SAP Fiori object page based on CDS view.
![Screenshot of installation details and OData service of Supplier in SAP Fiori apps reference library.](../images/6a3d41b58dfa4b1a.png)
In this example from the _SAP Fiori apps reference library_ , you see the SAP S/4HANA 2023 as a product solution. In addition, there is an OData service but without "CDS" in its name. Not every OData service using ABAP CDS Views is showing this in its name.
Hint
SAP Gateway services ending in "_SRV" are based on SAP Gateway projects. Omitting "_SRV" leaves the project name behind – in most cases. Developers may break this rule.
![Screenshots of Personalized Search and My Queries in FLP showing search history with options for range selection, drill in, log details, search activation, and personalized scope settings.](../images/aeaebcd94b48835b.png)
Users of the _SAP Fiori launchpad_ can activate a personalized search in the FLP settings by selecting _Track Search Activities_ under _Search_. In addition, it is possible to limit the personalized search scope to a selectable number of search connectors.
After activation, all search requests of the user in the SAP Fiori search are logged and made available via the _My Queries [F3719]_ app. Users can view and evaluate their search activities and search terms either graphically in a bar chart or as a table. By default, the personalized search is deactivated and the history can be cleared at any time. These defaults for collecting user-specific data can be managed via the _Configure Personalized Search [F2800]_ app.
Note
For more information about this topic, see:
SAP Fiori – System Administration (Classroom Training)
<https://training.sap.com/course/ux200>
## How to Find Apps for Managing Enterprise Search
### Business Example
You want to analyze apps managing enterprise search in the _SAP Fiori apps reference library_ and _SAP Fiori launchpad_.
Watch the video to see how to find apps for managing Enterprise Search.
Settings
## Activate and Examine Personalized Search Queries
### Business Example
You want to activate the _Personalized Search_ for your user in the _SAP Fiori launchpad_ and examine the search queries in the _My Queries_ app.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Activate Tracking for Search Activities
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_DF9972D8B6C72FA9:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system, activate the tracking of search activities for your user.
    1. In the _SAP Fiori launchpad_ of your S4H, choose your user in the upper right corner.
    2. Choose _Settings_.
    3. Choose _Search_.
    4. Select the _Track Search Activities_ checkbox.
    5. Choose _Save_.

### Task 2: Examine the Search History
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_405085622D2C0B88:uebung)
#### Steps
  1. Perform multiple searches in the SAP Fiori search. Examples are cost centers with **1010** , material BOM with **pump** , or G/L accounts with **building**.
    1. Choose _Search_ at the top.
    2. In the _Search In_ dropdown, choose _Cost Centers_.
    3. In the _Search_ field, enter **1010** and choose **Enter**.
    4. In the _Search In_ dropdown, choose _Material BOM_.
    5. In the _Search_ field, enter **pump** and choose **Enter**.
    6. In the _Search In_ dropdown, choose _GL Account_.
    7. In the _Search_ field, enter **building** and choose **Enter**.
    8. Choose _Navigate to Home_.
  2. In the _My Queries_ app, examine the search history of your user for today. Use the options _Drill In_ and _Display Log Details_ in the diagrams.
    1. Open the _Cross Topic_ → _General_ page.
    2. Choose the _My Queries_ tile.
    3. In the _Date and Time_ dropdown, choose **Today**.
    4. In the diagram, click the largest bar.
    5. Choose _Drill In_.
    6. In the diagram, click a bar of your choice.
    7. Choose _Display Log Details_.
    8. Continue to operate the SAP Fiori search and _My Queries_ as you wish.

## Configuration Parameters for SAP Fiori Search
These customizing parameters can be used to configure the SAP Fiori search in the _SAP Fiori launchpad_ :

DEFAULT_SEARCH_SCOPE_APPS

Specify the default search scope as "Apps" (true) or "All" (false).
true/false (default)

SEARCH

Specify whether the search option is displayed in the launchpad shell header bar.
true (default)/false

SEARCH_BUSINESS_OBJECTS

Specify if business objects are included in the search scope.
true (default)/false

SEARCH_SCOPE_WITHOUT_ALL

Specify whether the "All" connector is removed from the search bar.
true/false (default)
