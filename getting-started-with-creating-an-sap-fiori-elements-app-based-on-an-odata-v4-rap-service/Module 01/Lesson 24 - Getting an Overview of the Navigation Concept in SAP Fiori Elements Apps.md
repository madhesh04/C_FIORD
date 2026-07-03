# Getting an Overview of the Navigation Concept in SAP Fiori Elements Apps

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/examining-external-and-internal-navigation*

Objective
After completing this lesson, you will be able to explain the concept of internal and external navigation in SAP Fiori Elements applications.
## Navigation Inside the Application (Internal Navigation)
In the previous exercises, you have seen internal navigation, that is, navigation inside one app. Examples include navigation from the list report to its object page or from the object page to the subobject page. You can use the _Page Map_ to configure internal navigation and add new pages or remove existing ones. You can also add a custom page. For more information, see [Define Application Structure](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/bae38e6216754a76896b926a3d6ac3a9.html).
Other configuration options include navigation after executing an action, navigation between entities of an app and in-page navigation. For more information, see [Configuring Internal Navigation](https://ui5.sap.com/#/topic/2c65f07f44094012a511d6bd83f50f2d.html).
## Navigation Between Applications (External Navigation)
Besides navigation inside an app, you can also build a navigation flow connecting different apps. It is called external navigation.
There are several configuration options for external navigation:
  * Navigation using links. This is used to open other objects or lists. Links can be used both in the list report and on the object page (in forms or tables).
  * Navigation using line items in a table. This is used to display additional details of an item. This will replace the standard internal navigation with external navigation to another app. For more information, see [Changing Navigation to Object Page](https://ui5.sap.com/#/topic/8bd546e27a5f41cea6e251ba04534d70).
  * Navigation using a button action.

For more information about external navigation, check the [SAP Fiori for Web Design Guidelines](https://experience.sap.com/fiori-design-web/navigation/).
Note
To use external navigation, you need the SAP Fiori launchpad.
## Intents
Navigation inside the SAP Fiori launchpad environment is based on abstract representations called intents. They are resolved to specific navigation targets at runtime.
Each intent consists of a semantic object and an action. It may also have semantic object parameters. Semantic objects represent business entities such as a product, a travel, or a customer. Actions are operations which the user can perform on a semantic object, such as display or manage. This allows you to build groups of apps that perform different actions on the same business entity, such as display travels or manage travels.
An intent can be resolved differently based on the role of the user that triggers the navigation.
For more information, see [Configuring Navigation](https://help.sap.com/docs/SAP_NETWEAVER_750/cc1c7615ee2f4a699a9272453379006c/bd8ae3d327ab4541bcce8e7353c046fc.html?version=7.5.17).
An administrator configures the apps as navigation targets. For more information, see [Setting up Navigation](https://help.sap.com/docs/SAP_NETWEAVER_750/cc1c7615ee2f4a699a9272453379006c/03dbca33e25b44398e13be2f77082e79.html?version=7.5.17).
### Further Reading
[Configuring Navigation](https://ui5.sap.com/#/topic/a42427550b72436a8bdf53045b06effb)
