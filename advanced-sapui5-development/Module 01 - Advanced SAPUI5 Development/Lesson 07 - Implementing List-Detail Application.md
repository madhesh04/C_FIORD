# Implementing List-Detail Application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/designing-a-list-detail-application_a8654105-93dc-4fca-aa5c-d9e9d5d4f8c3*

Objective
After completing this lesson, you will be able to design a list-detail application using sap.f.FlexibleColumnLayout.
## Understanding the basic application design of a list-detail application
In SAPUI5 you can also implement the list-detail pattern. Apps following this pattern operate with a layout divided into two or three areas: a list area and two detail areas. The list area displays the items available to the user. The first detail area displays the details of an item selected in the list area. Sometimes this area contains, besides other data, a list of items. The user can select an item from this list to get more information in the second detail area.
In this unit, we will focus only on the design and implementation aspects that are different to the previous unit, Implementing Full-screen Application.
### The sap.f.FlexibleColumnLayout Control
For some use cases, it is very important to have a fluid navigation between pages, above the usual page-by-page navigation. Consequently, SAPUI5 provides the _sap.f.FlexibleColumnLayout_ control. The flexible column layout offers different layouts with up to three columns. Users can expand the column they want to focus on, switch between different layouts, and view the rightmost column in full screen mode.
In this video, take a look at the usage of _sap.f.FlexibleColumnLayout_ with the three columns.
### MVC Approach
The application design of an application using the _sap.f.FlexibleColumnLayout_ controls will also start with a view that is usually named App. Unlike the full-screen application, however, the App-view implementation does not only contain a control of the type _sap.m.App_. The _sap.f.FlexbileColumnLayout_ will be added to the _sap.m.App_.
![The structure of an App.view.xml, with a FlexiblecolumnLayout and three pages corresponding to begin, mid and end Column Pages.](../images/95820d9e22ad5dbe.png)
The _beginColumnPages_ , _midColumnPages_ and _endColumnPages_ aggregations of the Layout control aggregates the content entities.
The content entities can be of type _sap.f.DynamicPage_ , _sap.ui.core.View_ , _sap.m.Carousel_ , or any other control with fullscreen/page semantics.
### Using the List-Detail Pattern

When to use the list-detail pattern:
    You need to review and process different items quickly with minimal navigation.

When not to use the list-detail pattern:

  * You need to offer complex filters for the list of items.
  * You need to see different attributes for each item in the list, and compare these values across items.
  * You want to display a single object. Do not use the list to display different facets of the same object.
