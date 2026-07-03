# Implementing Navigation in a Full-screen application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/implementing-navigation_c27bc9ec-a109-4008-9d32-bcf795e7a42a*

Objective
After completing this lesson, you will be able to implement views and navigation for a full-screen application.
## Implementing Navigation
After routing configuration, we will now take a look at how to use the router with the configured routes.
### Implementing the Carrier View
The starting point of our full-screen application is the Carrier view.
In this video lets take a look at how to implement this carrier view:
The _sap.m.Page_ holds an aggregation with the name content. The content aggregation is of type, _sap.ui.core.Control_. In the sample shown above, an _sap.m.Table_ control (1) is added to the content aggregation. The table is bound to an entity, _CarrierCollection_. For each entity of the collection, an object of type _ColumnListItem_ (2) is created and added to the table.
### Implementing the Flights Detail View
The Flights view displays master data for a flight sap.m.ObjectHeader control. The data comes from a relative data binding that is set on the view level as we have seen in the controller before.
![The code in the Flights view to display the back navigation button](../images/ef96bab917b71275.png)
The Flights view implementation shows the details of the selected carrier and the list of flights for the selected carrier in a table. To provide the functionality for navigating back to the carrier view, we add the property _showNavButton_ with the value, true, to the page object.
To handle the back navigation, we assign an event handler for the _navButtonPress_ event (1). The event handler is implemented inside the flights controller.
### Implementation of the Back Button on the Flights Page
To enable the back navigation from the Flights view to the Carrier view, we have to add a corresponding event handler.
![The implementation in the Flights view controller of the onNavBack function](../images/fdd85e8a1c8a154f.png)
  1. Implement a function that returns the router instance for your component. It is also possible to use this.getOwnerComponent().getRouter().
  2. Implement the event handler function **onNavBack**.
This functions checks if there is a previous hash value in the app history, if so, redirect to the previous hash via the browser’s native History API. If not, use the Router to navigate to the route overview which is the carriers overview view.
The function **navTo** of the router is invoked using the name of the route and a boolean parameter indicating if a browser history entry should be created.
     * **true** : the hash is replaced (no browser history entry)
     * **false** : the hash is set (browser history entry)

### Display the NotFound Page for Invalid Carrier ID
As introduced in previous lessons, we have to make sure that the application is able to handle invalid hashes. To react to invalid hashes, we have to extend the element binding in the Flights.controller.js.
![The implementation of the binding change](../images/17c2a13d39481ebf.png)
  1. To react on the change event of the binding operation you can attach an event handler. You can display targets manually without referencing them in a navigation route. Good examples for this are temporary errors, switching to an edit page for a business object, or going to a "Settings" page.
  2. Inside the _onBindingChange() handler we get a reference to the Targets helper object of the router and simply call display("notFound").
The view associated to the target with the name notFound from the routing configuration will be displayed by the router without changing the hash.
The sap.m.routing.Targets object is retrieved by calling getTargets() on the router. However, you could also get a reference to the sap.m.routing.Targets object by calling this.getOwnerComponent().getRouter().getTargets() or this.getOwnerComponent().getTargets().

## Implementing Navigation in a Full-screen application
### Business Example
In the following exercise, you will learn how to implement navigation in a Full-screen Application with SAPUI5.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You should have completed the first exercise of this unit to import the full screen application.
### Task 1: Add a Control for Navigation
We now want to react to the selection of a carrier from the carriers table. Therefore, implement an event handler for the press event of the ColumnListItem element. Name the function onPress. Read the property Carridfrom the selected item. Furthermore, set the type attribute of the ColumnListItem element to Navigation. In this task, we will adjust the Carrier.view.xml file.
#### Steps
  1. Open the Carrier.view.xml file and assign an event handler function with the name onPress to the press event of the ColumnListItem element.
    1. Add the press attribute to the ColumnListItem :
Code Snippet
Copy codeSwitch to dark mode

```

1

press="onPress"

```

  2. Add the attribute type to the ColumnListItem element and assign the value Navigation to the attribute. Then save your changes.
    1. Add the type attribute to the ColumnListItem:
Code Snippet
Copy codeSwitch to dark mode

