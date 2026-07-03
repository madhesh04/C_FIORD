# Adding a Custom Micro Chart

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/adding-a-custom-micro-chart_e266e9d1-fcde-4aa1-9a79-65bec1c62ef4*

Objective
After completing this lesson, you will be able to create a custom micro chart displaying values calculated in the back end.
## Add a Custom Micro Chart to the Object Page Header of the Display Customers App
You may want to get a quick overview of all the bookings for one passenger. The information should be presented in a visually appealing way in the object page header of the Display Customers app, next to the _Contact Details_ section. The user would see at a glance how many bookings have the status "open", or "canceled", or "new".
To achieve this, you can use the comparison micro chart.
### Task flow
First, you will implement a method in the back end to calculate the number of bookings with different statuses. Then, you will create a local JSON model on the front end to retrieve the corresponding numbers from the back end. Next, you will add a custom header section next to the _Contact Details_ section. Note that this has to be done manually. Finally, you will create the micro chart itself.
### Prerequisites
You have completed the exercise Add Message Strips to the Object Page of the Display Customers App in the unit Discovering the Flexibility of the Programming Model for SAP Fiori Elements for OData V4 (lesson: Using Controller Extensions). Alternatively, you can check out its solution branch: [solution/add-message-strips](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-message-strips).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_8034E5D68FD43DBF:uebung)
### Steps
  1. Implement the method in the back end.
    1. You have already defined the BookingData type in the previous exercise. Now, you will change this type to reflect different booking statuses.
    2. Open the SAP Business Application Studio and choose schema.cds. Add the following code snippet to the BookingData type:
Code Snippet
Copy codeSwitch to dark mode

```

1

type BookingData: { TotalBookingsCount: Integer; NewBookingsCount: Integer; AcceptedBookingsCount: Integer; CancelledBookingsCount: Integer; }

```

    3. Open travel-service.cds. You can see the definition of the getBookingDataOfPassenger function you created in the previous exercise. You will also use it in this exercise.
    4. Open travel-service.js. It contains the implementation of the getBookingDataOfPassenger function from the previous exercise. You will enhance it in this exercise.
    5. Add the following code snippet to travel-service.js (overwrite the existing code from the previous exercise):
Code Snippet
Copy codeSwitch to dark mode

```

1

/** * Function import handler: getBookingDataOfPassenger * @param CustomerID * @returns BookingData */ this.on('getBookingDataOfPassenger', async (req) => { const { CustomerID } = req.data const allCustomerBookings = await SELECT `BookingStatus_code as status`.from (Booking) .where `to_Customer_CustomerID = ${CustomerID}` const bookingData = { TotalBookingsCount: 0, NewBookingsCount: 0, AcceptedBookingsCount: 0, CancelledBookingsCount: 0 } allCustomerBookings.forEach((booking) => { bookingData.TotalBookingsCount++ switch (booking.status) { case 'N': bookingData.NewBookingsCount++ break case 'B': bookingData.AcceptedBookingsCount++ break case 'X': bookingData.CancelledBookingsCount++ break default: break } }) return bookingData; });

```

This enhances the getBookingDataOfPassenger method so that it calculates the number of different booking statuses in the back end.
  2. Create a JSON model in the front end.
    1. As you have adjusted the back-end function, you now also have to adapt the front end method that calls this function. Open PassengerOPExtend.controller.js in SAP Business Application Studio and edit the code as follows:
Code Snippet
Copy codeSwitch to dark mode

```

1

sap.ui.define(['sap/ui/core/mvc/ControllerExtension',"sap/ui/core/message/Message","sap/ui/core/MessageType", "sap/ui/model/json/JSONModel", ], function (ControllerExtension, Message, MessageType, JSONModel) { 'use strict';

```

You have declared sap.ui.model.json.JSONModel which you'll use in your controller extension method.
    2. Add the following code snippet to onAfterBinding. Place it after the declaration of oInfoMessage.
Code Snippet
Copy codeSwitch to dark mode

```

1

 const oPassengerBookingsModel = new JSONModel({ totalBookingsCount: 0, newBookingsCount: 0, acceptedBookingsCount: 0, cancelledBookingsCount: 0 }); this.base.getView().setModel(oPassengerBookingsModel, "passengerBookingsModel");

```

This creates a JSONModel and adds it to your view with its given name "passengerBookingsModel".
    3. Add the following code snippet to onAfterBinding. Put it after the line const oContext = oFunction.getBoundContext(); :
Code Snippet
Copy codeSwitch to dark mode

