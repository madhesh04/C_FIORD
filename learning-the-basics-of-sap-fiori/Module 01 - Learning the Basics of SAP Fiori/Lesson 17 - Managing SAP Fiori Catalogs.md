# Managing SAP Fiori Catalogs

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/managing-sap-fiori-catalogs_ab64715f-a452-43c4-9d99-ae95ec3403fa*

Objective
After completing this lesson, you will be able to manage SAP Fiori catalogs
## Content Model for SAP S/4HANA
![Diagram showing that the target mapping of an app descriptor in a catalog refers to the application and the tile of an app descriptor referenced in tiles and links of sections of pages. The space containing the page and the catalog are referenced in user roles.](../images/59531ca06933a652.png)
In personalization, spaces and pages just visualize tiles or links for calling an application. In customizing and configuration, catalogs define app descriptors consisting of tiles and target mappings. Target Mappings hold all the information needed to actually start an application.
Watch the video explaining the content model since SAP S/4HANA 2023.
The following table outlines the elements that can be distinguished in the content model since SAP S/4HANA 2023:
| Element  | Short  | Naming Schema  | Description  |
| --- | --- | --- | --- |
| Business Role  | BR  | SAP_BR_<role>  | Role for topic  |
| Space  | SP  | SAP_<area>_SP_<topic>  | Tiles for topic  |
| Page  | PG  | SAP_<area>_PG_<task>  | Tiles for daily task  |
| Business Catalog  | BC  | SAP_<area>_BC_<duty>  | Tiles for duty  |
| Standard Catalog  | TC  | SAP_TC_<area>_<subarea>_COMMON  | App descriptors for area  |
| Back-End Catalog  | TC  | SAP_TC_<area>_<subarea>_BE_APPS  | App descriptors for area  |
Time to look at an example of the content model from the _SAP Fiori apps reference library_.
![Screenshot of catalogs, pages, spaces, and roles of Post General Journal Entries in reference library.](../images/16f12ce634dc3e30.png)
In this example from the _SAP Fiori apps reference library_ , you see content model elements under _Technical Configuration_ , starting with TC and continuing with BCs, PGs, SP, and BR. The names of the BCs describe the duties, the names of the PGs describe the topics, and the name of the SP and BR is the end users role.
## SAP Fiori Launchpad Content Manager
Let's watch a video to learn about the SAP Fiori launchpad content manager.
Settings
## Catalog Management
![Screenshot flow about copying a catalog in the SAP Fiori launchpad content manager.](../images/71de767a33cb4bfc.png)
Business catalogs can easily be copied in the _SAP Fiori launchpad content manager_ by selecting a catalog and choosing _Copy_. A customizing or workbench request is mandatory. If you select a technical catalog as copy source, a business catalog will be created. For customer catalogs, the new ID must begin with a Z or Y.
Note
It is recommended to prefix the title of the new catalog with the (solution) area separated from the title by a dash. This groups all business catalogs of the same area together in the app finder of the FLP.
The copied catalog consists of references to tiles and target mappings of the source catalog. It is a good starting point when defining own catalogs to start with referencing a catalog shipped by SAP. If SAP ships a new version of a catalog, all references immediately use the new version.
![Screenshot flow about assigning a catalog to a role in the SAP Fiori launchpad content manager.](../images/8642701ae085827c.png)
Since SAP S/4HANA 2023, it is possible to assign catalogs to existing roles in the FLPCM directly without opening the PFCG first. The button is visible when showing the usage of a catalog in roles.
## Copy SAP Fiori Catalogs
### Business Example
You want to create an SAP Fiori business catalog by searching and copying an existing one using the _SAP Fiori launchpad content manager_.

Solution:
    SAP_UX100_BC_S_MIG_DATA_STATUS (Business Catalog)
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names in this exercise include ##, replace ## with the number of your user.
### Prerequisites
The role was created in the exercise **Create SAP Fiori Spaces and Pages**.
### Task 1: Navigate in the SAP Fiori Launchpad Content Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_8C0679E1250E139D:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your SAP S/4HANA (S4H) system, search for an app about data migration status and check its details.
    1. In the _SAP Easy Access_ menu of your S4H, search for _FLP Content Manager: Client-Specific_ or start transaction /UI2/FLPCM_CUST.
    2. In the _SAP Fiori launchpad content manager_ for customizing, choose the _Tiles/Target Mappings_ tab.
    3. In the _Search Tiles/Target Mappings_ field, enter **data migration** and choose _Go_.
    4. In the _Tile / Target Mapping Combinations_ table, select the _Title/Subtitle/Information_**Data Migration Status**.
    5. Choose _Details_ (Magnifier).
