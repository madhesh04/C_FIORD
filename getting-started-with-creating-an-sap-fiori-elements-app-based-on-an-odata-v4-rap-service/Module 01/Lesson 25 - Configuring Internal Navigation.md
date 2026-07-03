# Configuring Internal Navigation

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-internal-navigation*

Objective
After completing this lesson, you will be able to configure navigation to the subobject page using the page editor.
## Configure Navigation to the Subobject Page
In this exercise, you will add internal navigation to the subobject page. The navigation will be triggered from the _Bookings_ table to display further details of a corresponding booking.
### Prerequisites
You have completed the exercise Add a Bookings Table to the Object Page in the unit Configuring Tables (lesson: Adding a Table to the Object Page).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B4BE8C22E319DEA1:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Right-click _webapp_ from your _travels_ project.
  3. Choose the _Show Page Map_ option from the subsequent menu.
  4. Select the add icon from the _Object Page_ in _Page Editor_.
  5. Select the _Select Page Type_ field from the _Add Page_ dialog box. You can see that it is possible to add navigation to an object page (subobject page), or to a custom page.
  6. _ObjectPage_ is selected by default in the _Select Page Type_ field.
  7. Select the dropdown icon for the _Navigation_ field.
  8. Choose __Booking (BookingType)_ as the value for the field.
  9. Select _Add_ from the _Add Page_ dialog box. You can see that a new object page (subobject page) has been added to the app in the _Page Editor_.
  10. Switch to the app preview in your browser. You can see that there is now a chevron for each table entry of the _Bookings_ table.
  11. Select the first booking. You have navigated to the subobject page. It opens next to the object page because you configured flexible column layout in one of the previous exercises. The subobject page is still empty, so you can just see the technical ID of the selected booking.

### Result
You successfully added internal navigation to the subobject page that provides the details of a booking.
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/getting-an-overview-of-the-navigation-concept-in-sap-fiori-elements-apps)
