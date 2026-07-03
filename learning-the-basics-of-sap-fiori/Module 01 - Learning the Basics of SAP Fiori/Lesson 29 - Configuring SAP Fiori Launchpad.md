# Configuring SAP Fiori Launchpad

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/configuring-sap-fiori-launchpad_be40d546-d8f8-4a6b-b69f-7c77e1a0e9e1*

Objective
After completing this lesson, you will be able to configure SAP Fiori launchpad.
## Configuration Options
![The image details configuration approaches. FLP Configurations include basic configuration, personalization, and runtime adaptation. Additional configurations cover user assistance, notifications, and support.](../images/b5741688ca3e9c36.png)
The _SAP Fiori launchpad (FLP)_ has many configuration options. There are several basic configurations and also advanced configurations needing other additional technical settings elsewhere. The configurations depend on the release of the software component SAP_UI. There are two approaches to configure the FLP:

Customer settings
    Define customer settings using the transaction /UI2/FLP_CUS_CONF. This is recommended since SAP S/4HANA 1809. These settings are valid for one system client.

Target Mapping
    Define target mappings in catalogs. This is recommended since SAPUI5 1.40. These catalogs can then be assigned to users via roles as usual.
Note
Originally, it was also possible to create and upload a configuration file as a third option. This option is deprecated since SAPUI5 1.40 and was removed with SAP S/4HANA 2022.
To configure the additional settings needed for context-sensitive user assistance, notifications, and contact support, consult the SAP online documentation for your system release or ask your system administrator.
### SAP Fiori Launchpad Customer Settings
Watch the video to understand SAP Fiori Launchpad Customer Settings.
Note
The transaction /UI2/FLP_SYS_CONF allows the configuration of the FLP for all clients. However, these settings are saved in the SAP namespace. They count as modifications, including all the drawbacks.
### SAP Fiori Launchpad Configuration via Custom Catalog
![Screenshots of an app descriptor in a technical catalog configuring the system info bar of the SAP Fiori launchpad. Highlighted fields are for the semantic object Shell, the action bootConfig, any value for componint ID, no tile checkbox, and configuration parameters list.](../images/6faeded5bca0d01b.png)
Target mappings for configuring the FLP can be created in any catalog. However, it is recommended that you use a separate one without any tiles or target mappings for apps. The semantic object for the FLP is **Shell** , followed by an action depending on the FLP part. The action **bootConfig** is meant for general settings of the FLP. The application type is **SAPUI5 Fiori App** , followed by a freely selectable component ID. The settings themselves are created using parameters of the target mapping and depend on the system release. A full list of available settings per system release can be found in the _SAP Fiori launchpad_ documentation on <https://help.sap.com/docs/SAP_FIORI_LAUNCHPAD>.
![Screenshot of target mapping in SAP Fiori launchpad designer showing settings and parameters for disabling personalization in SAPUI5 Fiori App with predefined intent 'Shell, bootConfig' and various configuration options.](../images/d2d21756638fd3f3.png)
For some configuration areas, SAP delivers predefined catalogs that already consist of target mappings with parameters. These catalogs can be assigned directly to roles to enable a certain feature set, or they can be copied in the customer namespace to change the default values to meet someone's needs. Depending on the release, these catalogs are delivered as business or technical catalogs and must be handled accordingly.
For example, assigning the _/UI2/CONFIG_PERS_OFF_ business catalog to a role deactivates the personalization options of the FLP for all users assigned to the role. Only accessibility features are still possible and the _My Home_ page in spaces can still be changed. But there is no access anymore to the app finder.
Hint
The _My Home_ page in spaces can be deactivated by setting **SPACES_MYHOME** to **false** in the /UI2/FLP_CUS_CONF transaction.
Note
For more information about this topic, see:
Configuring the SAP Fiori Launchpad for SAP S/4HANA (Learning Video)
<https://learning.sap.com/videos/configuring-the-sap-fiori-launchpad-for-sap-s-4hana>
## How to Configure SAP Fiori Launchpad
### Business Example
You want to move buttons from the user actions menu to the page header of the _SAP Fiori launchpad_.
Watch the video to see how to configure the SAP Fiori Launchpad.
Settings
## Deactivate Personalization
### Business Example
You want to manage the personalization options of the _SAP Fiori launchpad_ for a certain group of users.

