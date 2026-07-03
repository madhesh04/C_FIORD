# Implementing View Synchronization

*Source: https://learning.sap.com/courses/advanced-sapui5-development/implementing-view-synchronization_f59c0f24-7102-4743-8c76-8b0d5c83023b*

Objective
After completing this lesson, you will be able to implement synchronization functionality between list and detail view.
## Implementing Navigation
### Implementing Navigation
The basic navigation principals are also used when you implement an application using the sap.f.FlexibleColumnLayout - for example, using the router object or registering the event handler for attachMatched. The difference is that we have to extend it with the sap.f.FlexibleColumnLayoutcontrols.
![The _onObjectMatched function in the Detail View controller](../images/5081d8f8a4305904.png)
The figure shows the difference to the already known navigation handling inside the controller of the navigation target. As you can see in the implementation, the model with id mainView is fetched from the component. In the same line of code, the layout is set to TwoColumnsMidExpanded. This will show the second column of the sap.f.FlexibleColumnLayout to the user.
## Synchronizing the List and the Detail Views
The end user will usually select an item on the list to display the details. If so, everything works as expected. The navigation is triggered, the details of the selected item are displayed in the detail view, and the selected item is marked as selected in the list. But what happens if the user changes the hash directly in the address bar of the browser?
Obviously, if the hash is valid, the details are displayed but the item in the list will not be marked as selected. Furthermore, if the hash is invalid, the NotFound view is displayed but a previously selected item is still marked as selected. To make this happen, we have to implement a synchronization functionality between the detail and the list view.
In this video we will take a look at how to implement a synchronization functionality.
Settings
## Provide view synchronisation for the List-Detail application
### Business Example
In this exercise, you implement the List and Detail view synchronization.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You need to have completed the previous exercise to build the Detail View.
### Task 1: Provide View Synchronization Functionality
In this task, you implement view synchronization by creating a class with the name **ListSelector**. The ListSelector implementation should be placed in the controller folder of your project. The ListSelector.js file is provided in the course templates folder.
#### Steps
  1. Upload the ListSelector.js file into your project.
    1. Open the context menu of the _controller_ folder and choose _Upload_.
    2. Select the ListSelector.js file from your Templates folder.
  2. Observe the content of the ListSelector.js file and answer the following questions.
From which object is the ListSelector class derived ?
The master List controller, on initialization, will call the setBoundMasterList function. What does it do ?
The master List controller then will wait for the _oWhenListLoadingIsDone_ promise to be fulfilled before displaying the first carrier detail view. Why ?
What does the SelectAListItem function do?
    1. Look at the ListSelector.js file.
the ListSelector class is derived from the BaseObject class.
the setBoundMasterList function sets the _oList variable to the carrier list and resolves the _oWhenListHasBeenSet promise.
The function called when the __oWhenListHasBeenSet_ promise has been fulfilled waits for the **dataReceived** event to be triggered on the binding object and then, if there are some data, sets the list and oFirstListItem parameters of the resolve function. The master list controller will then be able to display the first element detail view.
  3. To make sure that the ListSelector can be referenced from each part of the application, we must create an instance of the ListSelector at a more global level. Therefore, create an instance of the ListSelector inside the Component.js file and make sure that the instance is a member variable of the component. Then save your changes.
    1. Open the Component.js file located in the _controller_ folder of your project.
    2. Add a reference to the ListSelector in the Component.js file as follows:
Code Snippet
Copy codeSwitch to dark mode

```

12345678

sap.ui.define([
        "sap/ui/core/UIComponent",
        "sap/ui/Device",
        "student/com/sap/training/advancedsapui5/listdetail/model/models",
        "student/com/sap/training/advancedsapui5/listdetail/controller/ListSelector"
    ],
    function (UIComponent, Device, models, ListSelector) {

```

    3. In the init function of the Component, declare a member variable named oListSelector and assign an ListSelector instance to the variable. Then save your changes.
Code Snippet
Copy codeSwitch to dark mode

```

123

// instantiation of the listselector
this.oListSelector = new ListSelector();

```

    4. Your init function should now look like this:
![Screen shot of the component init function.](../images/f0351ffcfc2ba760.png)

