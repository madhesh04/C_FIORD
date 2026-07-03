# Configuring External Navigation

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-external-navigation_dd4d7f6f-7857-4604-b993-70012c702c3f*

Objective
After completing this lesson, you will be able to configure the navigation to another application.
## Configuration of External Navigation
To configure navigation between two apps, you need to set up navigation targets and configure the navigation in the source app (outbound navigation).
There are several options how you can configure the navigation from a source app.
  1. As a button in the table tool bar. To do this, add an @UI.DataFieldForIntentBasedNavigation annotation containing a combination of a semantic object and action.
  2. You can replace the standard internal navigation to the object or subobject page in manifest.json. For more information, see [Changing Navigation to Object Page](https://ui5.sap.com/#/topic/8bd546e27a5f41cea6e251ba04534d70).
  3. You can configure links both in forms and tables (in the list report and on the object page). To do this, you can use the @Common.SemanticObject annotation.
For more information, see [Navigation from an App (Outbound Navigation)](https://ui5.sap.com/#/topic/d782acf8bfd74107ad6a04f0361c5f62.html).
  4. In SAP Fiori elements for OData V4 apps, you can configure external navigation from the header facet title of an object page. For more information, see [Navigation from Header Facet Title](https://sapui5.hana.ondemand.com/sdk/#/topic/fa0ca22de375490a84aa3375b617592f).

## Transition of the Navigation Context to the Target App
The navigation context of the source app is passed to the target app.
For example, if a user has selected some values in the filter bar and then navigates to the target app, the values in the filter bar will be passed to the target app and they will be displayed in its filter bar (if it exists in the target app). If the navigation context matches several items of the target app, the list report is displayed. If the unique object of the target app can be identified (that is, all the values of key fields are provided in the navigation context), the object or subobject page of the target app is displayed.
SAP Fiori launchpad can also pass other values to the target app, such as FLP target mapping default values. For more information, see [Navigation to an App (Inbound Navigation)](https://ui5.sap.com/#/topic/c337d8bde8c544598969c8e4edaab262).
## Navigate to the Display Customers App from the Manage Travels App by Pressing the Toolbar Button
You want to provide the ability to navigate from your _Manage Travels_ app to the detailed customer page, which is another app called _Display Customers_.
### Task Flow
You will first open the apps in the local sandbox environment. Then, you will add the button and check the results.
### Prerequisites
You have completed the exercise Add a Custom Micro Chart to the Object Page Header of the Display Customers App in the unit Discovering the Flexibility of the Programming Model for SAP Fiori Elements for OData V4 (lesson: Adding a Custom Micro Chart). Alternatively, you can check out its solution branch: [solution/add-custom-micro-chart-to-object-page-header](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-custom-micro-chart-to-object-page-header).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_BF451ABD036597B5:uebung)
### Steps
  1. Open the sandbox environment.
    1. Execute cds watch and navigate to the _Welcome_ page of the @sap/cds server. In the production environment, the app should run within the SAP Fiori launchpad. In this exercise, we will use the sandbox environment to simulate it.
    2. Add /sandbox/index.html to the URL of the current page to open the sandbox environment.
    3. You can see the simulated SAP Fiori launchpad with two tiles representing the apps.
    4. Select the _Travels_ tile. You have opened the _Manage Travels_ app in the sandbox environment.
  2. Add a navigation button to the _Manage Travels_ app.
    1. Open layouts.cds in SAP Business Application Studio and add the following record to the @UI.LineItem annotation for the Travel entity:
Code Snippet
Copy codeSwitch to dark mode

```

1

 { $Type : 'UI.DataFieldForIntentBasedNavigation', SemanticObject : 'Customer', Action : 'display', Label : '{i18n>DisplayCustomers}', RequiresContext : false, Mapping : [ { $Type : 'Common.SemanticObjectMappingType', LocalProperty : to_Customer_CustomerID, SemanticObjectProperty : 'CustomerID', } ] }

```

You have added an annotation of type UI.DataFieldForIntentBasedNavigation. You have declared the semantic object 'Customer' and the action 'display'. The combination of the semantic object and action is the intent which will be the target of this navigation.
    2. Open the manifest.json file of the _Display Customers_ app. You can see that the semantic object 'Customer' and the action 'display' are defined for the inbound navigation of the _Display Customers_ app.
    3. Open the i18n.properties file and add the new UI text for the DisplayCustomers button.
Code Snippet
Copy codeSwitch to dark mode

```

1

DisplayCustomers=Display Customers

```

    4. Note that the UI.DataFieldForIntentBasedNavigation record contains a mapping property. It is used to map the key property CustomerID of the target entity (Passenger) to the foreign key property to_Customer_CustomerID of the source entity (Travel).
  3. Check the results.
    1. Open the _Manage Travels_ app. You can see the _Display Customers_ button has been added to the tool bar on top of the _Travels_ table.
    2. Select the _Display Customers_ button. You have navigated to the list report of the _Display Customers_ app.
    3. Check the customer list and navigate back.
    4. Now select a travel and then select _Display Customers_. You have navigated directly to the object page for the selected customer.

### Result
In this lesson you have learned how to configure external navigation via a list report tool bar button.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-toolbar-button-to-navigate-to-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-toolbar-button-to-navigate-to-customer-app).
  * You can find the link to the direct comparison of the branch to the previous one on [Github](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-custom-micro-chart-to-object-page-header..solution/add-toolbar-button-to-navigate-to-customer-app).

Note
  * You can also skip the Mapping property of the @UI.DataFieldForIntentBasedNavigation annotation.
  * You can find the solution branch without the Mapping property on: [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-toolbar-button-without-semantic-mapping).
  * You can find the link with the comparison of the solution branch without the Mapping property and the solution branch containing the Mapping property on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-toolbar-button-to-navigate-to-customer-app..solution/add-toolbar-button-without-semantic-mapping?diff=split).

### Next Steps
For more information, see:
  * [Configuring External Navigation](https://ui5.sap.com/#/topic/1d4a0f94bfee48d1b50ca8084a76beec)
  * [Navigation from an App (Outbound Navigation)](https://ui5.sap.com/#/topic/d782acf8bfd74107ad6a04f0361c5f62)

## Associations in CAP
In this section you will learn the difference between managed and unmanaged associations in CAP CDS. This information will help you better understand the annotation syntax in the exercise which follows.
In the database model, associations need to be mapped to foreign-key relationships. CAP CDS supports both unmanaged and managed associations.
Unmanaged associations have to use the existing properties of the source and target entity. In this case, CAP does not generate any properties, and it's not possible to use other associations. The ON clause may contain any kind of join conditions referring to available foreign key properties. The following example demonstrates how you can associate the entity Customer with the key property CustomerID to the entity Booking with the foreign key property to_Customer_CustomerID:
Code Snippet
Copy codeSwitch to dark mode

```

1234

entity Booking { ...
  to_Customer_CustomerID : String(6);
  to_Customer        : Association to Passenger on to_Customer.CustomerID = to_Customer_CustomerID;
}

```

For managed associations, a foreign key constraint is automatically generated. That constraint ties the foreign key properties of the source entity (automatically added for a managed association) to the respective primary key properties of the target entity (already given):
Code Snippet
Copy codeSwitch to dark mode

```

123

entity Booking { ...
  to_Customer: Association to Passenger;
}

```

When you compare managed association to unmanaged, you can find two convenient shortcuts:
  1. The Booking entity no longer has the foreign key property that was named to_Customer_CustomerID
  2. The association to_Customer no longer has an ON clause

When CAP generates the OData metadata document at runtime, you'll see that the API still contains both a referential constraint representing the ON clause and the foreign key property to_Customer_CustomerID:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011

<EntityType Name="Booking">
    <Key>
        <PropertyRef Name="BookingUUID"/>
        <PropertyRef Name="IsActiveEntity"/>
    </Key>
    ...
    <NavigationProperty Name="to_Customer" Type="TravelService.Passenger">
        <ReferentialConstraint Property="to_Customer_CustomerID" ReferencedProperty="CustomerID"/>
    </NavigationProperty>
    <Property Name="to_Customer_CustomerID" Type="Edm.String" MaxLength="6"/>
</EntityType>

```

Keep in mind the difference between the managed and unmanaged associations and what is generated at runtime. In particular, you'll find that a few annotations which you would expect at foreign key property level, need to be maintained at association level. For managed associations foreign key properties are only available at runtime. The example below shows annotating the to_Customer_CustomerID field of the entity Booking with the text LastName of the associated customer when using a managed association:
Code Snippet
Copy codeSwitch to dark mode

```

123

annotate Booking with { ...
  to_Customer @Common.Text: to_Customer.LastName;
}

```

When using an unmanaged association, the foreign key property is already available at the source entity at the design time:
Code Snippet
Copy codeSwitch to dark mode

```

123

annotate Booking with { ...
  to_Customer_CustomerID @Common.Text: to_Customer.LastName;
}

```

### Next Steps
For more information, see:
  * [The Nature of Models](https://cap.cloud.sap/docs/cds/models)
  * [CDS Associations](https://help.sap.com/docs/SAP_HANA_PLATFORM/09b6623836854766b682356393c6c416/6fcd6e5883f04de5b618a6d91141afb4.html?version=2.0.02)
  * [CDS Association Syntax Options](https://help.sap.com/docs/SAP_HANA_PLATFORM/4505d0bdaf4948449b7f7379d24d0f0d/809a42308d814b7ea1c8369e55591515.html)
  * [SAP Cloud Platform Backend service: Tutorial [3]: CDS : how to define associations (1)](https://blogs.sap.com/2019/02/20/sap-cloud-platform-backend-service-tutorial-3-cds-how-to-define-associations-1/)
  * [SAP Cloud Platform Backend service: Tutorial [3]: CDS : how to define associations (2)](https://blogs.sap.com/2019/02/21/sap-cloud-platform-backend-service-tutorial-4-cds-how-to-define-associations-2/)

## Navigate to the Display Customers App from the Manage Travels App via a Link
You may want to display customer names in the list report table as links. The links should trigger the external navigation to the corresponding object page of the customer app displaying the customer's details.
### Task Flow
You will first open the apps in the local sandbox environment. Then, you will add the links and check the results.
### Prerequisites
You have completed the exercise Navigate to the Display Customers App from the Manage Travels App by Pressing the Toolbar Button in the unit Illustrating the Navigation Concept in SAP Fiori Elements for OData V4 (lesson: Configuring External Navigation). Alternatively, you can check out its solution branch: [solution/add-toolbar-button-to-navigate-to-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-toolbar-button-to-navigate-to-customer-app).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_32D9D0352892909D:uebung)
### Steps
  1. Open the app.
    1. Add /sandbox/index.html to the end of the URL of the sap/cds server welcome page. This opens local sandbox environment that simulates SAP Fiori launchpad for testing the external navigation.
    2. Select the _Travels_ tile to open the _Manage Travels_ app.
  2. Add the links.
    1. You will add links to the customer names. These links will trigger navigation to the _Display Customers_ app, showing the corresponding object page.
    2. Open layouts.cds in the SAP Business Application Studio.
    3. Add the following code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011

annotate TravelService.Travel with {
    @(Common: {
        SemanticObject: 'Customer',
        SemanticObjectMapping: [
            {
                LocalProperty : to_Customer_CustomerID,
                SemanticObjectProperty: 'CustomerID'
            }
        ]})
        to_Customer
    };

```

You have added the @Common.Semantic Object and @Common.SemanticObjectMapping annotations to the association to_Customer. Note that this is a managed association that represents the local foreign key property to_Customer_CustomerID.
  3. Check the results.
    1. Open manifest.json. You can see the Customer semantic object in the crossNavigation/inbounds section. It is used by the local sandbox environment.
    2. Switch to the application window. You can see the list report of the _Manage Travels_ app. It is running in the local sandbox environment simulating SAP Fiori launchpad. You can see that the customers' names are displayed as links now.

### Result
In this lesson you learned how to easily configure table cells to be displayed as links which trigger external navigation to another app.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-link-to-navigate-to-customer-app](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-link-to-navigate-to-customer-app).
  * You can find the link to the direct comparison of the branch to the previous one on [Github](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-toolbar-button-to-navigate-to-customer-app..solution/add-link-to-navigate-to-customer-app).

Note
  * You can also skip the @Common.SemanticObjectMapping annotation.
  * You can find the solution branch without the @Common.SemanticObjectMapping annotation on: [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-link-by-annotating-target-property).
  * You can find the link with the comparison of the solution branch without the @Common.SemanticObjectMapping annotation and the solution branch containing the @Common.SemanticObjectMapping annotation on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-link-to-navigate-to-customer-app..solution/add-link-by-annotating-target-property).

### Next Steps
For more information, see [Navigation from an App (Outbound Navigation)](https://ui5.sap.com/#/topic/d782acf8bfd74107ad6a04f0361c5f62.html).
[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/illustrating-the-navigation-concept-in-sap-fiori-elements-for-odata-v4_23b49588-7d8b-3d71-9c10-049d123d1307)
