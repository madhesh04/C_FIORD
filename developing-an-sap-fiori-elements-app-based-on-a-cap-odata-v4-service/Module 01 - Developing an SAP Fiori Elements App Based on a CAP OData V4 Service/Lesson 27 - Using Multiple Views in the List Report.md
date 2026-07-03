# Using Multiple Views in the List Report

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-multiple-views-using-single-table-mode_f66bbb36-20de-4d26-a25a-f27048a5b78a*

Objective
After completing this lesson, you will be able to configure several table views using single table mode in the list report.
## Multiple Views Using Single Table Mode
By default, the list report contains one table displaying the data for one business object.
For more complex scenarios you may need to provide multiple views of a table displaying one business object. Each view can display different pre-filtered states.
Technically, the UI contains just a single table instance with one table toolbar. Table-level view management is also available, but Fiori Design Guidelines strongly advise against it. For more information, see [List Report – Content Area](https://experience.sap.com/fiori-design-web/list-report-content-area-fiori-elements/).
A segmented button is used to switch between the views. If more than three views are present, selection control is shown instead.
You can enable the display of the number of total rows in the view by adding the showCounts setting to the manifest.json file. For more information, see [Defining Multiple Views on a List Report Table - Single Table Mode](https://sapui5.hana.ondemand.com/sdk/#/topic/0d390fed360c4c58a0f0619338938de1.html).
You can either use Configure Multiple Views guide from Guided Development for step-by-step instructions or the Page Editor to support you in creating multiple views.
## Create Multiple Table Views Using Single Table Mode
To make a list report table easier to navigate, you can create different views. When a view is selected, only entries that meet the parameters defined in the view will be displayed. As this is one table with different filters, it is known as single table mode.
In this exercise, you will create three table views based on _Travel Status_ : _Open_ , _Accepted_ and _Canceled_.
### Task Flow
In this exercise, you will first define the @UI.SelectionVariant annotations for the three views. Then, you will add these annotations as quick variant selection paths using the Page Map. It will add these annotations to the manifest.json file. Finally, you will check the results.
### Prerequisites
You have completed the exercise Add a Contact Quick View to the Table in the unit Configuring the Content of Table Columns (lesson: Configuring Contact Quick Views in a Table). Alternatively, you can check out its solution branch: [solution/add-quick-contact-view-to-table](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-quick-contact-view-to-table).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_9AD75061D9ACE385:uebung)
### Steps
  1. Define the@UI.SelectionVariant annotations for the three views.
    1. Open the layouts.cds file in SAP Business Application Studio.
    2. Add the @UI.SelectionVariant annotation with the qualifiercanceled to the Travel target entity. It will select the entries with TravelStatus_code='X', that is, _Canceled_.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920

annotate TravelService.Travel with @UI: {
    SelectionVariant #canceled: {
        $Type           : 'UI.SelectionVariantType',
        ID              : 'canceled',
        Text            : 'canceled',
        Parameters      : [

        ],
        FilterExpression: '',
        SelectOptions   : [{
            $Type       : 'UI.SelectOptionType',
            PropertyName: TravelStatus_code,
            Ranges      : [{
                $Type : 'UI.SelectionRangeType',
                Sign  : #I,
                Option: #EQ,
                Low   : 'X',
            }, ],
        }, ],
    },

```

    3. Add the second @UI.SelectionVariant annotation with the qualifier open. This will select the entries with TravelStatus_code='O', that is, _Opened_.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223

SelectionVariant#open  : {
         $Type : 'UI.SelectionVariantType',
         ID : 'open',
         Text : 'open',
         Parameters : [

         ],
         FilterExpression : '',
         SelectOptions : [
             {
                 $Type : 'UI.SelectOptionType',
                 PropertyName : TravelStatus_code,
                 Ranges : [
                     {
                         $Type : 'UI.SelectionRangeType',
                         Sign : #I,
                         Option : #EQ,
                         Low : 'O',
                     },
                 ],
             },
         ],
     },

```

    4. Add the third @UI.SelectionVariant annotation with the qualifier accepted. This will select the entries with TravelStatus_code='A', which means _Accepted_.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920

    SelectionVariant #accepted: {
        $Type           : 'UI.SelectionVariantType',
        ID              : 'accepted',
        Text            : 'accepted',
        Parameters      : [

        ],
        FilterExpression: '',
        SelectOptions   : [{
            $Type       : 'UI.SelectOptionType',
            PropertyName: TravelStatus_code,
            Ranges      : [{
                $Type : 'UI.SelectionRangeType',
                Sign  : #I,
                Option: #EQ,
                Low   : 'A',
            }, ],
        }, ],
    }
};

```

    5. Close the layouts.cds file.
  2. Add these annotations as quick variant selection paths.
    1. Select _Webapp >Show Page Map_.
    2. Add the annotation paths for _Open_ , _Accepted_ , and _Canceled_ travels.
  3. Check the results.
    1. All three annotation paths now appear in the _Quick Variant Selection_.
    2. They also have been added to manifest.json.
    3. You can now see three buttons in your app: _Open_ , _Accepted_ , and _Canceled_.

### Result
You have learned how to add multiple views using single table mode to the list report.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/create-multiple-table-views-single-table-mode](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/create-multiple-table-views-single-table-mode).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-quick-contact-view-to-table..solution/create-multiple-table-views-single-table-mode).

### Next Steps
For more information, see
  * [Multiple Views on List Report Tables](https://ui5.sap.com//#/topic/a37df408044e41ef84e67207c8658d4f)
  * [Defining Multiple Views on a List Report Table - Single Table Mode](https://ui5.sap.com//#/topic/0d390fed360c4c58a0f0619338938de1.html)