### Task 2: Implement the Base Controller
In this task, you implement a base controller class .This class provides to all controllers some functionalities for reuse (for routing, view synchronization, and backward navigation).
#### Steps
  1. Upload the BaseController.js file into your project.
    1. Open the context menu of the _controller_ folder and choose _Upload_.
    2. Select the BaseController.js file from your Templates folder.
  2. Look at the getListSelector function. It returns the reference of the oListSelector object from the component.

### Task 3: Implement the List Controller
In this task, you implement the controller of the List view for navigation.
#### Steps
  1. Open the Carrier.controller.js file. Define that the controller should be derived from the BaseController. Remove the two functions used for full screen navigation.
    1. Open the Carrier.controller.js file located in the controller folder of your project.
    2. Update the code as follows:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011

sap.ui.define([
    "student/com/sap/training/advancedsapui5/listdetail/controller/BaseController"
],
    function (Controller) {
        "use strict";

        return Controller.extend("student.com.sap.training.advancedsapui5.listdetail.controller.Carrier", {

        });
    });

```

  2. Implement a _navigateToCarrierDetails function. The function takes two arguments. Name the first argument sCarrierId and the second bReplace. The function should navigate to the carrierdetails route and pass a sCarrierId value as a parameter.
    1. Add the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123456

_navigateToCarrierDetails : function(sCarrierId,bReplace) {
  this.getRouter().navTo("flights", {
    carrid: sCarrierId
  }, bReplace);
},

```

  3. Add a _showDetail function. The function takes one argument. Name the argument oItem. This variable will contain during runtime the item selected by the user from the master list. Read the property Carrid from the oItemand store it in a variable sCarrierId. Check also if the app is running on a mobile device or not. Store the result in a local variable bReplace. Invoke the _navigateToCarrierDetails function and pass both variables as an argument.
    1. After the _navigateToCarrierDetails implementation, add the _showDetail function with an oItem argument as follows:
Code Snippet
Copy codeSwitch to dark mode

```

123

_showDetail: function(oItem) {

},

```

    2. Check whether the app is running on a mobile device or on a desktop and store the result in a local variable. Then read the Carrid property from the bindingContext of the oItem object and store it in a variable. Pass both variables to the _navigateToCarrierDetails function. Add the following code into the _showDetail function:
Code Snippet
Copy codeSwitch to dark mode

```

123

var sCarrierId = oItem.getBindingContext().getProperty("Carrid");
this._navigateToCarrierDetails(sCarrierId,true);

```

  4. Implement the event handler for the select event of the list. The assign function to handle the event was called onSelect. Invoke the _showDetail method and pass the selected item to the function. The selection behavior of the table depends on whether the app is running on a mobile device or not.
    1. Add the following code after the _showDetail implementation:
Code Snippet
Copy codeSwitch to dark mode

```

1234

onSelect: function(oEvent) {
  this._showDetail(oEvent.getParameter("listItem") || oEvent.getSource());
},

```

  5. Implement an onBypassed function. This function should handle the case that when the router bypasses the target. Inside the function, invoke the removeSelections function on the list object.
    1. Add the following code after the onSelect implementation:
Code Snippet
Copy codeSwitch to dark mode

```

1234

onBypassed: function() {
  this._oList.removeSelections(true);
},

```

  6. Add an _onListMatched function to the implementation. The function takes no argument. The function will be called when the list route is invoked by the router. React on the case when the promise oWhenListLoadingIsDone is resolved. If the promise is resolved, the details of the first item from the master list should be displayed inside the details view.
    1. Add the following code after the onBypassed implementation :
Code Snippet
Copy codeSwitch to dark mode

