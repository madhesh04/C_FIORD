# Creating an Object Page

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/creating-an-object-page*

Objective
After completing this lesson, you will be able to configure the header area of the object page, add sections to the object page body.
## Add a Title and a Description to the Header Area of the Object Page
In this exercise, you will add a title and a description to the object page. You will also add a title to the list report table.
### Prerequisites
You have completed the exercise Add Description Text Instead of Codes for the Overall Status in the same unit (lesson: Creating a List Report).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_EBEBCE0DD5F73B93:uebung)
### Steps
  1. You have the list report from your previous exercise open in your browser.
  2. Select a travel from the list. The object page opens but only a technical ID of the travel is displayed, as the object page is still empty.
  3. Open ADT and expand the _Metadata Extensions_ folder within _Project Explorer_.
  4. Add a title to the list report table, and a title and description to the object page.
    1. Double-click the metadata extension _ZC_FE_TRAVEL_######_. The metadata extension of the _Travel_ entity opens.
    2. Add the @UI.headerInfo annotation right on top of the file, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

123456

@UI.headerInfo: {
    typeNamePlural: 'Travels',
    typeName: 'Travel',
    title: { type: #STANDARD, value: 'Description'},
    description: { type: #STANDARD, value: 'TravelID'}
}

```

    3. The typeNamePlural property defines the title of the list report. The value of this annotation is a string.
    4. The typeName property for the object page title is displayed in the top center position of the object page. The value of this annotation is a string.
    5. The title property defines what is displayed in the left upper corner of the object page. The value of this property is the _Description_ field of the _Travel_ entity.
    6. The description property of the @UI.headerInfo annotation defines what is displayed underneath the title in the left upper corner of the object page.
  5. Click _Activate_ from the menu bar to save and activate your changes.
  6. Switch to the app preview in your browser. You can see that the title of the list report table has been added.
  7. Select _Go_ from the table. The list report table is displayed.
  8. Select the travel as before. The object page now opens with a title that includes the travel description and travel ID.

### Result
You successfully added the title of the list report table. You have displayed the travel ID and travel description for the object page header. Note that you cannot see Travel as the object page title due to certain restrictions of the ADT app preview. You will be able to see that in a real app once you have generated it in SAP Business Application Studio in one of the following exercises.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson2CreatingAnObjectPage/exercise1AddTitleAndDescriptionToTheHeaderAreaOfTheObjectPage.md).
## Enhance the Header with Price and Status Information of a Specific Travel
In this exercise, you are going to add _Total Price_ and _Overall Status_ to the header of the object page.
### Prerequisites
You have completed the exercise Add a Title and a Description to the Header Area of the Object Page in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_4817970A9173D8B1:uebung)
### Steps
  1. You have the list report from your previous exercise open in your browser.
  2. Select a travel. The object page for the travel opens. You are going to add the _Total Price_ and _Overall Status_ as data points to the object page header.
  3. You can now switch to ADT.
  4. Annotate TotalPrice with @UI.dataPoint.
    1. Double-click _ZC_FE_TRAVEL_######_ from the _Metadata Extension_ folder of _Project Explorer_.
    2. Add the @UI.dataPoint annotation for TotalPrice, as shown in the following sample code:
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.dataPoint: { qualifier: 'PriceData', title: 'Total Price' }

```

  5. Add the @UI.facet annotation and reference the @UI.dataPoint annotation of TotalPrice in it.
    1. In the same metadata extension, add the @UI.facet annotation, as shown in the following sample code, to define a section on the object page. Note that @UI.facet annotation comes directly after annotate view ZC_FE_Travel_###### with {
Code Snippet
Copy codeSwitch to dark mode

```

1234567

@UI.facet: [{
     purpose: #HEADER,
     position: 10,
     type: #DATAPOINT_REFERENCE,
     targetQualifier: 'PriceData'
}]

```

    2. The purpose for this annotation is added as #HEADER so that the section is placed into the object page header.
    3. The position is set as 10 so that it is the first section in the object page header.
    4. The type is defined as #DATAPOINT_REFERENCE, which means it references a @UI.dataPoint annotation.
    5. The targetQualifier identifies the referenced @UI.dataPoint annotation.
  6. Click _Activate_ from the menu bar to save and activate your changes.
  7. Switch to the app preview in your browser to see the changes on the UI. You can see that _Total Price_ is now visible in the object page header.
  8. Switch to ADT.
  9. Add the @UI.dataPoint annotation to OverallStatus in the opened metadata extension, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.dataPoint: { qualifier: 'StatusData', title: 'Status', criticality: 'OverallStatusCriticality' }

```

  10. Add the @UI.facet annotation and reference the @UI.dataPoint annotation of OverallStatus in it.
    1. Add another record of @UI.facet annotation to display the second section in the object page header, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1234567

,
{
     purpose: #HEADER,
     position: 20,
     type: #DATAPOINT_REFERENCE,
     targetQualifier: 'StatusData'
}

```

    2. Ensure that #HEADER is entered as the purpose.
    3. Set the position as 20 so that it is on the second position in the object page header.
    4. Define the type as #DATAPOINT_REFERENCE, which means it references a @UI.dataPoint annotation.
    5. The targetQualifier identifies the referenced @UI.dataPoint annotation.
  11. Click _Activate_ from the menu bar to save and activate your changes.
  12. Switch to the app preview in your browser to see the changes on the UI. You can see that the _Status_ is now visible in the object page header next to _Total Price_.

### Result
You successfully added two fields, _Total Price_ and _Overall Status_ , as data points to the object page header.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson2CreatingAnObjectPage/exercise2EnhanceTheHeaderWithPriceAndStatusInformationOfASpecificTravel.md).
## Add an Identification Section to the Object Page Body
In this exercise, you will add a section and the identification subsection to the object page body.
### Prerequisites
You have completed the exercise Enhance the Header with Price and Status Information of a Specific Travel in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_60FA8E447D033BBA:uebung)
### Steps
  1. You have the list report from your previous exercise open in your browser.
  2. Select a travel. The object page for travel opens. You have to add the first section to the object page body and add an identification subsection to it.
  3. You can now switch to ADT and open the _ZC_FE_TRAVEL_######__Metadata Extension_ from the _Project Explorer_.
  4. Annotate AgencyID with @UI.identification, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.identification: [{position: 10}]

