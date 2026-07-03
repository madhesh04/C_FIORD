# Configuring Sections of the Object Page Body

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-sections-of-the-object-page-body*

Objective
After completing this lesson, you will be able to add sections to object pages.
## Add Plane Details Section to the Subobject Page Body
In this exercise, you will add a section to the subobject page body containing the plane details.
### Prerequisites
You have completed the exercise Set Up the Subobject Page Header in the same unit (lesson: Configuring the Header Area of the Object Page).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2C80F34AEDD19CB6:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Right-click _webapp_ from your _travels_ project.
  3. Choose the _Show Page Map_ option from the subsequent menu.
  4. Select the edit icon for the _Travel_BookingObjectPage_ within the _Page Editor_.
  5. Select the _Sections_ row.
  6. Select the add icon for the _Sections_ row.
  7. Choose _Add Identification Section_ from the list.
  8. Enter **Plane Details** in the _Label_ field of the _Add Identification Section_ dialog box. _Plane Details_ are added within the _Sections_ row of the _Page Editor_.
  9. Expand the _Plane Details_ row.
  10. Expand _Form_ within _Plane Details_.
  11. Select _Fields_.
  12. Select the add icon for _Fields_.
  13. Choose _Add Basic Fields_ option from the list.
  14. Select the dropdown icon for the _Fields_ field within the _Add Basic Fields_ dialog box.
  15. Choose __Flight/PlaneType_ , __Flight/MaximumSeats_ , and __Flight/OccupiedSeats_ from the list.
  16. Select _Add_ from the _Add Basic Fields_ dialog box. You can see that all the three fields have been added within _Fields_.
  17. Select the _Edit in source code_ icon for _Maximum Capacity_ to open the file where the annotation has been added to.
  18. You can see the UI.Identification records that have been added by the page editor for all the three fields.
  19. Select the _Plane Details_ row from within the _Sections_.
  20. Select the global icon from the _Label_ field of the right-hand side pane.
  21. Select _Apply_ from the subsequent popup.
  22. Select the _Edit in source code_ icon for the _Plane Details_ row.
  23. You can see the UI.Facets record that has been added by the _Page Editor_. It creates a new section. It references the UI.Identification annotation that defines the content of the section.
  24. Scroll down to see the UI.Identification annotation definition for all the three fields.
  25. Switch to the app preview in your browser. You can see the section in the subobject page body containing plane details.
  26. Select the right chevron to expand the object page.
  27. Select the full screen option for the subobject page to expand it. You have observed the responsive behavior of your app, particularly the full screen mode of the subobject page.

### Result
You successfully added a section to the subobject page body using the page editor. You can also add a new section using the guided development guide Add a new section to an object page.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit9ConfiguringObjectPages/lesson2ConfiguringSectionsOfTheObjectPageBody/exercise1AddPlaneDetailsSectionToTheSubobjectPageBody.md).
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-object-pages)
