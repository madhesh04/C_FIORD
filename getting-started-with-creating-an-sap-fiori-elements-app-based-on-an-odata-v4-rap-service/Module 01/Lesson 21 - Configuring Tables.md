# Configuring Tables

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/adding-and-editing-table-columns-of-the-list-report-table*

Objective
After completing this lesson, you will be able to add, edit, delete, or move table columns using the page editor.
## Edit Table Columns of the List Report
In this exercise, you will edit the table columns of the list report. You will do the following:
  * Remove the _Time Stamp_ column.
  * Move the _Overall Status_ column infront of the _Booking Fee_ column.
  * Add a new _Description_ column and placing it after the _Travel ID_ column.

### Prerequisites
You have completed the exercise Enable Initial Load for the List Report Table in the unit Configuring General Settings of List Reports and Object Pages (lesson: Configuring Initial Load Setting for Your App).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B0BDC57DB91E8194:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Right-click _webapp_ from your _travels_ project.
  3. Choose the _Show Page Map_ option from the subsequent menu.
  4. Select the edit icon from _List Report_ to open the _Page Editor_.
  5. Expand _Columns_. You can see all the columns that are currently available in the list report table.
  6. Remove the _Time Stamp_ column.
    1. Select _Time Stamp_ from the _Column_ list. In the right-hand side pane, you can see the settings for the _Time Stamp_ column that you can configure.
    2. Select the delete icon from the highlighted _Time Stamp_ column. The _Delete confirmation_ dialog pops up.
    3. Select _Delete_ from the _Delete confirmation_ dialog. The column is deleted.
  7. Move the _Overall Status_ column before the _Booking Fee_ column.
    1. Select the _Move Up_ icon for the _Overall Status_ column. The column moves up and is placed before _Total Price_.
    2. Select the _Move Up_ icon again for the _Overall Status_ column. It is now placed before the _Booking Fee_ column.
    3. Select the _Edit in source code_ icon to open the annotation.xml. You can see that the @UI.LineItem record for OverallStatus has been moved up and placed before BookingFee.
  8. Add a new _Description_ column and place it after the _Travel ID_ column.
    1. Select the _Columns_ option from the _Page Editor_. The _Columns_ row gets highlighted.
    2. Select the add icon from the end of the highlighted row.
    3. Choose _Add Basics Columns_ from the dropdown list. The _Add Basic Columns_ dialog opens.
    4. Select the dropdown for the _Columns_ field.
    5. Choose _Description_ from the list.
    6. Select _Add_. The _Description_ column is added at the bottom of the list.
    7. Move the _Description_ column up by using the _Move Up_ icon.
    8. Keep moving the column up using the same icon until the _Description_ column is placed directly after the _Travel ID_ column.
    9. Select the _Edit in source code_ icon to open the annotation.xml for the _Description_ column. You can see that the @UI.LineItem record for Description has been added on the second position.
  9. Switch to the app preview in your browser. You can see that a new column _Description_ has been added after the _Travel ID_ column. You can also see that the _Overall Status_ column has been placed before the _Booking Fee_ column.
  10. Select the _Show More per Row_ icon from the table toolbar. You can see that _Time Stamp_ has been removed from the table columns.

### Result
You successfully added and edited certain columns of the list report table using the page editor. You can also do this using the guided development guide Add and Edit Table Columns.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit7ConfiguringTables/lesson1AddingAndEditingTableColumnsOfTheListReportTable/exercise1EditTableColumnsOfTheListReport.md).
