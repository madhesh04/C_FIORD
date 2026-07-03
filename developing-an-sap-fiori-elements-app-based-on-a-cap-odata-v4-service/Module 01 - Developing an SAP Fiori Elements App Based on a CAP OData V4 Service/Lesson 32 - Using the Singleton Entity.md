# Using the Singleton Entity

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/using-the-singleton-entity_fbea2947-c372-4bed-8d20-b61ceb327d4f*

Objective
After completing this lesson, you will be able to explain how you can create and use the singleton entity in your apps.
## The Singleton Entity
A singleton is a special one-element entity introduced in OData V4. It can be referred by its name from the service root, without having to know its key and without requiring an entity set.
You can annotate an entity with @odata.singleton or @odata.singleton.nullable to use it as a singleton in your service in CAP projects.
Code Snippet
Copy codeSwitch to dark mode

```

123456789

service myService {
  @odata.singleton entity MySingleton {
    key id : String; // can be omitted
    prop1 : String;
    prop2 : Boolean;
  }
}

```

In your CAP CDS annotations, you can reference properties from the singleton entity by using the $edmjson inline mechanism.
Let us consider a typical use case for singletons in self service apps. Here, you might want to load the user context describing the user's authorizations and default settings. In this case, the back end can simply use the log on ID of the user to send the relevant data through the corresponding singleton, exposing the user context.
Check another example of the use cases for singleton entities in SAP Fiori elements applications for OData V4 "Using Singletons to influence the visibility of the Create, Delete and Edit Buttons". For more information, see [Actions](https://sapui5.hana.ondemand.com/sdk/#/topic/cbf16c599f2d4b8796e3702f7d4aae6c.html).
Note
$edmJson is supported only with CDS compiler 2.3.0 or higher.
For more information about using the $edmjson inline mechanism in CAP CDS annotations, see Dynamic Expressions section in [Serving OData APIs.](https://cap.cloud.sap/docs/advanced/odata)
## Use the Singleton Entity for Constant Values of the Bullet Micro Chart
### Usage Scenario
In this exercise, you will see one of the use cases for using a singleton entity in SAP Fiori elements application for OData V4. Instead of assigning constant values to annotation properties, like you did in the previous exercise for the bullet micro chart, you will reference values from the singleton entity. Thus, you will modify the previous exercise in which you have added a bullet micro chart to the subobject page header.
Next, you will put the static boolean values into the corresponding CSV file for the singleton entity. With the use of singletons, you reduce the amount of metadata, and have all the constant values in one singleton file.
### Task Flow
In this lesson, you will define a new entity called SupplementScope in your CAP data model. The annotation @odata.singleton will make it a singleton entity.
Next, you will create a corresponding CSV file for the SupplementScope entity and will add values for the entity's properties. Then, you will reference singleton properties in the annotations by using the inline $edmjson mechanism.
### Prerequisites
You have completed the exercise Add the Bullet Micro Chart and the Progress Indicator to the Header Area in the unit Shaping the Header Area of the Object Page (lesson: Enriching the Object Page Header with Micro Charts). Alternatively, you can check out its solution branch: [solution/add-bullet-micro-chart-and-progress-indicator-to-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-bullet-micro-chart-and-progress-indicator-to-op).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_7B30DC2B62FED084:uebung)
### Steps
  1. Open your CAP project in SAP Business Application Studio.
  2. Define the new entity SupplementScope and annotate it with @odata.singleton.
    1. To open _Search files by names_ , press Ctrl+P on your keyboard.
    2. Choose **schema.cds fiori-elements-v4-cap-advanced/db**. The schema.cds file opens.
    3. Add the following code snippet to the schema.cds file:
Code Snippet
Copy codeSwitch to dark mode

```

123456789

@odata.singleton
entity SupplementScope {
  MinimumValue : Integer @Common.Label: 'Minimum Value';
  MaximumValue : Integer @Common.Label: 'Maximum Value';
  TargetValue : Integer @Common.Label: 'Target Value';
  DeviationRangeLowValue : Integer @Common.Label: 'Deviation Range Threshold';
  ToleranceRangeLowValue : Integer @Common.Label: 'Tolerance Range Threshold';
}

```

  3. Create a corresponding .csv file for the singleton entity and fill it with data.
    1. In the _Explorer_ view, select Projects\db\data.
    2. Expand _data_.
    3. Right-click on _data_.
    4. Select _New File..._.
    5. Enter the name of the new entity as sap.fe.cap.travel-SupplementScope.csv.
    6. Add the following properties and the corresponding values to the file:
Code Snippet
Copy codeSwitch to dark mode

```

123

DeviationRangeLowValue;ToleranceRangeLowValue;MinimumValue;MaximumValue;TargetValue
20;75;0;120;100

```

  4. Add the singleton entity SupplementScope to the service definition.
    1. To open _Search files by names_ , press Ctrl+P on your keyboard.
    2. Choose **travel-service.cds**. The travel-service.cds file opens.
    3. Add the following code snippet to the travel-service.cds file.
Code Snippet
Copy codeSwitch to dark mode

```

1

entity SupplementScope as projection on my.SupplementScope;

```

  5. Replace the constant values in the @UI.DataPoint annotation with the corresponding paths to the singleton properties.
    1. In the _Explorer_ view, select Projects\app\travel_processor\webapp.
    2. In the _Explorer_ view, select Projects\app\travel_processor\webapp.
    3. Right-click on _webapp_.
    4. Select _Show Page Map_. The Page Map of the _Travel_ application appears.
    5. Select the _Edit_ icon of the subobject page. The Page Map of the _BookingObjectPage_ appears.
    6. Expand the _Header Sections_.
    7. Select _Total Supplements_.
    8. In the right pane, select _Edit in source file_. The layout.cds file appears.
    9. To replace the existing constant values with the corresponding paths that refer to the singleton entity, add the following code snippet in the @UI.DataPoint annotation:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617

annotate TravelService.Booking with @(
  UI.DataPoint #TotalSupplPrice1: {
      Value : TotalSupplPrice,
      MinimumValue : {$edmJson: {$Path: '/SupplementScope/MinimumValue'}},
      MaximumValue : {$edmJson: {$Path: '/SupplementScope/MaximumValue'}},
      TargetValue : {$edmJson: {$Path: '/SupplementScope/TargetValue'}},
      Visualization : #BulletChart,
      // Criticality : TotalSupplPrice, // it has precedence over criticalityCalculation => in order to have the   criticality       color do not use it
     CriticalityCalculation: {
          $Type : 'UI.CriticalityCalculationType',
          ImprovementDirection : #Maximize,
          DeviationRangeLowValue: {$edmJson: {$Path: '/SupplementScope/DeviationRangeLowValue'}},
          ToleranceRangeLowValue: {$edmJson: {$Path: '/SupplementScope/ToleranceRangeLowValue'}}
    }
},

```

  6. Check the newly created singleton entity in the $metadata file.
    1. Open the _Welcome to @sap/cds Server_ page.
    2. Select _/processor/$metadata_.
#### Result
In the $metadata document, you can see that the new singleton entity SupplementScope is added to the EntityContainer. You can also see the @UI.DataPoint annotation in XML format.
  7. View the bullet micro chart on the header section.
    1. Open the _Manage Travels_ app on the browser.
    2. Under _Bookings_ , select the first row.
#### Result
You can see the bullet micro chart on the object page header.

### Result
In this lesson, you have learned to use a singleton entity in your SAP Fiori elements applications for OData V4.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/use-singleton-for-bullet-micro-chart-on-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/use-singleton-for-bullet-micro-chart-on-op).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-bullet-micro-chart-and-progress-indicator-to-op..solution/use-singleton-for-bullet-micro-chart-on-op).

### Next Steps
For more information, see
  * [Singletons](https://cap.cloud.sap/docs/advanced/odata#singletons)
  * [Actions](https://sapui5.hana.ondemand.com/sdk/#/topic/cbf16c599f2d4b8796e3702f7d4aae6c)

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/shaping-the-header-area-of-the-object-page_f8ebc9e1-d934-3c8b-91ab-855a5c419339)
