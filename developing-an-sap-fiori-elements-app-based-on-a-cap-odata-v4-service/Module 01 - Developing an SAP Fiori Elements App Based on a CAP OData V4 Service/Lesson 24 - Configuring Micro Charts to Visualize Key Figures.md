# Configuring Micro Charts to Visualize Key Figures

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-micro-charts-to-visualize-key-figures_cf7dc7e4-98d4-4c0b-84f9-626f43ced1c3*

Objective
After completing this lesson, you will be able to visualize semantically-colored representations of the customer-defined key figures and thresholds.
## Micro Charts
You can visualize a number of data points as micro charts in table cells, both in the list report and on the object page. They are non-interactive. You can display changes in the data in an easy and condensed way. You can choose from different types of micro charts, such as area, bullet, line, radial, and stacked bar micro charts.
![Examples of different micro charts](../images/a624b2bded00a220.png)
A micro chart will not display any title, description, measure labels or footers while used in a table column. By default, the micro chart has a size "XS". You can change the size by adding a corresponding setting to the manifest.json file. For more information, see [Adding a Micro Chart to a Table](https://sapui5.hana.ondemand.com/sdk/#/topic/b8312a4adde54f33a89480dbe12d8632). You can use SAP Fiori tools to create a new column containing a micro chart. You can choose between using guided development (the _Add a Smart Micro Chart to a Table_ guide) and the Page Editor.
## Add a Bullet Micro Chart to the Table Column
You may want to provide an overview of the total amount of supplements per booking without having to navigate to each booking's detailed page. To do this, you can use a bullet micro chart.
The micro chart is displayed in the booking table on the object page. It has a predefined target and two thresholds. Its bar chart will show a different color, depending on the value for each booking. This provides a quick overview of the values for each booking without having to navigate to the sub-object page.
### Task Flow
First, you will introduce and implement a new property in the _Booking_ entity called _Total Amount of Supplements_.
Then, you'll use the application modeler to add a new column containing a bullet micro chart to the _Booking_ table.
Finally, you will update the .csv file containing the initial app data to include the new property and add the relevant values for existing bookings.
### Prerequisites
You have completed the exercise Add a Progress Indicator Column to the Table in the unit Configuring the Content of Table Columns (lesson: Creating a Visual Representation of a Progress Indicator). Alternatively, you can check out its solution branch: [solution/add-progress-indicator-to-table-column](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-progress-indicator-to-table-column).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_F304F32DE571C4A3:uebung)
### Steps
  1. Open the selected travel's object page.
  2. Switch to SAP Business Application Studio and add the following code snippet to the Booking entity definition (line 37 of db/schema.cds):
Code Snippet
Copy codeSwitch to dark mode

```

1

TotalSupplPrice : Decimal(16, 3);

```

This adds a new property TotalSupplPrice to the entity Booking. It displays the total price of all supplements in the booking.
  3. Open srv/travel-service.js to implement a method called _update_totals_supplement; this will update the TotalSupplPrice property:
Code Snippet
Copy codeSwitch to dark mode

```

12345678

 /**
   * Update the Booking's TotalSupplPrice
   */
this._update_totals_supplement = async function (booking) {
    const { totals } = await SELECT.one `coalesce (sum (Price),0) as totals` .from (BookingSupplement.drafts) .where
     `to_Booking_BookingUUID = ${booking}`
    return  UPDATE (Booking.drafts, booking) .with({TotalSupplPrice: totals})
}

```

  4. Update the method this.after ( 'UPDATE', 'BookingSupplement.drafts') in travel-service.js:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

/**
   * Update the Travel's TotalPrice when a Supplement's Price is modified.
   */
 this.after ('UPDATE', 'BookingSupplement.drafts', async (_,req) => { if ('Price' in req.data) {
    // We need to fetch the Travel's UUID for the given Supplement target
    const { booking } = await SELECT.one `to_Booking_BookingUUID as booking`
      .from (BookingSupplement.drafts).where({BookSupplUUID:req.data.BookSupplUUID})
    const { travel } = await SELECT.one `to_Travel_TravelUUID as travel` .from (Booking.drafts)
      .where `BookingUUID = ${booking} `
    await this._update_totals_supplement (booking)
    return this._update_totals4 (travel)
  }})

```

  5. Use the page editor to add a new column with a bullet micro chart to the table on the object page.
    1. Select _webapp > Show Page Map_ and click the pencil icon on _Object Page_.
    2. Expand _Bookings > Table > Columns_ and select the plus icon to add a new column. Choose _Chart Column_ and _Bullet_ as the chart type.
    3. Choose _TotalSupplPrice_ as a _Value_ and enter 120 as the _Maximum Value_. Select _Add_.
    4. Note that a new column _TotalSupplPrice_ has been added. Change its title to _Supplements_ and select the globe icon to add the text to i18n.properties.
    5. Select _Edit in source file_ to check the annotations generated by the page editor.
    6. You can see the generated annotations @UI.DataPoint and @UI.Chart. Add the values as shown in the code snippet below:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415161718192021222324252627

annotate TravelService.Booking with @(
    UI.DataPoint #TotalSupplPrice: {
        Value                 : TotalSupplPrice,
        MinimumValue          : 0,
        MaximumValue          : 120,
        TargetValue           : 100,
        Visualization         : #BulletChart,
        //  Criticality : TotalSupplPrice, // it has precedence over criticalityCalculation => in order to have the criticality color do not use it
        CriticalityCalculation: {
            $Type                 : 'UI.CriticalityCalculationType',
            ImprovementDirection  : #Maximize,
            DeviationRangeLowValue: 20,
            ToleranceRangeLowValue: 75
        }
    },
    UI.Chart #TotalSupplPrice    : {
        ChartType        : #Bullet,
        Title            : 'total supplements',
        AxisScaling      : {$Type: 'UI.ChartAxisScalingType', },
        Measures         : [TotalSupplPrice, ],
        MeasureAttributes: [{
            DataPoint: '@UI.DataPoint#TotalSupplPrice',
            Role     : #Axis1,
            Measure  : TotalSupplPrice,
        }, ],
    }
);

```

  6. Open sap.fe.travel-Booking.csv. This file contains initial app data for the entity Booking. As you have added a new property TotalSupplPrice to this entity, you also have to update this file with a new column TotalSupplPrice. The column will contain the values for existing bookings.
    1. Copy and replace the sap.fe.cap.travel-Booking.csv file from the Github repository at [db/data/sap.fe.cap.travel-Booking.csv](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/blob/solution/add-bullet-micro-chart-to-table/db/data/sap.fe.cap.travel-Booking.csv). This file contains the TotalSupplPricecolumn with the updated values.
  7. Switch back to the app window and check the results.
    1. Select a travel to navigate to its object page.
    2. You can see the new column in the _Bookings_ table. It displays the total sum of Supplements per booking visualized as a bullet micro chart.

### Result
You have learned how to add and configure a bullet micro chart to a table column.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-bullet-micro-chart-to-table](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-bullet-micro-chart-to-table).
  * A direct comparison of this branch with the previous exercise is available on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-progress-indicator-to-table-column..solution/add-bullet-micro-chart-to-table).
