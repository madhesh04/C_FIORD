# Creating Business Catalogs

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/creating-business-catalogs_d633c222-3ab4-4e10-8fb8-8db1d2688541*

Objective
After completing this lesson, you will be able to create business catalogs.
## Intent-Based Navigation
The most important part of a tile is its navigation information, which contains an intent that connects to a target mapping.
Watch this video to learn about intent-based navigation.
![Screenshots illustrating the navigation process from FLP to FLPCM where it is processed mapping intent to application and the executing the application.](../images/09c64f4efa5263bc.png)
Target mappings contain the information about which app to start, with what parameters, and on what device types. They are identified by its intent, the combination of semantic object and action. If the user chooses a tile, the intent-based navigation defined in the tile is started. The suitable target mapping then calls the target app that is defined.
![Screenshot of /UI2/SEMOBJ_SAP showing columns for Semantic Object, Semantic Object Name, Applic. Component, and Status with multiple entries marked Active.](../images/9d92cc12f8f611aa.png)
A semantic object represents a business entity such as a customer, a sales order, or a product. Using semantic objects bundles applications that reflect a specific scenario. They allow referring to business entities in a standardized way, abstracting from concrete implementations. A list of all semantic objects delivered by SAP can be accessed using the transaction /UI2/SEMOBJ_SAP. If customers want to define their own semantic objects, they can do so using the transaction /UI2/SEMOBJ. By defining an entry with the same key, customers can overwrite the attributes of a semantic object delivered by SAP.
## References in Catalogs
![Screenshots of tiles and target mappings of a business catalog in the SAP Fiori launchpad content manager.](../images/7c9f05e379dc8db6.png)
SAP delivers numerous catalogs containing many tiles and target mappings. All definitions are tested and distinguished, for example, the different device types the app is working in or include dynamic information in the tiles. All of these can also be referenced in other catalogs such as a new one created by a customer.
![Screenshot flow about referencing to tiles and target mappings in the SAP Fiori launchpad content manager.](../images/94b7da84ea7e0d83.png)
To create a reference to a tile and target mapping in the _SAP Fiori launchpad content manager_ , choose _Add Tiles/Target Mappings_ in the target catalog. In the next screen, search for the app you want to reference in all catalogs of the system. You can create a reference just for the tile, the target mapping, or both.
## Reference Tiles and Target Mappings
### Business Example
You want to create an SAP Fiori business catalog and reference tiles and target mappings from other catalogs.

Solution:
    SAP_UX100_BC_S_EMPLOYEE (Business Catalog)
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names in this exercise include ##, replace ## with the number of your user.
### Prerequisites
The role was created in the exercise **Create SAP Fiori Spaces and Pages**.
### Task 1: Create a Business Catalog in the SAP Fiori Launchpad Content Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_733425A4F4662E9E:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your SAP S/4HANA (S4H) system, create the catalog **Z_##_BC_EMPLOYEE** with the title **Z## - Employee**.
    1. In the _SAP Easy Access_ menu of your S4H, search for _FLP Content Manager: Client-Specific_ or start transaction /UI2/FLPCM_CUST.
    2. Choose _Create_.
    3. In the _Create Catalog_ popup, in the _New ID_ field, enter **Z_##_BC_EMPLOYEE**.
    4. In the _New Title_ field, enter **Z## - Employee**.
    5. Choose _Continue_.
    6. Choose the transport request provided to you.

### Task 2: Reference Tiles and Target Mappings in the SAP Fiori Launchpad Content Manager
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_6547326F8EF8398D:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, in your _Z## - Employee_ catalog, add the tile and target mapping for the app _Manage Business Partner Master Data_.
    1. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, in the _Content in Catalog Z_##_BC_EMPLOYEE_ table, choose _Add Tiles/Target Mappings_ → _Add Tiles/TMs to Selected Catalog_.
    2. In the _Search Tiles/Target Mappings_ field, enter **business partner master** and choose _Go_.
    3. In the _Tiles/Target Mappings Combinations_ table, select the _Action_**manage**.
    4. Choose _Add Tile/TM Reference_.
  2. To your _Z## - Employee_ catalog, add all tiles and target mappings that meet the following conditions:
| Condition  | Value  |
| --- | --- |
| Technical Catalog  | SAP_TC_PLM_COMMON  |
| Semantic Object  | MaterialBOM  |
| SAP Fiori ID  | F1813  |
    1. In the _Search Catalogs_ field, enter **tc_plm** and choose _Go_.
    2. Select _SAP_TC_PLM_COMMON_.
    3. In the _Content in Catalog SAP_TC_PLM_COMMON_ table, choose _Set Filter..._ (Funnel).
    4. In the _Filter_ popup, in the _Column Set_ , double-click _Semantic Object_.
    5. Choose _Define Values_.
    6. For the _Semantic Object_ field, open the value help.
    7. In the popup, double-click _MaterialBOM_.
    8. Choose _Execute_ (Check mark).
    9. Select the _SAP Fiori ID_ column.
    10. Choose _Sort in Ascending Order_.
    11. Select all lines with _SAP Fiori ID_ _F1813_.
    12. Choose _Add Tiles/Target Mappings_ → _Add Selected Tiles/TMs to Other Catalog_.
    13. In the _Search Catalogs_ field, enter **z_##** and choose _Go_.
    14. Select _Z_##_BC_EMPLOYEE_.
    15. Choose _Add Tile/TM Reference_.
    16. In the _Content in Catalog Z_##_BC_EMPLOYEE_ table, choose _Set Filter..._ → _Delete Filter_.

### Task 3: Assign the Employee Catalog to a Role and Test it in the SAP Fiori launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_9AD42E02BE7EFFAC:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, assign the _Z_##_BC_EMPLOYEE_ catalog to the _Z_##_BR_TRAINING_ role.
    1. In the _SAP Fiori launchpad content manager_ for customizing, select the _Z_##_BC_EMPLOYEE_ catalog.
    2. Choose _Show Usage in Roles_.
    3. In the _Roles containing Catalog Z_##_BC_EMPLOYEE_ table, choose _Assign Role_.
    4. In the _Assign Role to Catalog_ popup, for the _Role ID_ field, open the value help.
    5. In the popup, in the _Single Role_ field, enter **z_##***.
    6. Double-click _Z_##_BR_TRAINING_.
    7. In the _Assign Role to Catalog_ popup, choose _Continue_.
  2. In the _SAP Fiori launchpad_ spaces of your S4H, add the _Manage Business Partner Master Data_ and _Maintain Bill Of Material_ tiles from the _Z## - Employee_ catalog to your _My Home_ and test them.
    1. Start or reload the _SAP Fiori launchpad_ spaces of your S4H in the client of your choice.
    2. Choose your user in the upper right corner.
    3. In the _User Actions Menu_ , choose _App Finder_.
    4. In the list of catalogs on the left, choose _Z## - Employee_.
    5. Choose the plus of the _Maintain Bill Of Material_ tile.
    6. In the _Select Pages for This Tile_ popup, select _My Home_ and choose _OK_.
    7. Choose the plus of the _Manage Business Partner Master Data_ tile.
    8. In the _Select Pages for This Tile_ popup, select _My Home_ and choose _OK_.
    9. Choose _Navigate to Home_.
    10. Operate the apps as you wish.