Solution:
    SAP_BR_UX100_S_RESTRICTED (Role)     SAP_UX100_BC_S_PERS_OFF (Catalog)
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names include ##, replace ## with the number of your user.
### Task 1: Copy and Edit the Catalog for Disabling Personalization
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_66D17DAF4B062D94:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your SAP S/4HANA (S4H) system, copy the _/UI2/CONFIG_PERS_OFF_ catalog using ID **Z_##_BC_PERS_OFF** and title **Z## - Disable Personalization**.
    1. In the _SAP Easy Access_ menu of your S4H, search for _FLP Content Manager: Client-Specific_ or start transaction /UI2/FLPCM_CUST.
    2. In the _Search Catalogs_ field, enter **pers** and choose _Go_.
    3. Select the _/UI2/CONFIG_PERS_OFF_ catalog.
    4. Choose _Copy_.
    5. In the _New ID_ field, enter **Z_##_BC_PERS_OFF**.
    6. In the _New Title_ field, enter **Z## - Disable Personalization**.
    7. Choose _Continue_.
    8. Choose the transport request provided to you.
  2. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, open the _Z_##_BC_PERS_OFF_ in the _SAP Fiori launchpad designer_ for customizing and assign a transport request in the settings.
Note
Close the _SAP Fiori launchpad content manager_ to release the lock.
    1. In the _SAP Fiori launchpad content manager_ for customizing, select the _Z_##_BC_PERS_OFF_ catalog.
    2. Choose _Open in Designer_.
    3. Close the _SAP Fiori launchpad content manager_.
    4. In the _SAP Fiori launchpad designer_ for customizing, choose _Settings_ (gearwheel) in the upper right corner.
    5. In the _Assign Transport Request_ popup, deselect the _None (Local Object)_ checkbox.
    6. In the _Customizing Request_ dropdown, select the transport request provided to you.
    7. Choose _OK_.

### Task 2: Edit Parameters of a Target Mapping in the SAP Fiori Launchpad Designer
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_843F249630CA6280:uebung)
#### Steps
  1. In the _SAP Fiori launchpad designer_ for customizing of your S4H, in the target mapping for the _Shell_ semantic object of the _Z_##_PERS_OFF_ catalog, change the default value of the _renderers/fiori2/componentData/config/enableSetTheme_ parameter to **true**.
Caution
If you get an error when saving the catalog, close the _SAP Fiori launchpad content manager_ to release the lock.
    1. In the _SAP Fiori launchpad designer_ for customizing of your S4H, in the _Z_##_BC_PERS_OFF_ catalog, choose _Target Mappings_ at the top of the page.
    2. Select the _Semantic Object_**Shell** with _Action_**bootConfig** .
    3. Choose _Configure_.
    4. Enlarge the width of the _Name_ column of the _Parameters_ table until you can fully read the names.
    5. In the _Default Value_ cell of the _renderers/fiori2/componentData/config/enableSetTheme_ parameter, enter **true**.
    6. Choose _Save_.
    7. In the _Confirmation_ popup about breaking the reference, choose _OK_.
Caution
If you get an error when saving the catalog, close the _SAP Fiori launchpad content manager_ to release the lock.

### Task 3: Create a Business Role, Add the Catalog, and Test it in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_9817501C3B51CC8A:uebung)
#### Steps
  1. Create the role **Z_##_BR_RESTRICTED** in the _Role Maintenance_ (PFCG) of your S4H. Assign the role to your user.
    1. In the _SAP Easy Access_ menu of your S4H, search for _Role Maintenance_ or start transaction PFCG.
    2. In the _Role_ field, enter **Z_##_BR_RESTRICTED**.
    3. Choose _Create Single Role_.
    4. In the _Description_ field, enter **Restricted ##**.
    5. Choose _Save_.
    6. Choose the _User_ tab.
    7. In the _User ID_ field, enter your user.
    8. Choose _Save_.
  2. Add the _Z_##_BC_PERS_OFF_ catalog to the menu of the _Z_##_BR_RESTRICTED_ role in the Role Maintenance (PFCG) of your S4H.
    1. Choose the _Menu_ tab.
    2. Expand the _Insert Node_ button.
Hint
The initial value written on the _Insert Node_ button is _Transaction_.
    3. Choose _SAP Fiori Launchpad_ → _Launchpad Catalog_.
    4. In the _Catalog ID_ field, enter **z_##*** and use the value help.
    5. In the popup, double-click _Z_##_BC_PERS_OFF_.
    6. Choose _Continue_.
Note
If _Warnings and/or errors happened during evaluation of the catalog details_ appears in a pop-up, choose _No_ to continue.
    7. Choose _Save_.
  3. Test if the personalization in the _SAP Fiori launchpad_ spaces of your S4H is disabled and changing the theme is still possible.
Note
To enable personalization again for later exercises, go back to transaction PFCG and remove your user from the role _Z_##_BR_RESTRICTED_.
    1. Start or reload the _SAP Fiori launchpad_ of your S4H in the client of your choice.
    2. Choose the _Cross Topic_ space.
    3. Choose your user in the upper right corner.
#### Result
The _App Finder_ button disappeared and the _Edit Current Page_ button is renamed to _Add Tiles to My Home_.
    4. In the _User Actions Menu_ , choose _Settings_.
    5. Choose _Appearance_.
    6. Select a _Theme_ of your choice.
    7. Choose _Save_.
Note
To enable personalization again for later exercises, go back to transaction PFCG and remove your user from the role _Z_##_BR_RESTRICTED_.
