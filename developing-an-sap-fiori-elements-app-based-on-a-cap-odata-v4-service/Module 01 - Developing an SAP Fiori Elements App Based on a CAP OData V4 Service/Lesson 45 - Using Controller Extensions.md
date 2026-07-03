# Using Controller Extensions

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/using-controller-extensions_f47e841f-2dd8-4b88-ba5e-39c0eedd983e*

Objective
After completing this lesson, you will be able to apply controller extensions provided by SAP Fiori elements to add your custom JavaScript code.
## Function Imports
The Open Data Protocol (OData) includes the standard CRUD (Create, Read, Update and Delete) operations that map to the HTTP methods POST, GET, PUT/MERGE and DELETE.
In addition, OData supports further service operations (function imports) that can be invoked by the HTTP methods GET or POST for anything that cannot be mapped to the standard CRUD operations. You can implement the additional service operations in your back end.
In this training, you use CAP as your back end and you will create a function import within your CAP data model.
When you add a definition of the function import to your CAP data model, it becomes a part of the service metadata. You will find it in the $metadata document.
![Function import](../images/026bf30e974ee6c1.png)
The screenshot above shows that the function import is added to the service container alongside the entity sets of the service.
In the same $metadata document, you can find the API of the function import.
![Function import API](../images/5388dbae62475025.png)
As soon as the function import is part of $metadata, it can be used on the client side in your SAP Fiori elements application.
## Controller Extensions
SAP Fiori elements for OData V4 provides a collection of controller extensions. They expose methods which you can override. Check a list of available controller extensions at [API reference for controller extensions](https://sapui5.hana.ondemand.com/sdk/#/api/sap.fe.core.controllerextensions).
For example, class [sap.fe.core.controllerextensions.EditFlow](https://sapui5.hana.ondemand.com/#/api/sap.fe.core.controllerextensions.EditFlow%23methods) offers hooks into the edit flow of your SAP Fiori elements application.
In this lesson, you will use the onAfterBinding method of [sap.fe.core.controllerextensions.Routing](https://sapui5.hana.ondemand.com/#/api/sap.fe.core.controllerextensions.Routing) controller extension to call the function import. You will then evaluate its return value and display a message strip (if necessary) at the right point of time, that is, after a page is bound but not yet rendered.
## Add Message Strips to the Object Page of the Display Customers App
In your _Display Customers_ app, you may want to notify the user if there are any bookings with the status _New_. To do this, you will display the corresponding message above the _Own Bookings_ table on the object page.
In the previous exercise, you have already created a custom section and added the _Table_ building block to it. Now, you will add a message strip to the table. You will also see an option to add a message to the whole object page.
### Task Flow
The table displaying the customer's bookings uses paging to restrict the data exchange load: only the first ten lines are loaded. This means you cannot analyze all the bookings on the UI side; this should be done in the back end instead. To do this, you will create a function import in the back end.
You will first add a controller extension to your _Display Customers_ app using the Page Map.
Next, you will extend your CAP service with a new function. It will check the back end for any bookings with the status _New_ for the selected customer.
After that, you will be able to call this function in your front end using the controller extension. If there are any bookings with the status 'new', a message strip will be shown above the table, displaying a warning.
Finally, you will add an information message to the whole object page, in case there are any bookings with the status _New_.
### Prerequisites
You have completed the exercise Create a Table Using the Table Building Block in the Display Customers App in the unit Discovering the Flexibility of the Programming Model for SAP Fiori Elements for OData V4 (lesson: Using Building Blocks). Alternatively, you can check out its solution branch: [solution/add-table-building-block](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-table-building-block).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_5B3D0509B0C6E780:uebung)
### Steps
  1. Add a controller extension to your app.
    1. Open the object page of the _Display Customers_ app and switch to SAP Business Application Studio.
    2. Open the webapp folder and select _Show Page Map >Object Page>Add Controller Extension_.
    3. Add _PassengerOPExtend_ as the controller name.
    4. You have now added a new controller extension.
  2. Extend your CAP service with a new function.
    1. Open schema.cds and paste the following code snippet into the file:
Code Snippet
Copy codeSwitch to dark mode

```

1

type BookingData: { HasNewBookings: Boolean }

```

This adds a new type BookingData in your data model.
    2. Open travel-service.cds and add the following function definition to it:
Code Snippet
Copy codeSwitch to dark mode

```

1

// Function import used in Controller Extension 'PassengerOPExtend.js' to calculate booking data function getBookingDataOfPassenger(CustomerID: String) returns my.BookingData;

```

This adds a new function getBookingDataOfPassenger.
    3. Open travel-service.js and add the following code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

 /** * Function import handler: getBookingDataOfPassenger * @param CustomerID * @returns BookingData */ this.on('getBookingDataOfPassenger', async (req) => { const { CustomerID } = req.data const allCustomerBookings = await SELECT `BookingStatus_code as status`.from (Booking) .where `to_Customer_CustomerID = ${CustomerID}` const bookingData = { HasNewBookings: false } bookingData.HasNewBookings = allCustomerBookings.some((booking) => { return booking.status === 'N'; }) return bookingData });

```

You have added the implementation of the getBookingDataOfPassenger function.
It takes CustomerID as a parameter and checks the data base for bookings with the status _New_ per _Customer_.
  3. Add a function to the controller extension.
    1. Open the controller extension file PassengerOPExtend.controller.js and add the following code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

 sap.ui.define(['sap/ui/core/mvc/ControllerExtension',"sap/ui/core/message/Message","sap/ui/core/MessageType", ], function (ControllerExtension, Message, MessageType) { 'use strict'; return ControllerExtension.extend('sap.fe.cap.customer.ext.controller.PassengerOPExtend', { // this section allows to extend lifecycle hooks or hooks provided by Fiori elements override: { /** * Called when a controller is instantiated and its View controls (if available) are already created. * Can be used to modify the View before it is displayed, to bind event handlers and do other one-time initialization. * @memberOf sap.fe.cap.customer.ext.controller.PassengerOPExtend */ onInit: function () { // you can access the Fiori elements extensionAPI via this.base.getExtensionAPI var oModel = this.base.getExtensionAPI().getModel(); }, routing: { onAfterBinding: async function (oBindingContext) { } } } }); });

```

You have added the onAfterBinding function of the routing object (class sap.fe.core.controllerControllerextensions.Routing).
    2. Add the following code snippet to the onAfterBinding function:
Code Snippet
Copy codeSwitch to dark mode

```

1

 onAfterBinding: async function (oBindingContext) { const oExtensionAPI = this.base.getExtensionAPI(), oModel = oExtensionAPI.getModel(), sFunctionName = "getBookingDataOfPassenger", oFunction = oModel.bindContext(`/${sFunctionName}(...)`), oBookingTableAPI = oExtensionAPI.byId("fe::CustomSubSection::Bookings--OwnBookingsTable"), oWarningMessage = new Message({ type: MessageType.Warning, message: await oExtensionAPI.getModel("i18n").getResourceBundle().getText("bookingsNew") }), oInfoMessage = new Message({ type: MessageType.Info, message: await oExtensionAPI.getModel("i18n").getResourceBundle().getText("bookingsAttention") }); // Request OData function with current CustomerID const oCustomer = await oBindingContext.requestObject(oBindingContext.getPath()); oFunction.setParameter("CustomerID", oCustomer.CustomerID); await oFunction.execute(); const oContext = oFunction.getBoundContext(); if (this.message !== undefined) { oBookingTableAPI.removeMessage(this.message); } if (oContext.getProperty("HasNewBookings")) { this.message = oBookingTableAPI.addMessage(oWarningMessage); oExtensionAPI.showMessages([oInfoMessage]); } }

```

You have added some code to onAfterBinding. With this code, you have accessed the back-end function getBookingDataOfPassenger in the [SAPUI5 OData V4 Model](https://sapui5.hana.ondemand.com/sdk/#/topic/5de13cf4dd1f4a3480f7e2eaaee3f5b8), got the table API of the table building block, and created a warning message.
You have also created a message of type _Info_. If the HasNewBookings parameter of the back-end function is true, the info message is added to the whole object page using the object page controller's extensionAPI.
    3. Open the i18n file in the file explorer and add the following code snippet:
Code Snippet
Copy codeSwitch to dark mode

```

1

#XMSG: Warning message on object page bookingsNew=There are new bookings that have not yet been accepted. #XMSG: Info message on object page bookingsAttention=Some bookings require your attention

```

You have just added the warning and the information message texts to the i18n.properties file.
    4. Switch to the app window. You can see the warning message for Theresia Buccholm's bookings as some of these have the _New_ status. You can also see an info message in the object page header.

### Result
In this exercise you have added two message strips: one to the table building block and one to the whole object page. To achieve that, you have created and implemented a function in the CAP service that checks if there are any bookings with the status _New_ for the given customer. On the front-end side (in the controller extension), you have implemented the function call and added the messages if needed.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-message-strips](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-message-strips).
  * You can find the link to the direct comparison of the branch to the previous one on [Github](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-table-building-block..solution/add-message-strips).
