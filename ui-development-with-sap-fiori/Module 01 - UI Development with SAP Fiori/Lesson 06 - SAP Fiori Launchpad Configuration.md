# SAP Fiori Launchpad Configuration

*Source: https://learning.sap.com/courses/ui-development-with-sap-fiori/understanding-the-sap-fiori-launchpad-configuration*

Objective
After completing this lesson, you will be able to understand the SAP Fiori launchpad configuration
## SAP Fiori Launchpad Configuration
After looking at the technical aspects of the SAP Fiori Launchpad, we will now recap how the different objects the SAP Fiori Launchpad configuration are related.
Each User of the SAP Fiori Launchpad is assigned to various Business Roles, based on the assignment the user see Tiles or Links in the SAP Fiori Launchpad. The following figure gives you an overview of the different objects and how they are related.
The configuration of the SAP Fiori launchpad is shown in the figure, Configuration Steps.
![The figure provides an optical representation of the configuration steps.](../images/ce59bcd48206698c.png)![The figure illustrates the recent situation in developing screens.](../images/7873d9d42c879327.png)![The figure illustrates the offering of SAP Fiori 3: Spaces, which consist of Pages, Sections and Tiles.](../images/2e278ff8345499d4.png)
The SAP Fiori 3 spaces concept gives your users stable, well-structured, and personalizable access to their important apps.
A space represents an area of work, typically corresponding to one or more business roles. You can structure each space using one or more pages for various work contexts, and optionally use sections to further group the work within a page.
SAP S/4HANA Cloud comes with space and page templates per business role, making it easy for customers to structure the layout of the SAP Fiori launchpad for their end users. This layout remains stable, even if a user is assigned to more roles later.
For on-premise customers, spaces and pages is supported by the SAP Fiori front-end server 2020 for S/4HANA, which supports S/4HANA releases 1809, 1909 and 2020. Example spaces are only provided for the S/4HANA 2020 on-premise release.
Users can easily personalize their pages, by adding or removing tiles, or adding or removing sections.
Rather than looking at this on a slide, let me show you what it looks like in the system. But before I do that, let me briefly explain how the spaces approach improves on the previous home page approach.
For more, see <https://blogs.sap.com/2020/11/06/sap-fiori-for-sap-s-4hana-best-practices-for-structuring-spaces-and-pages/>
It's important to understand how the objects on the SAP Fiori launchpad relate to eachother.
![Sample SAP Fiori launchpad configuration.](../images/c450614c898b1d0b.png)
Configure the tile by creating a target mapping, a semantic object, and a resulting action.
![Diagram showing the relationship from User to Target Application via Business Role. Links connect Space, Group, Catalog, Page, Tile, Intent \(SemanticObject#Action\), and Target Mapping.](../images/6ed8194037e22097.png)
A tile in the SAP Fiori launchpad doesn't point directly to an SAP Fiori app
A tile points to a target mapping in conjunction with a semantic object and an action.
With this so called **intent** the SAP Fiori Launchpad can resolve the navigation target. The navigation concept is called **intent-based navigation**.
When you create, update, or delete a catalog or a tile, all these actions have to be captured.
If you launch the SAP Fiori launchpad designer in a customization scope, these actions are captured under the customizing request.
![The SAP Fioril launchpad interface showing navigation tabs at the top and six application tiles with titles like Manage Launchpad Apps and SAP Fiori Launchpad Designer.](../images/cb51ca36dc2c7db0.png)
To start a configuration in SAP Fiori Launchpad Designer you need to create a transport request and assign it to a system (SE01)
  * Customizing (CUST)
This layer can be used for testing or other purposes.
  * Workbench (CONF)
All content that you want to deliver to customers must be created in the CONF layer.

Running in customization scope:
<https://server:port/sap/bc/ui5_ui5/sap/arsrvc_upd_admin/main.html?scope=CUST>
You can use transaction /UI2/FLPD_CUST to start the SAP Launchpad Designer in customizing mode.
Running in configuration scope:
<https://server:port/sap/bc/ui5_ui5/sap/arsrvc_upd_admin/main.html?scope=CONF>
You can also use transaction /UI2/FLPD_CONF to start the SAP Launchpad Designer in configuration mode.
![The figure shows the Launchpad Designer.](../images/165519408bf530d1.png)
In the Launchpad Designer, you need to assign whatever changes you make to one of the requests you created in the Gateway system.
Choose the _Tool_![](../images/acd50b6f2c1f90bd.png) icon to open the assignment dialog.
![In the Assign Transport Request, choose OK.](../images/8bc783d46a980310.png)
### To Create a New SAP Fiori Catalog
  1. Choose the ![](../images/464b900a111b8141.png) at the bottom of the screen.
  2. Enter the name and ID of your catalog. (The ID must be in capital letters).
  3. Choose _Save_.

![In the Create Catalog popup, choose Continue.](../images/6445ab1ab97c8faf.png)![Screenshot of the screen, which is used to create a target mapping.](../images/1acc148eb6933043.png)![Options for creating a tile in the SAP Fiori launchpad.](../images/1acc148eb6933043.png)![The screenshot shows the Manage Launchpad Spaces App.](../images/8cd91d04e5acc141.png)![To create a new Space, you have to fill in this pop-up, containing information about the Space ID, a Space Description and further details.](../images/1680fc74ab4416ba.png)![Here, you can edit the page content.](../images/7e42d73798476aa5.png)![Set the page visibility to Hidden or Visible.](../images/fe502aab782c16e7.png)
Run transaction PFCG and create a new role.
Add a new role of type _SAP Fiori Tile Catalog_.
![Assign content, such as Launchpad Catalog, Launchpad Group, or Launchpad Space.](../images/e7dbfd1788cc43c5.png)![Add a Space ID and choose Continue.](../images/26cfb784a12c2c0b.png)![In the popup, add a Catalog ID.](../images/ac7bfba7ba979d94.png)![In the User Assignments list, add a User ID.](../images/63c3ab5045e9af97.png)![Select the Use Spaces checkbox.](../images/6ba5809f74a7685f.png)![Sample space in the SAP Fiori launchpad.](../images/56f477b01799f15f.png)
To create dynamic tiles, it is important to understand the anatomy of a tile.
![Graphic explaining components of a dynamic tile.](../images/66ed00cf28f76ba7.png)
With this in mind, it is possible to build a service that provides structured information that can be shown on the tile dynamically.
When using dynamic tiles, you need to keep in mind that requests to get tile data create network traffic. The load created, in some cases, may be a heavy load on the system. This might lead to weak performance.![Options for configuring an app launcher, with fields for general settings, dynamic data, navigation, and tile actions; includes input boxes for text, URLs, and parameters with options to add or remove items.](../images/dfc1a91231d703b2.png)
It is also possible to implement a complete dynamic tile.
![Sample dynamic tile.](../images/b4f09cf5e5f55eb8.png)
Implement an OData service in the back-end system
Register the OData service on the front-end server.
![Screenshot of the SAP Gateway Service Builder interface showing a data model with entity properties, attributes like type, precision, scale, and other metadata in a tabular format.](../images/cf16cf609289b470.png)
For the second step, configure the dynamic tile. Make sure the result of the service invocation is in the JSON format.
![In the Service URL field, the service invocation is in the JSON format.](../images/055ba07503f24d94.png)
## Semantic Objects
Semantic objects can be created using the transaction /ui2/semobj.
![Semantic objects, using the /ui2/semobj transaction.](../images/035bfc51fd6777bd.png)
The figure shows the configuration of four semantic objects. Please be careful using the transaction **/ui2/semobj** , changes are not client specific. After the configuration of the semantic object the semantic object can be used during the target mapping configuration
![configure: Target Mapping screen, as described in the following text.](../images/d44686581977b9f6.png)
As you can see in the figure, the configuration of the target mapping contains the semantic object as created before. The action **display** was chosen from the list of predefined actions. It is very important to understand that the value of the action has no direct influence on the behavior of the application. In the example here the configured application does not start in the display-mode. But the developer can fetch later during runtime the action value and influence the behavior of the application by code e.g. start the application in display mode.
As you also can see in the target mapping we only add the application id of the SAPUI5 application to the target mapping configuration.
After the target mapping configuration we have to create tile.
![Sample tile configuration, as described in the following text.](../images/c017f4fe7deb70a2.png)
The figure shows a tile configuration. As you can see we are using the semantic object and action that was previously assigned to a specific application during the target mapping configuration. As you also see is that in the field Target URL the value **#UX410NavStart00-display** is shown. This hash value will be used to address the target application during navigation.
The following section will cover how to configure tiles and target mappings in the SAP Fiori Launchpad.
### Create Tiles and Target Mappings
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_312B960D7F11E1BF:uebung)
