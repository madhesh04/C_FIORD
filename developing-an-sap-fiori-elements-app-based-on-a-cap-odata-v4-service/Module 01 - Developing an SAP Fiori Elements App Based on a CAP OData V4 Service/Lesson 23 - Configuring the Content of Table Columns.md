# Configuring the Content of Table Columns

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/creating-a-visual-representation-of-a-progress-indicator_e09671c3-25f7-4813-ab24-394c905ede50*

Objective
After completing this lesson, you will be able to display a progress indicator in a table column.
## Visual Representation of a Progress Indicator
You can visualize your content as a table both in the list report and on the object page. There are different types of tables you can use, based on your use case. The default and recommended table type is the responsive table, as it is supported by all devices. For an aggregate-based service, the default table type is the analytical table. For more information about the table types, see [Setting the Table Type](https://sapui5.hana.ondemand.com/sdk/#/topic/7f844f1021cd4791b8f7408eac7c1cec).
SAP Fiori elements makes it possible to present your table content in a visually appealing manner. In addition to text, you can configure the table cells to display micro charts, a rating indicator, a progress indicator, a contact quick view which displays additional information, images, and more.
For more information, see [Configuring Tables](https://sapui5.hana.ondemand.com/sdk/#/topic/f4eb70f4808b48adb6ea03a4017aba24).
## Add a Progress Indicator Column to the Table
You can add a visual progress indicator to a table. This gives you a quick overview of the current status of a table entry.
### Task Flow
In this exercise, you will first add a new property called _Progress_ to a _Travel_ entity.
Then, you will implement a method for updating the _Progress_ property when the _Travel_ is created or changed.
You will also add the _Progress_ property to the _Travel_ entity's .csv file to populate the initial data.
Finally, you will use the Page Editor to configure a new progress indicator column in the list report table.
### Prerequisites
You have completed the exercise Create an Application-Specific Action with a Mandatory Parameter in the unit Examining Actions Available on the List Report (lesson: Creating App-Specific Actions). Alternatively, you can check out its solution branch: [solution/create-action-with-a-mandatory-parameter](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/create-action-with-a-mandatory-parameter)
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_AD1958B9AD100B3:uebung)
### Steps
  1. Add the _Progress_ property to the _Travel_ entity.
    1. Open the db/schema.cds file in the file explorer. Here you can define the properties for the entities and the associations between the entities.
    2. Add the _Progress_ property to line 20 in the schema.cds file by pasting the following code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

Progress : Integer @readonly;

```

  2. Implement a method for updating the _Progress_ property.
    1. Open the srv/travel-service.js file. Here you can implement the method for updating the _Progress_ property.
    2. Add the following code snippet to the file:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223

/**
   * Calculate the progress of the travel booking.
   */

  // Travel is new (0 bookings) = 10%
  // Travel contains at least one booking = 50%
  // Travel contains at least two bookings = 65%
  // Supplement target reached + 5 % per booking, max 90%
  // Travel is accepted = 100% -> see acceptTravel
  // Travel is rejected = 0% -> see rejectTravel
 this.before ('SAVE', 'Travel', async req => {
    if (!req.event === 'CREATE' && !req.event === 'UPDATE') return //only calculate if create or update
    let score = 10
    const { TravelUUID } = req.data
    const res = await SELECT .from(Booking.drafts) .where `to_Travel_TravelUUID = ${TravelUUID}`
    if (res.length >= 1) score += 40
    if (res.length >= 2) score += 15
    res.forEach(element => {
      if (element.TotalSupplPrice > 70) score += 5
    });
    if (score > 90) score = 90;
    req.data.Progress = score
  })

```

    3. This adds the implementation of the method for updating the _Travel Progress_. The method is triggered by selecting the _Save_ button on the UI. At this moment, CAP will convert the draft into an active document.
The _Travel Progress_ is calculated as follows:
       * Creating the travel brings the progress to 10%.
       * Adding a booking brings the progress to 50%.
       * Adding another booking brings the progress to 65%.
       * Each booking can have supplements. If the booking's supplement target is reached, the progress increases by 5% per booking, to a maximum of 90%.
       * If the travel is accepted, the progress is set to 100%.
       * If the travel is rejected, the progress is set to 0%.
    4. Add the following code snippet to the Action Implementations section of srv/travel-service.js:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

  this.on ('acceptTravel', async req => {
    await UPDATE (req.subject) .with ({TravelStatus_code:'A'})
    return this._update_progress(req.subject, 100)
  })
  this.on ('rejectTravel', async req => {
    await UPDATE (req.subject) .with ({TravelStatus_code:'X'})
    return this._update_progress(req.subject, 0)
  })

  this._update_progress = async function (travel, progress){
    return await UPDATE (travel) . with({Progress : progress})
  }

```

    5. This creates a new method called _update_progress for updating the _Progress_ property. This method is called when the acceptTravel and rejectTravel actions are executed.
  3. Add the new property to the travel's .csv file.
    1. In file explorer, select db/data/sap.fe.cap.travel-Travel.csv. Here you can add the _Progress_ property with the corresponding values.
    2. To implement the changes faster, copy the sap.fe.cap.travel-Travel.csv from this solution's [GitHub branch](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/blob/solution/add-progress-indicator-to-table-column/db/data/sap.fe.cap.travel-Travel.csv) and replace your local version of the file with it. It already contains the _Progress_ property with the corresponding data.
  4. Add the new progress indicator to the table column using the Page Editor.
    1. Select _Edit_ on the list report page.
    2. Expand the _Columns_ property.
    3. Select the plus icon to add a new property.
    4. Select _Add Progress_ Columns.
    5. In the pop-up, expand the _Columns_ dropdown menu.
    6. Select _Progress_ as it is the property you added to the _Travel_ entity.
  5. You can see that a new column called _Progress_ has been added to _Columns_. On the right, you can edit settings.
    1. Try changing the column title, for example, to _Progress of Travel_.
    2. Select the globe icon to add the label text to i18n.properties for translation.
    3. You will be prompted to generate a text key in the i18n file. Select _Apply_ to confirm.
  6. Check the _Target_ property; it is filled in 100%. Choose the _Navigate to Source Code_ icon in the _Progress of Travel_ column. This shows the added annotations.
    1. The layouts.cds file has the UI relevant annotations. The added i18n annotation is highlighted.
    2. Ctrl+left click on the @UI.DataPoint#Progress annotation in the file. You have navigated to the definition of the @UI.DataPoint annotation with the qualifier Progress1. The value is the Progress property we previously added to the travel.
  7. Navigate to the _App_ window. If necessary, select _Show More per Row_ to display all table columns. You can now see that the _Progress of Travel_ is displayed for existing travels.
  8. Check the results.
    1. Create a new travel.
    2. In the _Agency_ text box, select _Input Help_ to open a dropdown menu with the existing values.
    3. Select the second entry from the top.
    4. In the _Customer_ text box, select _Input Help_ to open a dropdown menu with the existing values.
    5. Select the third entry from the top.
    6. Select the _Create_ button at the bottom of the screen.
    7. You can see the newly created travel with a _Progress of Travel_ column. The _Progress of Travel_ stands at 10%. You can see the progress 10 of 100 in the tool tip.

### Result
You have added a new column _Progress of Travel_ to the table in the list report page.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-progress-indicator-to-table-column](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-progress-indicator-to-table-column).
  * A direct comparison of this branch with the previous exercise is available on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/create-action-with-a-mandatory-parameter..solution/add-progress-indicator-to-table-column).

### Next Steps
For more information, see [Configuring Tables](https://sapui5.hana.ondemand.com/sdk/#/topic/f4eb70f4808b48adb6ea03a4017aba24).
