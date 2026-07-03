# Building the Detail View for a List-Detail Application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/implementing-views-and-controller_ce148675-21ba-44c7-98e2-50b5ff8f47da*

Objective
After completing this lesson, you will be able to build the Detail view for a List-Detail application.
## Implement Views for List-Detail Application
After the implementation of the Overview-page, we want to implement the details. The details page should display the details of the selected carrier from the list page, and additionally, the flights and connections of the carrier. The page should look like what is shown in the following figure and can be achieved by using the _sap.uxap.ObjectPageLayout_.
Watch this video to know more about the structure of _sap.uxap.ObjectPageLayout_ control used in the Detail View.
### Use Cases
Use the **ObjectPageLayout** if:
  * The users need to see, edit, or create an item with all its details.
  * Users need to get an overview of an object and interact with different parts of the object.

### Implementation Example
![The detail view with an ObjectPageLayout control.](../images/f5be09a39935e804.png)
The figure shows parts of the Carrier-view implementation. You can see the implementation of the aggregations _headerTitle_ and _sections_.
## Build the Detail view for the List-Detail application
### Business Example
In this exercise, you define the detail view content for your application. The view should show the details of the selected carrier using the sap.uxap.ObjectPageDynamicHeaderTitle element and sap.uxap.headerContent aggregation. The table that will be implemented shows the available flights for the selected carrier.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You need to have completed the previous exercise to build the List View.
### Steps
  1. Open the Flights.view.xml file and add the namespaces sap.uxap with the XML alias ux.
    1. Update the code as follows:
Code Snippet
Copy codeSwitch to dark mode

```

123456789

<mvc:View controllerName="student.com.sap.training.advancedsapui5.listdetail.controller.Flights"
    xmlns:mvc="sap.ui.core.mvc" displayBlock="true"
    xmlns="sap.m"
    xmlns:l="sap.ui.layout"
    xmlns:ux="sap.uxap">

</mvc:View>

```

  2. Add an sap.uxap.ObjectPageLayout element to the view. Add the attribute id with the value objectPageLayout.
    1. Add the following code at the beginning of the View definition:
Code Snippet
Copy codeSwitch to dark mode

```

123

<ux:ObjectPageLayout id="objectPageLayout">

</ux:ObjectPageLayout>

```

  3. Add an sap.uxap.headerTitle, sap.uxap.headerContent and sap.uxap.sections aggregation to the sap.uxap.ObjectPageLayout control.
    1. Add the following code inside the ObjectPageLayout element:
Code Snippet
Copy codeSwitch to dark mode

```

123456789

<ux:headerTitle>

</ux:headerTitle>
<ux:headerContent>

</ux:headerContent>
<ux:sections>

</ux:sections>

```

  4. Add an sap.uxap.ObjectPageDynamicHeaderTitle control to the headerTitle aggregation. For the attribute id, add the value objectPageDynamicHeader.
    1. Add the following code inside the headerTitle element:
Code Snippet
Copy codeSwitch to dark mode

```

123

<ux:ObjectPageDynamicHeaderTitle id="objectPageDynamicHeader">

</ux:ObjectPageDynamicHeaderTitle>

```

  5. Add an sap.uxap.expandedHeading aggregation to the sap.uxap.ObjectPageDynamicHeaderTitle control.
    1. Add the following code inside the ObjectPageDynamicHeaderTitle element:
Code Snippet
Copy codeSwitch to dark mode

```

123

<ux:expandedHeading>

</ux:expandedHeading>

```

  6. Add an sap.m.Title control to the sap.uxap.expandedHeading aggregation with the listed attributes and values.
#### Attribute-value Pairs for the sap.m.ObjectAttribute Elements
| Attribute  | Value  |
| --- | --- |
| id  | **title1**  |
| text  | **{Carrname}**  |
| level  | **H2**  |
    1. Add the following code inside the expandedHeading element:
Code Snippet
Copy codeSwitch to dark mode

```

1234

<Title
id="fltitle"
text="{Carrname}"
level="H2"/>

```

    2. The headerTitlesection should now look like the following:
![Screenshot of the resulting headerTitle section.](../images/2bcc50ea28aedb80.png)
  7. Add an sap.m.FlexBox control to the sap.uxap.headerContent with the listed attributes and values.
| Attribute  | Value  |
| --- | --- |
| id  | **flexbox**  |
| wrap  | **Wrap**  |
    1. Add the following code inside the headerContent element:
Code Snippet
Copy codeSwitch to dark mode

```

123

<FlexBox wrap="Wrap" id="flexBox">

</FlexBox>

```

  8. Add an sap.f.Avatar and a sap.ui.layout.VerticalLayout control to the sap.m.Flex control with the listed attributes and values.
| Element  | Attribute  | Value  |
| --- | --- | --- |
| 1  | id  | **avatar**  |
| src  | **sap-icon://flight**  |
| 2  | id  | **verticallayout1**  |
| class  | **sapUiSmallMarginBeginEnd**  |
    1. Add the following code inside the FlexBox element:
Code Snippet
Copy codeSwitch to dark mode

```

1234

<Avatar id="avatar" src="sap-icon://flight"/>
<l:VerticalLayout id="verticalLayout1" class="sapUiSmallMarginBeginEnd">

</l:VerticalLayout>

```

  9. Add two sap.m.Label controls to the sap.ui.layout.VerticalLayout control with the listed attributes and values:
| Element  | Attribute  | Value  |
| --- | --- | --- |
| 1  | id  | **label1**  |
| text  | **{Carrid}**  |
| 2  | id  | **label2**  |
| text  | **{Url}**  |
    1. Add the following code into the VerticalLayout element:
Code Snippet
Copy codeSwitch to dark mode

```

12

<Label id="label1" text="{Carrid}"/>
<Label id="label2" text="{Url}"/>

```

    2. Your code for the headerContent should now look like the following:
![Screenshot of the resulting headerContent section.](../images/a70af9e0a6ffa157.png)
  10. Add an sap.uxap.ObjectPageSection control to thesap.uxap.sections aggregation. Add the value objectPageSection to the attribute id.
    1. Add the following code inside the sections element:
Code Snippet
Copy codeSwitch to dark mode

```

123

<ux:ObjectPageSection id="objectPageSection">

</ux:ObjectPageSection>

```

  11. Add an sap.uxap.ObjectPageSubSection control to the sap.uxap.ObjectPageSection control. Add the value objectPageSubSection to the attribute id.
    1. Add the following code inside the ObjectPageSection element:
Code Snippet
Copy codeSwitch to dark mode

```

123

<ux:ObjectPageSubSection id="objectPageSubSection1">

</ux:ObjectPageSubSection>

```

  12. Cut and paste the sap.m.Table control into the sap.uxap.ObjectPageSubSection aggregation.
    1. Cut / Paste the table element and its content inside the ObjectPageSubSection element:
Code Snippet
Copy codeSwitch to dark mode

```

123456

<Table id="idFlights" items="{path: 'to_Flight', sorter: {path: 'Carrid'}}"
                            mode="SingleSelectMaster"
                            growing="true"
                            growingThreshold="10">
[...]
</Table>

```

  13. Remove the remaining _Page_ element and its content.
    1. Remove the rest of the Page element code:
Code Snippet
Copy codeSwitch to dark mode

```

123

<Page id="idFlightsPage".....
...
</Page>

```

### Result
You won't be able to test the detail view yet. You need to do next exercise on view synchronization first.
