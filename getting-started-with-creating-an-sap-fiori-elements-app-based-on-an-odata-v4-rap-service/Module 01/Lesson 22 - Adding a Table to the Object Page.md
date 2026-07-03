# Adding a Table to the Object Page

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/adding-a-table-to-the-object-page*

Objective
After completing this lesson, you will be able to add a table to your application.
## Add a Bookings Table to the Object Page
In this exercise, you will add a table displaying the bookings of a travel. It will be displayed in a separate section underneath the _General Information_ section on the object page.
### Prerequisites
You have completed the exercise Edit Table Columns of the List Report in the same unit (lesson: Adding and Editing Table Columns of the List Report Table).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_8EDD8363D60D09D:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Right-click _webapp_ from your _travels_ project.
  3. Choose the _Show Page Map_ option from the subsequent menu.
  4. Enter _Bookings_ as a section in the object page.
    1. Select the edit icon from _Object Page_ to open the _Page Editor_.
    2. Select the add icon from _Sections_.
    3. Choose _Add Table Section_ from the dropdown list.
    4. Add _Bookings_ as the _Label_ in the subsequent _Add Table Section_ dialog.
    5. Select the global icon within the Label field.
    6. Select _Apply_ from the subsequent popup.
    7. Select the dropdown for the _Value Source_ field.
    8. Select the __Booking_ option.
    9. Select _Add_ from the _Add Table Section_ dialog. You can now see _Bookings_ added as a section after _General Information_ in the _Page Editor_.
  5. Choose the fields that you want to display as the table columns in the _Bookings_ section.
    1. Expand the _Bookings_ section within the _Page Editor_.
    2. Expand _Table_ within the _Bookings_ section.
    3. Select _Columns_.
    4. Select the add icon from the highlighted _Columns_ row.
    5. Select _Add Basic Columns_ from the list.
    6. Select the following columns that can be displayed in the _Bookings_ section:
       * _BookingID_
       * _BookingDate_
       * _CarrierID_
       * _ConnectionID_
       * _CustomerID_
       * _FlightDate_
       * _FlightPrice_
    7. Select _Add_ from the dialog box. You can see all the selected columns are now added within _Bookings_.
  6. Look up the generated annotations for the _Bookings_ section and the table that you have configured in the previous steps.
    1. Select the _Bookings_ section from the _Page Editor_.
    2. Select the _Edit in source code_ icon to open the annotation.xml for the _Bookings_ section. You can see that a new record of the _@UI.Facets_ annotation has been added to display a new section.
    3. The annotation is of type UI.ReferenceFacet. The label references the generated entry in the i18n file. The target references @UI.LineItem, with the qualifier as i18nbookings annotating the Booking entity.
    4. Press CTRL+ LEFT MOUSE CLICK on the UI.LineItem to navigate to the UI.LineItem definition.
    5. Switch to the app preview in your browser. You can see the _Bookings_ section under the _General Information_ section. The _Bookings_ section contains the table with the columns that you have configured.
  7. Display the customer’s last name along with the _Customer ID_.
    1. Switch to SAP Business Application Studio.
    2. Select the _Customer ID_ column from the _Page Editor_.
    3. Select the dropdown for the _Text_ from the right-hand side pane.
    4. Select __Customer/LastName_ option from the list. You have now updated the _Customer ID_ column to display the customer's last name.
  8. Change the column label from _Customer ID_ to _Customer_.
    1. Enter **Customer** in the _Label_ field on the right-hand side pane for the _Customer ID_ column.
    2. Select the global icon from the _Label_ field.
    3. Select _Apply_ from the subsequent popup. You have now changed the column label from _Customer ID_ to _Customer_.
  9. Change the column label from _Airline ID_ to _Airline_.
    1. Select the _Airline ID_ column from the _Page Editor_.
    2. Enter **Airline** in the _Label_ field on the right-hand side pane of the selected column.
    3. Select the global icon from the _Label_ field.
    4. Select _Apply_ from the subsequent popup. The column label is now changed to _Airline_.
  10. Display the airline name in addition to the airline abbreviation
    1. Select the dropdown within the _Text_ field from the right-hand side pane.
    2. Select __Carrier/Name_ from the list.
    3. Select the _Edit in source code_ icon for the _Text_ field to open the annotation.xml file. You can see that a corresponding Common.Text annotation has been added for CarrierID to the local annotation file.
  11. Switch to the app preview in your browser. You can see that the airline name is now displayed in addition to the abbreviation. The column name is now changed to _Airline_. Also, along with the _Customer ID_ , the customer's name is also displayed. The column title has been updated to _Customer_.
  12. Remove the _Customer ID_ from the _Customer_ column.
    1. Switch to SAP Business Application Studio.
    2. Select the _Customer_ column.
    3. Select the dropdown of the _Text Arrangement_ field from the right-hand side pane.
    4. Choose the _Text Only_ option from the list.
    5. Select the _Edit in source code_ icon. You can see that the UI.TextArrangement annotation with TextOnly has been added to Customer ID. This means that only the customer's name is displayed and the ID remains hidden.
    6. Switch to the app preview of your browser. You can see that the customer ID is now hidden.
  13. Add a picture of the airline logo in a new column at the beginning of the bookings table.
    1. Switch to SAP Business Application Studio.
    2. Select _Columns_ from the _Page Editor_.
    3. Select the add icon from the highlighted row.
    4. Select _Add Basic Columns_ from the list.
    5. Select the dropdown from the _Columns_ field of the _Add Basic Column_ dialog box.
    6. Choose _AirlinePicURL_ from the list.
    7. Select _Add_ from the _Add Basic Column_ dialog box. You can see that a new field _Airline Logo_ has been added to the _Columns_ list.
    8. Select the _Move up_ icon for the _Airline Logo_ row to move the column up in the list of columns.
    9. Keep moving the column up the list until _Airline Logo_ is at the top of the _Columns_ list.
    10. Select the _Edit in source code_ icon for _Airline Logo_. You can see that the record for the Airline Logo has been added to UI.LineItem.
    11. Switch to the app preview of your browser. You can see that the _Airline Logo_ column is displayed.
    12. Switch to SAP Business Application Studio.
    13. Select the _Airline Logo_ column from the _Page Editor_.
    14. Remove _Airline Logo_ from the _Label_ field on the right-hand side pane for the column.
    15. Switch to the app preview of your browser. You can see that the _Airline Logo_ column title is now removed.
    16. Choose the _Show More per Row_ icon to view all the relevant details for the _Bookings_.

### Result
You successfully added the bookings table to the object page of the _Manage Travels_ app using the _Page Editor_. You can also do this using the guided development guide Add and Edit Table Columns.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit7ConfiguringTables/lesson2AddingATableToTheObjectPage/exercise1AddBookingsTableToTheObjectPage.md).
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-tables)
