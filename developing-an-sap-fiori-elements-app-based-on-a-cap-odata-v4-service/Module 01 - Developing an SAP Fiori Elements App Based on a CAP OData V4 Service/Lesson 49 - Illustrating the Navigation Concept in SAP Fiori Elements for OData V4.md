# Illustrating the Navigation Concept in SAP Fiori Elements for OData V4

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/examining-internal-and-external-navigation_afe50cc3-c65c-44df-8cea-1ec20c58636f*

Objective
After completing this lesson, you will be able to explain the concept of internal and external navigation in SAP Fiori elements applications.
## SAP Fiori Launchpad
The SAP Fiori launchpad environment is a runtime shell that hosts SAP Fiori applications and provides the applications with services such as navigation, personalization, embedded support, and application configuration.
According to [Fiori for Web Design Guidelines](https://experience.sap.com/fiori-design-web/home-page/), the SAP Fiori launchpad home page must be used for all SAP Fiori apps. It is the main entry point to SAP Fiori apps on mobile and desktop devices.
The SAP Fiori launchpad home page displays tiles and links to launch the apps. It can also show additional information. It is role-based, displaying tiles according to the user's role.
For more information about the SAP Fiori launchpad home page, see <https://experience.sap.com/fiori-design-web/home-page/>
### Local Sandbox Environment
When developing apps in SAP Business Application Studio or Visual Studio Code, you may want to test the app to app navigation. As the SAP Fiori launchpad is not available there, we need a local sandbox environment simulating the SAP Fiori launchpad. This allows you to check if you have completed the necessary steps to make the navigation work from the application side.
In this tutorial, we have implemented a small local sandbox environment simulating the SAP Fiori launchpad. It is used for app-to-app navigation for the exercises of this unit and shouldn't be used for production. This environment uses the internal server module of CAP that allows extending the standard CAP bootstrapping sequence with a custom server.js file. In this file, we load further HTML and JSON files required for building the sandbox SAP Fiori launchpad. In addition, we use the semantic object entries placed at /sap.app/crossNavigation/inbounds/… in the application manifest files (webapp/manifest.json).
There is an option to maintain a semantic object and an action during the app generation process (the step _Fiori Launchpad Configuration_).
These entries are then inserted into the manifest.json file by the Template Wizard.
To learn more about the local sandbox environment, see:
  * [Bootstrapping Servers and Service Providers](https://cap.cloud.sap/docs/node.js/cds-serve)
  * [Run Your Own Applications in the Sandbox](https://help.sap.com/doc/saphelp_nw75/7.5.5/en-US/59/ea851d55e04c69a5ae07b15a3eda1b/content.htm?no_cache=true)
  * [Local Configuration File for the Launchpad Sandbox](https://help.sap.com/doc/saphelp_nw75/7.5.5/en-US/c9/1d091226804dd2b727de4375f0cf1f/content.htm?no_cache=true)

### Production Environment
In the production environment, an administrator would have to set up the SAP Fiori launchpad and configure the navigation targets as described in [Configuring Navigation](https://help.sap.com/docs/SAP_NETWEAVER_750/cc1c7615ee2f4a699a9272453379006c/bd8ae3d327ab4541bcce8e7353c046fc.html?version=7.5.17) and [Setting up Navigation](https://help.sap.com/docs/SAP_NETWEAVER_750/cc1c7615ee2f4a699a9272453379006c/03dbca33e25b44398e13be2f77082e79.html?version=7.5.17).
In this unit, you will explore the different options how you can configure the navigation between your apps.
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