```

1

 oPassengerBookingsModel.setProperty("/totalBookingsCount", oContext.getProperty("TotalBookingsCount")); oPassengerBookingsModel.setProperty("/newBookingsCount", oContext.getProperty("NewBookingsCount")); oPassengerBookingsModel.setProperty("/acceptedBookingsCount", oContext.getProperty("AcceptedBookingsCount")); oPassengerBookingsModel.setProperty("/cancelledBookingsCount", oContext.getProperty("CancelledBookingsCount"));

```

This binds the properties of your JSONModel to the corresponding properties of the return parameter of the function import.
    4. Adjust the last code block of onAfterBinding as follows:
Code Snippet
Copy codeSwitch to dark mode

```

1

 if (oContext.getProperty("NewBookingsCount") > 0) { this.message = oBookingTableAPI.addMessage(oWarningMessage); oExtensionAPI.showMessages([oInfoMessage]); }

```

  3. Add a custom header section.
    1. Open manifest.json and add the following code under "PassengerObjectPage"/"options"/"settings"/"content":
Code Snippet
Copy codeSwitch to dark mode

```

1

 "header": { "facets": { "CustomHeaderFacetContentBased1": { "template": "sap.fe.cap.customer.ext.fragment.BookingStatus", "title": "{i18n>bookingStatus}", "visible": "true", "position": { "placement": "After", "anchor": "ContactDetails" } } } },

```

You have declared a new custom header facet next to the _Contact Details_ header facet.
    2. Open i18n>i18n.properties. Here, you can add some text to the UI that should be translated.
    3. Add the following code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

#XTIT: Custom header title bookingStatus=Booking Status

```

This adds the title of your custom header section.
  4. Create the micro chart.
    1. Right-click on the fragment folder and choose _New File_.
    2. Create a new file called BookingStatus.fragment.xml and add the following code for your micro chart:
Code Snippet
Copy codeSwitch to dark mode

```

1

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" xmlns:macros="sap.fe.macros" xmlns:mc="sap.suite.ui.microchart"> <VBox id="BookingStatusOverview" displayInline="true"> <mc:ComparisonMicroChart size="S" maxValue="{passengerBookingsModel>/totalBookingsCount}"> <mc:data> <mc:ComparisonMicroChartData title="{i18n>bookingStatusNew}" value="{passengerBookingsModel>/newBookingsCount}" color="sapUiChartPaletteSemanticCritical" /> <mc:ComparisonMicroChartData title="{i18n>bookingStatusAccepted}" value="{passengerBookingsModel>/acceptedBookingsCount}" color="sapUiChartPaletteSemanticGood" /> <mc:ComparisonMicroChartData title="{i18n>bookingStatusCancelled}" value="{passengerBookingsModel>/cancelledBookingsCount}" color="sapUiChartPaletteSemanticBad" /> </mc:data> </mc:ComparisonMicroChart> </VBox> </core:FragmentDefinition>

```

You have added asap.m.VBox. It is the container for sap.suite.ui.microchart.ComparisonMicroChart. For more information, check the [API reference](https://sapui5.hana.ondemand.com/sdk/#/api/sap.m.VBox).
    3. You have bound the micro chart data to the corresponding properties of theJSONModel. You have also added the three label texts for the micro chart. For more information, check the [API reference](https://sapui5.hana.ondemand.com/#/api/sap.suite.ui.microchart.ComparisonMicroChart).
    4. You can see errors for the micro chart and its data items saying that IDs are missing. Use a quickfix to generate the necessary IDs.
    5. Finally, add the three label texts to the i18n.properties file:
Code Snippet
Copy codeSwitch to dark mode

```

1

#XTIT: Custom header title bookingStatus=Booking Status #XTIT: Custom micro chart legend bookingStatusNew=New #XTIT: Custom micro chart legend bookingStatusAccepted=Accepted #XTIT: Custom micro chart legend bookingStatusCancelled=Cancelled

```

  5. Check the results.
    1. Switch to the app window.
    2. You can see the newly added Booking Status section with the comparison micro chart in the object page header, next to the _Contact Details_ section.

### Result
In this exercise, you have learned how you can manually add a custom header facet (section) to the object page. You have extended the function import to calculate the number of bookings with different statuses.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-custom-micro-chart-to-object-page-header](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-custom-micro-chart-to-object-page-header).
  * You can find the link to the direct comparison of the branch to the previous one on [Github](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-message-strips..solution/add-custom-micro-chart-to-object-page-header).

### Next Steps
For more information, see:
  * [Extension Points for Object Page Header Facets](https://sapui5.hana.ondemand.com/sdk/#/topic/61cf0ee828824903907464c80dd0d88c.html)
  * [sap.suite.ui.microchart.ComparisonMicroChart](https://sapui5.hana.ondemand.com/#/entity/sap.suite.ui.microchart.ComparisonMicroChart)