```

123456789

_onListMatched: function() {
  this.getListSelector().oWhenListLoadingIsDone.then(
    function(mParams) {
      var sObjectId = mParams.oFirstListItem.getBindingContext().getProperty("Carrid");
      this._navigateToCarrierDetails(sObjectId,true);
    }.bind(this)
  );
}

```

  7. Implement the onInit function. Get a reference to the master list of your view and store the reference in a variable named oList. Assign the reference to oList to a member variable named _oList. Add a eventhandler for onBeforeFirstShow of the view using addEventDelegate-function and invoke the setBoundMasterList of the ListSelector and pass the reference to the oList object to the function. Implement a behavior when the masterlist route is invoked by the router. If this is the case, the _onListMatched function should be invoked. Implement a behavior when the router bypasses the list route, register the onBypassed function when this event occurs. Then save your changes.
    1. Add the following code at the beginning:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

 onInit: function () {
                var oList = this.byId("list");
                this._oList = oList;
                this.getView().addEventDelegate({
                    onBeforeFirstShow: function () {
                        this.getOwnerComponent().oListSelector.setBoundMasterList(this._oList);
                    }.bind(this)
                });
                this.getRouter().getRoute("Overview").attachPatternMatched(this._onListMatched, this);
                this.getRouter().attachBypassed(this.onBypassed, this);
            },

```

    2. Save your changes.

### Task 4: Implement the Detail Controller
In this task, you implement the controller of the Detail view for navigation.
#### Steps
  1. Open the Flights.controller.js file. Define that the controller should be derived from the BaseController. You can now remove the getrouter and onNavBack functions since we're using those of the Base Controller.
    1. Open the Flights.controller.js file located in the _controller_ folder of your project.
    2. Update the code as follows:
Code Snippet
Copy codeSwitch to dark mode

```

12345

sap.ui.define([
  "student/com/sap/training/advancedsapui5/listdetail/controller/BaseController"
],
  function (Controller) {

```

    3. Remove the getrouter function.
    4. Remove the onNavBack function.
  2. Modify the _onBindingChange function. If the view Is not bound to an entity, the selection on the master list should be cleared. To clear the selection, call the function clearListSelection on the ListSelector. If the view is bound to an entity, get the binding path of the entity and invoke the selectAListItem function from the ListSelector. Pass the binding path as an argument.
    1. Your code should look like the following:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

_onBindingChange: function() {
  var oView = this.getView();
  var oElementBinding = oView.getElementBinding();
  if (!oElementBinding.getBoundContext()) {
    this.getRouter().getTargets().display("notFound");
    this.getOwnerComponent().oListSelector.clearMasterListSelection();
    return;
  }
  var sPath = oElementBinding.getPath();
  this.getOwnerComponent().oListSelector.selectAListItem(sPath);
}

```

  3. Modify the function named _onObjectMatched. Change the layout attribute of the mainView Model to TwoColumnsMidExpanded to adjust the layout behavior of your sap.f.flexibleColumnLayout. Remove the dataRequested and dataReceived events from the bindElement call. The Busy property of the view will have to be managed differently because the OData service will not be called each time the selection changes.
    1. Your code should now look like the following::
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415

  _onObjectMatched: function (oEvent) {
        var oArgs = oEvent.getParameter("arguments");
        this._sCarrierId = oArgs.carrid;
        var oView = this.getView();

        oView.getModel("mainView").setProperty("/layout", "TwoColumnsMidExpanded");

        oView.bindElement({
          path: "/UX_C_Carrier_TP('" + this._sCarrierId + "')",
          events: {
            change: this._onBindingChange.bind(this)
          }
        });
      },

```

  4. Modify the onInit function. Get the OData Model reference to attach the RequestSent and RequestCompleted events and set the Busy property of the view.
    1. Update the code of the onInit function as follows:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213

onInit: function () {
        var oRouter = this.getRouter();
        oRouter.getRoute("flights").attachMatched(this._onObjectMatched, this);

        var oModel = this.getOwnerComponent().getModel();
        oModel.attachRequestSent(function (oEvent) {
          this.getView().setBusy(true);
        }, this);
        oModel.attachRequestCompleted(function (oEvent) {
          this.getView().setBusy(false);
        }, this);
      },

```

    2. Save your changes.

### Task 5: Test your Application
#### Steps
  1. Test your application. Choose a carrier to see the corresponding connections.
![Resulting application screen. A list of carriers is displayed on the left and the connections of the selected carrier are displayed on the right.](../images/003cb105d718b16e.png)
    1. Perform this step as shown in a previous exercise.
  2. Try to navigate to a hash for which no route exists. The NotFound view should be displayed.
![Resulting application screen. The right details pane shows the resource not found page.](../images/0cbd533fbf36b024.png)
    1. Change the URL in your browser to something not corresponding to a route, for example **Carrier/AA** instead of **Carriers/AA**.
