# Examining the Flexible Programming Model

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/getting-an-overview-of-the-flexible-programming-model*

Objective
After completing this lesson, you will be able to identify the main components of the flexible programming Model.
## The Flexibility of the Programming Model
In the previous units of this course, you have mostly used SAP Fiori tools to configure the features of SAP Fiori elements. Under the hood, these tools have added UI annotations and manifest.json settings to your app, but you haven't written any UI code so far. These tools are designed to cover most business scenarios you may come across.
At times, however, you may need more flexibility, introducing some custom code or custom controller logic. SAP Fiori elements supports this through the flexibility built into its programming model. This flexibility has been available starting with SAPUI5 version 1.94.
When extending your SAP Fiori elements apps using the flexibility of the programming model, you may be sure that your extensions remain stable as SAP Fiori elements evolves.
Settings
You can use the _SAP Fiori development portal_ to interactively explore all the available SAP Fiori elements features and capabilities, both standard and extension possibilities. With live editing, you can do the following:
  * Change annotations and instantly see how they alter the user interface.
  * Test different configuration combinations.
  * Discover how metadata drives UI behavior.
  * Explore safely in a sandbox environment, isolated from your own projects.

How to access the _SAP Fiori development portal_ :
  1. Open the _UI5 Demo Kit_ at <https://sapui5.hana.ondemand.com/>.
  2. In the top navigation, select _Resources_.
  3. In the _Development Tools_ section, select _SAP Fiori development portal_.
Note
In some places, it may still appear under its former name, _flexible programming model explorer_.

The _SAP Fiori development portal_ groups everything you need into four main areas, each supporting a different aspect of SAP Fiori app development.
  * _Building Blocks_ : This section covers the core UI components—from the basic _field_ used in most applications to advanced elements such as _tables_ and _charts_. Each standard floorplan consists internally of building blocks. Every building block comes with built-in, enterprise-grade features you’d otherwise spend months building yourself.
  * _Global Patterns_ : These are the behind-the-scenes essentials - non-visual building blocks that make your app production-ready: draft saving, in-app and cross-app navigation, and solid error handling. Use them to deliver the reliability users expect from SAP solutions.
  * _Standard Floorplans_ : Need a proven layout quickly? This area offers ready-made page types for common scenarios (like List Report and Object Page). They’re based on years of UX research, giving you consistency and speed. You’ll also see where you can plug in extensions with SAP Fiori elements. If your app is close to a standard floorplan, extending it using extension points is the fastest way to the finish line.
  * _Custom Pages_ : For unique requirements, this section explains how to assemble visual and non-visual building blocks to craft custom layouts without losing enterprise features or annotation-based advantages.

The extension capabilities for SAP Fiori elements for OData V4 applications include:
  * EXTENSION POINTS. They are "hooks" for the SAP Fiori elements framework. They are containers which you can use to implement your own UI, such as custom sections or custom pages.
  * BUILDING BLOCKS. They are reusable pieces of code provided by SAP Fiori elements, such as the _table_ building block. You can use them in your own extension points.
  * CONTROLLER EXTENSIONS. They are methods that let you override or augment standard logic with custom code - for example, implementing event handlers, lifecycle hooks, validations, and navigation or edit-flow behavior. SAP Fiori elements provides the Extension API, which offers comprehensive capabilities for extending list report and object page applications. Use the Extension API as the sole, supported interface for extending list report and object page applications. Do not access or manipulate internal methods or controls directly, as they are not public APIs and can change without notice, which will break your application during future upgrades.

### Summary
In this lesson, you have learned that the SAP Fiori elements programming model for OData V4 is flexible enough to add custom logic and UI controls beyond the standard features. By using the documented extension points and the Extension API provided in the _SAP Fiori development portal_ , your extensions remain stable, upgrade-safe, and consistent with the framework.
### Further Reading
[SAP Fiori Development Portal](https://sapui5.hana.ondemand.com/test-resources/sap/fe/core/fpmExplorer/index.html)
[Introducing the SAP Fiori Development Portal: Your Gateway to Rapid SAP Fiori App Creation (1 of 6)](https://community.sap.com/t5/technology-blog-posts-by-sap/introducing-the-sap-fiori-development-portal-your-gateway-to-rapid-sap/ba-p/14236768)
[Get familiar with SAP Fiori Development Portal and the Power of the Building Blocks (2 of 6)](https://community.sap.com/t5/technology-blog-posts-by-sap/get-familiar-with-sap-fiori-development-portal-and-the-power-of-the/ba-p/14240041)
[Extension API for list reports in SAP Fiori elements for OData V4](https://sapui5.hana.ondemand.com/sdk/#/api/sap.fe.templates.ListReport.ExtensionAPI)
[Extension API for object pages on SAP Fiori elements for OData V4](https://sapui5.hana.ondemand.com/sdk/#/api/sap.fe.templates.ObjectPage.ExtensionAPI)
