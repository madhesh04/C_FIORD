# Configuring General Settings of List Reports and Object Pages

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-the-flexible-column-layout*

Objective
After completing this lesson, you will be able to enable the flexible column layout on the UI for your app.
## The Flexible Column Layout
In SAP Fiori elements, the flexible column layout allows you to view both the list report and the object page in the same screen, without navigating back and forth between them.
![TwoColumnsBeginExpanded option of the flexible column layout](../images/54dba6ff846d54ab.png)
You can also display two object pages next to a list report. Each page is displayed in its own column, and you can adjust the column width if necessary.
![ThreeColumnsMidExpanded option of the flexible column layout](../images/dc90d832fe7b2ea6.png)
The flexible column layout can be configured manually in the manifest.json file. You can also configure the layout using the Page Map. For more information, please refer to the SAP Fiori elements documentation: [Enabling the Flexible Column Layout](https://sapui5.hana.ondemand.com/sdk/#/topic/e762257125b34513b0859faa1610b09e)
## Enable the Flexible Column Layout
In this exercise, you will enable the flexible column layout for your Manage Travels application.
### Prerequisites
You have completed the exercise Create the Manage Travels App in the unit Getting an Overview of SAP Fiori tools (lesson: Creating an SAP Fiori Elements App Using the Application Generator).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_30DAC77EEFBB288D:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. You have the _EXPLORER_ tab open.
  3. Right-click _webapp_ from your _travels_ project.
  4. Select the _Show Page Map_ option.
  5. The SAP Fiori tools page map opens. You can configure different settings for your app using this tool.
  6. Choose the _Flexible Column Layout_ option from the right-hand side menu.
  7. Select a layout from the following two options:
     * _Select Layout for 2 Columns_
Offers a layout if a list report and an object page are opened.
     * _Select Layout for 3 Columns_
Offers a layout if a list report, an object page, and a subobject page are opened.
  8. Select the _Mid-Expanded_ option from the 2 column layout.
  9. Select the _End-Expanded_ option from the 3 column layout.
  10. You have now configured the _Flexible Column Layout_ with _Mid-Expanded_ for 2 column layout and _End-Expanded_ for 3 column layout.
  11. Switch to the app preview in your browser.
  12. Select the _Go_ option from your list report.
  13. Select a travel. The object page for that travel opens. You can see that the object page opens next to the list report on the same screen.
  14. Select the chevrons present between the list report and object page to expand either of them.
  15. Select the _Close_ option for the object page from the right-hand side.

### Result
You successfully configured the flexible column layout.