#### Result
All details about the _Data Migration Status_ app are displayed.
    6. In the _Details_ window, choose _Close window_.
  2. For the _Data Migration Status_ app, check its usage in roles. Check the details of the _Configuration Expert - Data Migration_ role.
    1. With _Data Migration Status_ selected, choose _Show Usage in Roles_.
    2. In the _Roles_ table, select the _SAP_BR_CONFIG_EXPERT_DATA_MIG_ role.
    3. Choose _Role View_.
    4. In the _Roles_ table, choose _Open in PFCG_.
#### Result
The _SAP_BR_CONFIG_EXPERT_DATA_MIG_ consists of two catalogs, one space, and one group about data migration.
    5. Choose _Exit_ twice.
  3. Display the content of the central business catalog for data migration.
    1. In the _SAP Fiori launchpad content manager_ for customizing, in the _Catalogs assigned to role SAP_BR_CONFIG_EXPERT_DATA_MIG_ table, select the _SAP_CA_BC_MIG_DATA_ catalog.
    2. Choose _Catalog View_.
    3. If the catalog content is not displayed, choose _Show Catalog Content_.
#### Result
The _SAP_CA_BC_MIG_DATA_ catalog consists of four app descriptors.

### Task 2: Copy and Edit a Catalog in the SAP Fiori Launchpad Content Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_868440F97A2F0F9A:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, copy the _SAP_CA_BC_MIG_DATA_ catalog using ID **Z_##_BC_MIG_DATA** and title **Z## - Data Migration Status**.
    1. In the _SAP Fiori launchpad content manager_ for customizing, select the _SAP_CA_BC_MIG_DATA_ catalog.
    2. Choose _Copy_.
    3. In the _New ID_ field, enter **Z_##_BC_MIG_DATA_STATUS**.
    4. In the _New Title_ field, enter **Z## - Data Migration Status**.
    5. Choose _Continue_.
    6. Choose the transport request provided to you.
  2. In the _Z_##_BC_MIG_DATA_STATUS_ catalog, remove the tile and target mapping for the migration cockpit.
    1. In the _Search Catalogs_ field, enter **z_##** and choose _Go_.
    2. In the _Catalogs_ table, select _Z_##_BC_MIG_DATA_STATUS_.
    3. In the _Content in Catalog Z_##_BC_MIG_DATA_STATUS_ table, select _Migrate Your Data - Migration Cockpit / Active Migration Projects_.
    4. Choose _Remove Tiles/Target Mappings_.
    5. In the _Remove References from Catalog_ popup, choose _Continue_.

### Task 3: Assign the Catalog to a Role and Test it in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_E4B763C35E1D29D:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ of your S4H, assign the _Z_##_BC_MIG_DATA_STATUS_ catalog to the _Z_##_BR_TRAINING_ role.
    1. In the _SAP Fiori launchpad content manager_ for customizing, select the _Z_##_BC_MIG_DATA_STATUS_ catalog.
    2. Choose _Show Usage in Roles_.
    3. In the _Roles containing Catalog Z_##_BC_MIG_DATA_STATUS_ table, choose _Assign Role_.
    4. In the _Assign Role to Catalog_ popup, for the _Role ID_ field, open the value help.
    5. In the popup, in the _Single Role_ field, enter **z_##***.
    6. Double-click _Z_##_BR_TRAINING_.
    7. In the _Assign Role to Catalog_ popup, choose _Continue_.
  2. In the _SAP Fiori launchpad_ spaces of your S4H, add the _Data Migration Status_ tile from the _Z## - Data Migration Status_ catalog to your _My Home_ and test it.
    1. Start or reload the _SAP Fiori launchpad_ spaces of your S4H in the client of your choice.
    2. Choose your user in the upper right corner.
    3. In the _User Actions Menu_ , choose _App Finder_.
    4. In the list of catalogs on the left, choose _Z## - Data Migration Status_.
    5. Choose the plus of the _Data Migration Status_ tile.
    6. In the _Select Pages for This Tile_ popup, select _My Home_ and choose _OK_.
    7. Choose _Navigate to Home_.
    8. Choose _Data Migration Status_.
    9. Operate the app as you wish.