```

1

type="Navigation"

```

    2. Save your changes. You now should have the following code:
![Screenshot of the resulting ColumnListItem code.](../images/0f0b741f976fa637.png)

### Task 2: Implement the Carrier View Behavior for Navigation
In the following task, you must implement the onPress function in the Carrier view controller. The onPress function reads the property Carrid from the event initiator. After reading the property, the route flights will be invoked and the id of the airline/carrier is passed as argument to the route.
#### Steps
  1. Open the Carrier.controller.js file and remove the onInit function.
    1. Open the Carrier.controller.js file.
    2. Remove the onInit function.
![Screenshot of the Carrier View XML file after removing the onInit function.](../images/f8b752eff0c36ebc.png)
  2. Implement a function getRouter in the view controller of the carrier view. The function should return the reference to the router object of the component.
    1. Use the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1234

getRouter: function () {
    return sap.ui.core.UIComponent.getRouterFor(this);
}

```

  3. Add an event handler function with the name onPress to the controller implementation of the carrier view controller. The function takes one argument with the name oEvent.
    1. Add a function with the name onPress. The function should take one argument called oEvent. Use the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123

 onPress: function(oEvent) {

}

```

  4. Read the property Carrid from the binding context of the event initiator and store the value in a local variable, sCarrid.
    1. Declare a variable with the name oItem and assign the event-source object to the variable.
    2. Declare a variable with the name oCtx and assign the binding context from the event source object to the variable.
    3. Declare a variable sCarrid. Read the value of the property Carrid from the oCtx-Object using the function getProperty and assign the result to the variable sCarrid.
    4. Your implementation inside the onPress function should look like the following:
Code Snippet
Copy codeSwitch to dark mode

```

1234

var oItem = oEvent.getSource();
var oCtx = oItem.getBindingContext();
var sCarrid = oCtx.getProperty("Carrid");

```

  5. Navigate to the Flights view using the route flights. Pass the value of sCarrid to the route as an argument using the property carrierId. Use the navTo function of the router for triggering the navigation.
    1. Use the following code after the variables definition :
Code Snippet
Copy codeSwitch to dark mode

```

1234

this.getRouter().navTo("flights", {
  carrid: sCarrid
}, false);

```

    2. Your controller implementation should look like the following:
    3. Save your changes. You now should have the following code:
![Screenshot of the Carrier View XML code after adding both functions.](../images/2d419f443a5cdacd.png)