```

  5. Annotate CustomerID with @UI.identification, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.identification: [{position: 20}]

```

  6. Add a new record to @UI.facet annotation, as shown in the following sample code, to create a section in the object page body. This is an empty container, and you can add subsections here.
Code Snippet
Copy codeSwitch to dark mode

```

1234567

,
{
    label: 'General Information',
    type: #COLLECTION,
    id: 'GeneralInfo',
    position: 10
}

```

  7. Add another record to @UI.facet annotation, as shown in the following sample code, for the identification subsection.
Code Snippet
Copy codeSwitch to dark mode

```

123456

,
{
     label: 'General',
     type: #IDENTIFICATION_REFERENCE,
     parentId: 'GeneralInfo'  /*The section id*/
}

```

  8. Reference the section created earlier as the parent section of this subsection by maintaining parentId as GeneralInfo. The new section now becomes the subsection of the _General Information_ section.
  9. Click _Activate_ from the menu bar to save and activate your changes.
  10. Switch to the app preview in your browser to see your changes on the UI. You can see that _General Information_ is a new section, and the identification subsection is visible as _General_ within the new section.

### Result
You successfully created a section and an identification subsection within the object page body.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson2CreatingAnObjectPage/exercise3AddAnIdentificationSectionToTheObjectPageBody.md).
## Add Two Subsections to a Section in the Object Page Body
In this exercise, you will add two subsections to the _General Information_ section of the object page.
### Prerequisites
You have completed the exercise Add an Identification Section to the Object Page Body in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_A19ADFB108267B87:uebung)
### Steps
  1. You have the list report from your previous exercise open in your browser.
  2. Select a travel from the list. The object page for the travel opens. You have to add a subsection with prices, and a subsection with date information. You have to place both of these subsections within the _General Information_ section next to the _General_ subsection.
  3. You can now switch to ADT and open the _ZC_FE_TRAVEL_######__Metadata Extension_ from the _Project Explorer_.
  4. Annotate TotalPrice with @UI.fieldGroup, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.fieldGroup: [{qualifier: 'PricesGroup', position: 10}]

```

  5. Annotate BookingFee with @UI.fieldGroup, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.fieldGroup: [{qualifier: 'PricesGroup', position: 20}]

```

  6. Add another record to @UI.facet annotation of type #FIELDGROUP_REFERENCE for the _Prices_ subsection, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

123456789

,
{
    label: 'Prices',
    purpose: #STANDARD,
    position: 20,
    type: #FIELDGROUP_REFERENCE,
    parentId: 'GeneralInfo',
    targetQualifier: 'PricesGroup'
}

```

    1. The label is Prices.
    2. The parentId for this subsection is GeneralInfo, so the subsection appears within the _General Information_ section.
    3. The targetQualifier is PricesGroup.
  7. Annotate BeginDate with @UI.fieldGroup, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.fieldGroup: [{qualifier: 'DatesGroup', position: 10}]

```

  8. Annotate EndDate with @UI.fieldGroup, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

