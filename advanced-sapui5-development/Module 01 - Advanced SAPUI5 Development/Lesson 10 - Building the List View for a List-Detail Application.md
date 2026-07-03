# Building the List View for a List-Detail Application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/building-the-list-view-for-a-list-detail-application*

Objective
After completing this lesson, you will be able to build the List view for a List-Detail application.
## The DynamicPage control
After the implementation of the application foundation, we can go further with the implementation of the views. We start with the list view, the view that should be shown after the initial start of the application. We will use the _sap.f.DynamicPage_ to implement the basic layout.
Watch this video to know more about the structure of the _sap.f.DynamicPage_ control used in the List View.
### Reasons to use DynamicPage controls
  * You need to have a title, that is always visible and a header, that has configurable Expanding/Snapping functionality. If you don't need the Expanding/Snapping functionality it is better to use the sap.m.Page as a lighter control.
  * You're displaying a sap.m.FlexBox with non-adaptive content (doesn't stretch to fill the available space), it is recommended to set the fitContainer property of the FlexBox to false. If you are displaying a sap.ui.table.Table, keep in mind that it is non-adaptive and may cause unpredicted behavior for the DynamicPage on smaller screen sizes, such as mobile.
  * The snapping of the DynamicPageTitle is not supported in the following case: When the DynamicPage has a scroll bar, the control usually scrolls to the snapping point - the point, where the DynamicPageHeader is scrolled out completely. However, when there is a scroll bar, but not enough content to reach the snapping point, the snapping is not possible using scrolling.
  * You are using sap.ui.layout.form.Form, sap.m.Panel, sap.m.Table and sap.m.List controls in the content of DynamicPage, you need to adjust their left text offset if you want to achieve vertical alignment between the sap.f.DynamicPageHeader`s content and DynamicPage`s content. For more information, see the documentation for the content aggregation.

### The DynamicPage Responsive Behavior
The responsive behavior of the DynamicPage depends on the behavior of the content that is displayed. To adjust the DynamicPage content padding, the sapUiContentPadding, sapUiNoContentPadding, and sapUiResponsiveContentPadding CSS classes can be used.
This Image shows the implementation of the Overview view using the sap.f.DynamicPage:
![The List view definition with a DynamicPage control and a Table.](../images/1f5e469253562aef.png)
## Build the List view for the List-Detail application
### Business Example
In this exercise, you define the list view content for your application. The view will implement a sap.f.DynamicPage object. The page will show a list of Carriers fetched from the entity set UX_C_Carrier_TP.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You need to have completed the previous exercise to adapt the router configuration.
### Steps
  1. Open the Carrier.view.xml file, remove the page element and add the namespace sap.f with the XML-alias f.
    1. Update the code as follows:
Code Snippet
Copy codeSwitch to dark mode

```

123456

<mvc:View controllerName="student.com.sap.training.advancedsapui5.listdetail.controller.Carrier"
    xmlns:mvc="sap.ui.core.mvc"
    displayBlock="true"
    xmlns="sap.m"
    xmlns:f="sap.f">

```

  2. Add an sap.f.DynamicPage element with sap.f.content aggregation to the view with the following properties.
| Property  | Value  |
| --- | --- |
| id  | **dynamicPageOverviewId**  |
| headerExpanded  | **true**  |
| toggleHeaderOnTitleClick  | **true**  |
    1. Add the following code inside the View definition:
Code Snippet
Copy codeSwitch to dark mode

```

123456

<f:DynamicPage id="dynamicPageOverviewId" headerExpanded="true" toggleHeaderOnTitleClick="true">
  <f:content>

  </f:content>
</f:DynamicPage>

```

  3. Create an sap.m.List control inside the sap.f.content aggregation and assign the following values to the List element:
#### Attribute-value Pairs for the sap.m.List Control
| Attribute  | Value  |
| --- | --- |
| id  | **list**  |
| items  | **{/UX_C_Carrier_TP}**  |
| busyIndicatorDelay  | **0**  |
| growing  | **true**  |
| growingThreshold  | **20**  |
| growingScrollToLoad  | **true**  |
| mode  | **SingleSelectMaster**  |
| selectionChange  |  **onSelect**  |
    1. Add the following code inside the content aggregation:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910

<List id="list"
      items="{/UX_C_Carrier_TP}"
      busyIndicatorDelay="0"
      growing="true"
      growingThreshold="10"
      growingScrollToLoad="true"
      mode="SingleSelectMaster"
      selectionChange="onSelect">

</List>

```

  4. Add the items aggregation to the sap.m.List control and add a control type of sap.m.ObjectListItem to the items aggregation with the following attributes:
#### Attribute-value Pairs for the sap.m.ObjectListItem Element
| Attribute  | Value  |
| --- | --- |
| id  | **objectListItem**  |
| title  | **{Carrname}**  |
| intro  | **{Carrid}**  |
| type  | **Inactive**  |
    1. Extend your code with the following implementation inside the List element:
Code Snippet
Copy codeSwitch to dark mode

```

12345678

<items>
  <ObjectListItem
    id="objectListItem"
    title="{Carrname}"
    intro="{Carrid}"
    type="Inactive">
  </ObjectListItem>
</items>

```

    2. Your implementation should now look like the following:
![Screenshot of the resulting view code.](../images/c9bbf4d0a7ed1e34.png)
  5. Preview the application. A list of carriers should display.
    1. Preview the application as shown before. A list of carriers should display.