### Task 3: Implement the Flights View Behavior for Navigation
#### Steps
  1. Implement a function getRouter in the view controller of the flights view. The function should return the reference to the router object of the component.
    1. Open the Flights.controller.js file.
    2. Add a getRouter function using the following code (don't forget to add a coma after the onInit function):
Code Snippet
Copy codeSwitch to dark mode

```

1234

getRouter: function () {
return sap.ui.core.UIComponent.getRouterFor(this);
}

```

  2. Implement the onInit function of the Flights controller. Register a function _onObjectMatched for the route flights. The function will be implemented in one of the next steps.
    1. Locate the onInit function.
    2. Create a variable with the name oRouterand assign a reference to router. Use the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

var oRouter = this.getRouter();

```

    3. Register the function _onObjectMatched when the route flights is matched. Enter the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

oRouter.getRoute("flights").attachMatched(this._onObjectMatched, this);

```

    4. You now should have the following code:
![Screenshot of the resulting onInit function code.](../images/582ff4a1e86a1062.png)
  3. Implement the function _onObjectMatched. The function should read the property carrierId from the event parameter arguments and bind the view to the selected carrier. Register the _onBindingChange function for the change event. Then register anonymous event handler functions for the events dataRequestedand dataReceived. When the event dataRequested occurs, the view should be set into the busy mode, and when dataReceivedoccurs, the busy mode should be set to false. In this step, create a function _onObjectMatched with one invocation parameter called oEvent. Then retrieve the parameter with the name arguments from the event object, read the property Carrid and store the value in a local variable _sCarrierId. In addition, get the view and assign it to the local variable oView.
    1. Create a function _onObjectMatched with one invocation parameter called oEvent. Add the following code after the getRouter function (don't forget to add a coma) :
Code Snippet
Copy codeSwitch to dark mode

```

123

_onObjectMatched: function (oEvent) {

}

```

    2. Retrieve the parameter with the name arguments from the event object. Assign it to a variable called oArgs. Add the following code to the function:
Code Snippet
Copy codeSwitch to dark mode

```

1

var oArgs = oEvent.getParameter("arguments");

```

    3. Read the property carrierId from the oArgs object and assign the result to a member variable called _sCarrierId. Add the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

this._sCarrierId = oArgs.carrid;

```

    4. Get a reference to the view object and assign the reference to a local variable called oView. Add the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

var oView = this.getView();

```

  4. Call the function bindElement on the view object. Pass a literal object to the function.
    1. Enter the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123

oView.bindElement({

});

```

  5. Add the property path to the literal object and assign the binding to the selected Carrier using the _sCarrierId variable.
    1. Add the following code to the bindElement function:
Code Snippet
Copy codeSwitch to dark mode

```

1

path: "/UX_C_Carrier_TP('" + this._sCarrierId + "')",

```

  6. Add a property events to the literal object. Assign another literal object to the property.
    1. Add the following code after the path property specification:
Code Snippet
Copy codeSwitch to dark mode

```

123

events: {

}

```

  7. Call the _onBindingChange function for the event change. The function will be implemented in a later step.
    1. Add the following code to the events definition:
Code Snippet
Copy codeSwitch to dark mode

```

1

change: this._onBindingChange.bind(this),

```

  8. Add a function for the event dataRequested and implement the function in a way that the view is set to busy.
    1. Add the following code after the change event specification:
Code Snippet
Copy codeSwitch to dark mode

```

1234

dataRequested: function () {
  oView.setBusy(true);
},

```

  9. Add a function for the event dataReceived and implement the function in a way that the view is set to not busy.
    1. Add the following code after the dataRequested event specification:
Code Snippet
Copy codeSwitch to dark mode

```

1234

dataReceived: function () {
  oView.setBusy(false);
}

```

    2. You now should have the following code:
![Screenshot of the resulting _onObjectMatched function code.](../images/468252efd162c804.png)
  10. Add a function _onBindingChange to the controllers implementation. Get the element binding from the view. If the element binding has no bound context, the NotFound view should be displayed. Get a reference to the target's helper object of the router and call display("notFound").
    1. Enter the following code after the _onObjectMatched function implementation:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011

_onBindingChange: function () {
  var oElementBinding;

  oElementBinding = this.getView().getElementBinding();

  // No data for the binding
  if (oElementBinding && !oElementBinding.getBoundContext()) {
    this.getRouter().getTargets().display("notFound");
  }
},

```

  11. Add a function onNavBack to the controllers implementation. If the previous hash is undefined, use the navTo function of the router with the overview route. Then save your changes.
    1. Add the following code after the _onBindingChange function implementation:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213

onNavBack: function () {
  var oHistory, sPreviousHash;

  oHistory = sap.ui.core.routing.History.getInstance();
  sPreviousHash = oHistory.getPreviousHash();

  if (sPreviousHash !== undefined) {
    window.history.go(-1);
  } else {
    this.getRouter().navTo("overview", true /*no history*/);
  }
}

```

    2. Save all of your changes.

### Task 4: Test your Application
Be aware that since we are not testing the application in a real SAP Fiori environment you will get errors in the console if you use Dev Tools to debug your application. Please, dismiss any message about resource preload.
#### Steps
  1. Test your application. Choose a carrier to see the corresponding flights. The Flights view should be displayed.
![Resulting applkication screen. Carrier information is displayed in the header and a list of Flights with four columns is displayed in the content.](../images/00d178055c7e45b9.png)
    1. Perform this step in the way it was shown in a previous exercise.
  2. Try to navigate to a URL for which no route exists. The NotFound view should be displayed.
![Not found view screenshot.](../images/78616ce5ccaa099a.png)
    1. In the URL field of your browser, exchange the carrier id at the end with something that does not exist (like XX for example) and press Enter (on your keyboard).
    2. The Not Found view should display.
