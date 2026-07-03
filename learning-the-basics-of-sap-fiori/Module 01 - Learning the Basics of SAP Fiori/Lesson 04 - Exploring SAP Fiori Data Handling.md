# Exploring SAP Fiori Data Handling

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/exploring-sap-fiori-data-handling_c0701c78-f545-4219-8ace-beb7d28cdd09*

Objectives
After completing this lesson, you will be able to:
  * Execute SAP Fiori data handling.
  * Operate SAP Fiori search.

## Interaction Floorplan
![SAP Fiori interaction pyramid and flowchart displaying components of FLP: Entry point at the top connects to a domain section, which further leads to details sections on the left and right sides of the diagram.](../images/0d71143365df06c9.png)
The SAP Fiori interaction pyramid visualizes the connection between different layers of apps. The overall content scope becomes more focused with each interaction step. The FLP used as an entry point contains all favorite apps of a user. An overview page focuses on the domain-specific key tasks and contains only the most frequently used apps for a role. A pool of apps shows the details and offer actions for certain business objects with object pages standing in the center of cross-app navigation.
![Screenshot of an overview page displaying analytical, list, and table cards with charts, graphs, and lists.](../images/cd081b9785138e5d.png)
The overview page (OVP) is a data-driven SAP Fiori app type and floorplan. It provides all the information that a user needs in a single page, based on the specific domain or role of the user. It enables the user to focus on the most important tasks and view, filter, and react to information quickly. Each task or topic is represented by a card (or content container). Different types of cards enable the visualization of information in an attractive and efficient way.
![Screenshot of an object page showing details of a product like delivery time, leasing installment, assembly options, contact information, and a table of assembly options. Elements are labeled as header, sections, and block.](../images/3b1c9013eda53621.png)
The object page enables the user to display, create, or edit a business object. It comes with a flexible header; a choice of anchor or tab navigation; and a flexible, responsive layout. These features make it adaptable for a wide range of use cases. The object page, similar to the overview page, is based on _SAP Fiori elements_ technology and uses an annotated view of app data.
## SAP Fiori Search
SAP Fiori offers a powerful search to find contents in the _SAP Fiori launchpad (FLP)_. Using any database, you can search for text fragments of SAP Fiori tiles. However, when using SAP HANA, all business data of the back-end server (BES) can be searched quickly.
To access the SAP Fiori search, open the _Search_ field at the top of the FLP, select a data area, and enter any value of a dataset in the BES. You can use the wildcard * as a placeholder.
Watch the video to see how to use the SAP Fiori Search.
## Operate SAP Fiori Search
### Business Example
You want to search for business data using the SAP Fiori search, navigate to dependent business objects, and save the result as a tile in the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Navigate SAP Fiori Search
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_6D897154FB0D8E83:uebung)
#### Steps
  1. Search for all banks in **Germany** in the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system.
    1. In the _SAP Fiori launchpad_ of your S4H, choose _Search_ in the upper right-hand corner.
    2. In the _Search In_ dropdown, choose _Banks_.
    3. In the _Search_ field, enter ***** and choose **Enter**.
    4. Choose _Show filters_ in the upper left.
    5. In the _Filter By_ pane, choose _Germany_ as _Country_.
    6. Examine the _Results_ screen.
  2. Display the G/L account balances of the house bank account of **Bank 1** for the currency _EUR_.
    1. On the _Results_ screen, choose _Bank 1 - SAMPLE BANK 50070010_.
    2. In the _House Banks_ table, choose _DEBK1_.
    3. In the _House Bank Accounts_ table of _DEBK1_ , look for _EUR_ in the _Currency_ column.
    4. Choose the _G/L Account_ _11001000_.
    5. In the popup, choose _Display G/L Account Balances_.
    6. In the _Fiscal Year of Ledger_ field, enter the current year and choose **Enter**.
#### Result
There are no balances for this G/L account in the current year.

### Task 2: Save an App as Tile
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_A53F6F326BA876A5:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ spaces of your S4H, save the balances of the G/L account _11001000_ as a tile in your _My Home_ page. Add **Bank 1 Giro** as _Subtitle_ for the tile.
    1. In the _SAP Fiori launchpad_ of your S4H, in the _Display G/L Account Balances_ , in the upper right-hand corner, choose _Share_ → _Save as Tile_.
    2. In the _Subtitle_ field, enter **Bank 1 Giro**.
    3. For the _Pages_ field, open the value help.
    4. In the _Pages_ popup, select _My Home_ and choose _Apply_.
    5. Choose _Save_.
    6. Choose _Navigate to Home_.
    7. In the _Apps_ section, choose the _Display G/L Account Balances (Bank 1 Giro)_ tile.
    8. Continue to operate the SAP Fiori search as you wish.

[Continue to quiz](https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/end-user-perspective_430105f0-e770-31b0-bdd7-8fab5d5399e0)
