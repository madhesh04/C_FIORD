# Configuring Object Pages

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-the-header-area-of-the-object-page*

Objective
After completing this lesson, you will be able to add elements to the object page header, such as a title, an image, or a section.
## Set Up the Subobject Page Header
In this exercise, you will fill the subobject page, that you created in the previous exercise, with the data relevant to the booking. For now, only the technical ID is displayed on the page since the subobject page is not configured. You will add the following to the page:
  * Booking ID as the page title.
  * Airline logo as an image.
  * Data point sections displaying the name of the airline, departure time, departure airport, arrival time, and destination airport.

### Prerequisites
You have completed the exercise Configure Navigation to the Subobject Page in the unit Getting an Overview of the Navigation Concept in SAP Fiori Elements Apps (lesson: Configuring Internal Navigation).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_577FA1F2779B1E97:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Right-click on the _travels_ project of your _EXPLORER_.
  3. Choose the _Show Page Map_ option from the subsequent menu.
  4. Set the booking ID and the airline logo as the page title.
    1. Select the edit icon for the _Travel_BookingObjectPage_ of the _Page Editor_.
    2. Select the _Header_ option for the object page. The right-hand side pane opens where you can manage different settings for the header.
    3. Enter **Booking** as the _Type Name_. This is the name of the subobject page.
    4. Select the global icon from the _Type Name_ field.
    5. Select _Apply_ from the subsequent popup.
    6. Select the dropdown from the _Title_ field.
    7. Choose _BookingID_ from the list.
    8. Select the dropdown from the _Image_ field from the right-hand side pane.
    9. Choose __Carrier/AirlinePicURL_ from the list.
    10. Switch to the app preview in your browser. You can see that the airline logo and the booking ID have been added to the header of the subobject page.
  5. Add data point sections displaying the name of the airline, departure time, departure airport, arrival time, and destination airport to the header.
    1. Select the add option from the _Header Sections_ of _Travel_BookingObjectPage_ in _Page Editor_.
    2. Choose _Add Data Point Section_ from the list.
    3. Select the dropdown icon for the _Value Source Property_ field within the _Add Data Point Section_ dialog box.
    4. Choose the following properties from the __Connection_ list:
       * _AirlineID_Text_
       * _DepartureTime_
       * _DepartureAirport_
       * _ArrivalTime_
       * _DestinationAirport_
    5. Select _Add_ from the _Add Data Point Section_ dialog box. You can see that all the selected properties are listed within the _Header Sections_.
    6. Select _AirlineID_Text_ from the list.
    7. Enter **Airline** as the label within the _Label_ field on the right-hand pane.
    8. Select the global icon from the _Label_ field.
    9. Select _Apply_ from the subsequent popup.
    10. Select _Departure Time_ from the _Header Sections_ list.
    11. Enter **Departure Time** as the label within the _Label_ field on the right-hand pane.
    12. Select the global icon from the _Label_ field.
    13. Select _Apply_ from the subsequent popup.
    14. Select _Departure Airport_ from the _Header Sections_ list.
    15. Enter **Departure Airport** as the label within the _Label_ field on the right-hand pane.
    16. Select the global icon from the _Label_ field.
    17. Select _Apply_ from the subsequent popup.
    18. Select _Arrival Time_ from the _Header Sections_ list.
    19. Enter **Arrival Time** as the label within the _Label_ field on the right-hand pane.
    20. Select the global icon from the _Label_ field.
    21. Select _Apply_ from the subsequent popup.
    22. Select _Destination Airport_ from the _Header Sections_ list.
    23. Enter **Destination Airport** as the label within the _Label_ field on the right-hand pane.
    24. Select the global icon from the _Label_ field.
    25. Select _Apply_ from the subsequent popup.
    26. You have now created the header sections and have maintained their labels.
  6. Select the _Edit in source code_ icon for the _Header_ row of _Travel_BookingObjectPage_.
  7. You can see that the Page Editor has added UI.HeaderInfo annotation for the header.
  8. Select the _Header Sections_ row from the _Page Editor_.
  9. Select the _Edit in source code_ icon for the _Header Sections_.
  10. You can see that the _Page Editor_ has added UI.HeaderFacets records for the five data point sections. Each of them references a corresponding UI.DataPoint annotation.
  11. Scroll down to see the corresponding UI.DataPoint annotations.
  12. Switch to the app preview in your browser. You can see that the five data point sections have been added to the subobject page header.
  13. Select the right chevron to expand the object page.
  14. Select the left chevron to expand the subobject page.
  15. Select the full screen icon from the subobject page to expand it. You have observed the responsive behavior of the subobject page. As the list report is not visible now, the title of the subobject page gets displayed.

### Result
You successfully configured the subobject page header using the _Page Editor_. You can also configure the subobject page using the guided development guides Configure object page header and Add a header facet to an object page using data points.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit9ConfiguringObjectPages/lesson1ConfiguringTheHeaderAreaOfTheObjectPage/exercise1SetUpTheSubobjectPageHeader.md).