1

@UI.fieldGroup: [{qualifier: 'DatesGroup', position: 20}]

```

  9. Add another record to @UI.facet annotation of type #FIELDGROUP_REFERENCE for the Dates subsection, as shown in the following sample code.
Code Snippet
Copy codeSwitch to dark mode

```

123456789

,
{
    label: 'Dates',
    purpose: #STANDARD,
    position: 30,
    type: #FIELDGROUP_REFERENCE,
    parentId: 'GeneralInfo',
    targetQualifier: 'DatesGroup'
}

```

    1. The label is Dates.
    2. The parentId for this subsection is GeneralInfo, so the subsection appears within the _General Information_ section.
    3. The qualifier for the field group is DatesGroup.
  10. Click _Activate_ from the menu bar to save and activate your changes.
  11. Switch to the app preview in your browser to see your changes on the UI. You can see _Prices_ and _Dates_ as subsections that have been added to the _General Information_ section.

### Result
You successfully added two subsections, _Prices_ and _Dates_ , to the existing _General Information_ section of the object page.
Note
You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-rap-learning-journey/blob/main/Fiori%20Elements%20App%20Based%20on%20an%20V4%20RAP%20Service/unit3ConfiguringAbapCdsAnnotationsInTheBackEnd/lesson2CreatingAnObjectPage/exercise4AddTwoSubsectionsToASectionInTheObjectPageBody.md).
## Mapping of ABAP CDS Annotations to XML Format
So far, you have added ABAP CDS annotations to the corresponding metadata extension of your projection view in ADT. Once you publish the service in ADT, an OData service is generated by the runtime. From this point on, the service URL is available and can be used, for example, to generate an SAP Fiori elements app. All the meta descriptions of the data model of your service (including the exposed entities, properties, and associations) is available in the machine-readable $metadata document of the service. All the ABAP CDS annotations are converted automatically by the runtime to XML format and also added to the same $metadata document. In order to view the $metadata document in the browser, you can take the root URL of an OData service and append $metadata at the end. Note that for OData V2 services, annotations are added into a separate annotation file.
After the service has been published, you can still add UI annotations to the metadata extensions. They are added to the $metadata document automatically once you activate your changes in ADT.
## Check Active Annotations for a CDS View and the Corresponding OData Annotations in the Service
In this exercise, you will see how you can look up the active ABAP CDS annotations for a projection view. You will see the service URL and observe how the data model of your service is represented in the $metadata document. You will then go on to check the corresponding OData annotations that have been transformed by the runtime from the corresponding ABAP CDS annotations.
### Prerequisites
You have completed the exercise Add Two Subsections to a Section on the Object Page in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_781693AED8EDFC82:uebung)
### Steps
  1. Open the _Data Definitions_ folder within the _Core Data Services_ folder from _Project Explorer_ in ADT.
  2. Right-click _ZC_FE_TRAVEL_######_.
  3. Choose _Open With_ from the subsequent menu.
  4. Choose the _Active Annotations_ option.
  5. All the active annotations for the selected projection view are displayed. You can see @UI.annotations along with other annotations, such as @AccessControl and @ObjectModel.
  6. You can see the definition of the @UI.headerinfo annotation that is defined on the entity level.
  7. Scroll down to see other UI relevant annotations, such as @UI.facet annotation.
  8. From the _Business Services_ folder of _Project Explorer_ , double-click _ZUI_FE_TRAVEL_######_O4_.
  9. From the _Service Binding_ document, select the _Service URL_ available within _Service Version Details_. The service URL opens in your browser.
  10. You can see all the entities of your service. Each entity represents the corresponding projection view. The I_DraftAdministrativeData is automatically added to your service by runtime, as the service is draft enabled.
  11. Remove _?sap-client=100_ from the URL and replace it with _$metadata_. The service metadata is displayed.
  12. Scroll down to the definition of the _Travel_ entity. It represents the corresponding projection view. Each property is a field of the _ZC_FE_TRAVEL_######_ projection view. You can also see the navigation properties such as _BookingFee, _CustomerID. You can also see certain technical properties, such as HasDraftEntity, which are added automatically by the runtime, as the service is draft enabled.
  13. Scroll down to the definition of the @UI.LineItem annotation. You can see a collection of records where each record represents a table column.

### Result
You successfully displayed the active ABAP CDS annotations in ADT. You also observed the mapping of the data model and annotations to the OData entities and annotation in the $metadata document of your service.
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/configuring-abap-cds-annotations-in-the-back-end)
