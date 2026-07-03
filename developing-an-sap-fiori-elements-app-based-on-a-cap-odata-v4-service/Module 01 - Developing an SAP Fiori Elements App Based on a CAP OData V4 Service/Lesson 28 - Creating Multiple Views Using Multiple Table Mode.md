# Creating Multiple Views Using Multiple Table Mode

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/creating-multiple-views-using-multiple-table-mode_aa0befbd-0bf8-492e-be4f-9fbe4dfc4c1b*

Objective
After completing this lesson, you will be able to configure multiple views using multiple table mode in the list report.
## Multiple Views Using Multiple Table Mode
In the previous lesson, you learned how to add several views as a single table mode to the list report. In this lesson, you will learn about multiple table mode. In multiple table mode SAP Fiori elements creates a separate table instance for each view. It allows you to define different table toolbars and different table columns for each view. You can also have a separate table variant management for each view.
Note
SAP Fiori design guidelines don’t recommend using table variant management. For more information, see [List Report – Content Area](https://experience.sap.com/fiori-design-web/list-report-content-area-fiori-elements/).
Each view is displayed as a tab on the table. An icon tab bar is rendered above the table for switching between the views. Only the table on the currently selected tab is visible.
Besides tables, you can also apply multiple table mode on charts.
For step-by-step instructions, use the Configure Multiple Views aid from guided development. You can also use the Page Editor to create multiple views.
### Further Reading
  * [Multiple Views on List Report Tables](https://sapui5.hana.ondemand.com/sdk/#/topic/a37df408044e41ef84e67207c8658d4f)
  * [Defining Multiple Views on a List Report Table](https://sapui5.hana.ondemand.com/sdk/#/topic/37aeed74e17a42caa2cba3123f0c15fc.html)

## Create Multiple Table Views Using Multiple Table Mode
### Usage Scenario
Using the multiple table mode, you want to visualize the data displayed on the Travels table based on its travel status. The columns and toolbar actions can differ in each table view.
### Task Flow
In this exercise, you will perform the following tasks:
  * Create three different table views of the table.
  * Add an @UI.SelectionPresentationVariant annotation for each table view.
  * Define columns and actions for each table view.

### Prerequisites
You have completed the exercise Add a Contact Quick View to the Table in the unit Configuring the Content of Table Columns (lesson: Configuring Contact Quick Views in a Table). You also need to undo the changes made in the exercise Create Multiple Table Views Using Single Table Mode before starting this exercise. Alternatively, you can check out the solution branch of the exercise Add a Contact Quick View to a Table[solution/add-quick-contact-view-to-table](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-quick-contact-view-to-table).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_3690F4A2C872F5A2:uebung)
### Steps
  1. Open your CAP project in SAP Business Application Studio.
    1. In the _Explorer_ view, select Projects\fiori-elements-v4-cap-advanced\app\travel_processor\webapp.
    2. Right-click on _webapp_ and select _Show Page Map_. The Page Map of the Manage Travels application appears.
  2. Create table views.
    1. On the list report page, choose the _Edit_ option. The TravelList Page Editor appears.
    2. Select _Views_.
    3. Click the _Add_ icon to add a new table view.
    4. Select _Add Table View_. The Add Table View dialog appears.
    5. Select _Add_ to add the new table view.
    6. Repeat steps c to e to create another table view.
  3. Define the labels for the table views.
    1. Select the required table view.
    2. In the right pane, under _View Label_ , enter the name of the table view as Open.
    3. Click the _Edit in source file_ icon next to the label of the table view.
    4. Select _Apply_ to rename the existing value.
    5. Repeat steps a to d to define the labels of other table views as Accepted and Canceled.
  4. Configure the @UI.SelectionPresentationVariant annotation of the table view, Open.
    1. Select the table view, Open.
    2. In the right pane, under Presentation Variant: Annotation, select the _Edit in source code_ icon. The layout.cds file opens, and you can see the code generated for @UI.SelectionPresentationVariant.
    3. Complete the code by defining the SelectOptions property.
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213141516171819

annotate TravelService.Travel with @(
    UI.SelectionPresentationVariant #tableView : {
        $Type              : 'UI.SelectionPresentationVariantType',
        PresentationVariant: ![@UI.PresentationVariant],
        SelectionVariant   : {
            $Type        : 'UI.SelectionVariantType',
            SelectOptions: [{
                $Type       : 'UI.SelectOptionType',
                PropertyName: TravelStatus_code,
                Ranges      : [{
                    $Type : 'UI.SelectionRangeType',
                    Sign  : #I,
                    Option: #EQ,
                    Low   : 'O',
                }, ],
            }],
        },
        Text               : '{i18n>Open}',
    },

```

Note
The code snippet for the table view, Open is partially generated by the Page Map. You must explicitly add the code for the SelectOptions property in the SelectionVariant.
In the code snippet, the @UI.LineItem annotation is not referenced under PresentationVariant/Visualizations property because you have not defined any columns or actions for the Open table view. Thus, the Open table view uses the default @UI.LineItem annotation without any qualifier.
  5. Configure the @UI.SelectionPresentationVariant annotation of the table view, Accepted.
    1. Select the table view, Accepted.
    2. Perform steps b to c of step 4.
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213141516171819202122

 UI.SelectionPresentationVariant #tableView1: {
        $Type              : 'UI.SelectionPresentationVariantType',
        PresentationVariant: {
            $Type         : 'UI.PresentationVariantType',
            Visualizations: ['@UI.LineItem#tableView', ],
        },
        SelectionVariant   : {
            $Type        : 'UI.SelectionVariantType',
            SelectOptions: [{
                $Type       : 'UI.SelectOptionType',
                PropertyName: TravelStatus_code,
                Ranges      : [{
                    $Type : 'UI.SelectionRangeType',
                    Sign  : #I,
                    Option: #EQ,
                    Low   : 'A',
                }, ],
            }],
        },
        Text               : '{i18n>Accepted}',
    }
);

```

  6. Configure the @UI.SelectionPresentationVariant of the table view, Canceled
    1. Select the table view, Canceled.
    2. Perform steps b and c of step 4.
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213141516171819202122

 UI.SelectionPresentationVariant #tableView2: {
        $Type              : 'UI.SelectionPresentationVariantType',
        PresentationVariant: {
            $Type         : 'UI.PresentationVariantType',
            Visualizations: ['@UI.LineItem#tableView1', ],
        },
        SelectionVariant   : {
            $Type        : 'UI.SelectionVariantType',
            SelectOptions: [{
                $Type       : 'UI.SelectOptionType',
                PropertyName: TravelStatus_code,
                Ranges      : [{
                    $Type : 'UI.SelectionRangeType',
                    Sign  : #I,
                    Option: #EQ,
                    Low   : 'X',
                }, ],
            }],
        },
        Text               : '{i18n>Canceled}',
    }
);

```

  7. Configure actions for the table view, Accepted.
    1. On the TravelList Page Map, click to expand the Accepted table view. The Table Toolbar appears.
    2. Click Table Toolbar.
    3. Select Actions and click the _Add_ icon.
    4. Click Add Actions. The Add Action dialog appears.
    5. From the Actions drop-down, select TravelService.rejectTravel.
    6. Click Add.
  8. Configure columns for the table view, Accepted.
    1. Select Columns and click the add icon.
    2. Select Add Basic Columns. The Add Basic Column dialog appears.
    3. From the Columns dropdown, select the required columns.
    4. Click Add to add the columns to the table view. The following code snippet shows the @UI.LineItem annotation generated by the Page Editor.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223

  UI.LineItem #tableView : [
        {
            $Type : 'UI.DataFieldForAction',
            Action : 'TravelService.rejectTravel',
            Label : 'rejectTravel',
        },
        {
            $Type : 'UI.DataField',
            Value : Description,
        },
        {
            $Type : 'UI.DataField',
            Value : LastChangedAt,
        },
        {
            $Type : 'UI.DataField',
            Value : TravelID,
        },
        {
            $Type : 'UI.DataField',
            Value : to_Customer_CustomerID,
        },],

```

Note
The Page Editor has generated a new @UI.LineItem annotation (with the qualifier #tableView) because you have defined the columns and actions for the Accepted table view. The @UI.LineItem annotation is referenced under PresentationVariant/Visualizations of the corresponding @UI.SelectionPresentationVariant annotation.
  9. Configure columns for the table view, Canceled
    1. On the TravelList Page Map, click to expand the Canceled table view. The Table Toolbar appears.
    2. Select Columns and click the add icon.
    3. Select Add Basic Columns. The Add Basic Column dialog appears.
    4. From the Columns drop-down, select the required columns.
    5. Click _Add_ to add the columns to the table view. The following code snippet shows the @UI.LineItem annotation generated by the Page Editor.
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415161718192021222324

annotate TravelService.Travel with @(
    UI.LineItem #tableView1                    : [
        {
            $Type: 'UI.DataField',
            Value: Description,
        },
        {
            $Type: 'UI.DataField',
            Value: LastChangedAt,
        },
        {
            $Type: 'UI.DataField',
            Value: TravelID,
        },
        {
            $Type: 'UI.DataField',
            Value: to_Agency_AgencyID,
        },
        {
            $Type: 'UI.DataField',
            Value: to_Customer_CustomerID,
        },
    ],

```

Note
The Page Map has generated the @UI.LineItem annotation with the qualifier #tableView1. The @UI.LineItem annotation is referenced under PresentationVariant/Visualizations of the corresponding @UI.SelectionPresentationVariant annotation.
  10. Check the table views on the Travels app.
    1. Open the Travels app. You can see the newly created table views displayed as tabs. By default, the Open tab is selected.
    2. On the Travels table, select the check box corresponding to the required travels.
    3. Select Reject Travel.
    4. Click the Accepted tab. The table displays only the selected columns and the travel entries with the travel status Accepted.
    5. Click Canceled. The table displays only the selected columns and travel entries that has travel status as Canceled.

### Result
You have enabled the multiple table mode on list report table.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/create-multiple-table-views-multiple-table-mode](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/create-multiple-table-views-multiple-table-mode).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-quick-contact-view-to-table..solution/create-multiple-table-views-multiple-table-mode).

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/using-multiple-views-in-the-list-report_ab22f486-7a2c-3d0e-89eb-99a5be56f1e5)
