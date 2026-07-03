# Implementing Element Binding

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/implementing-element-binding_a35e50ad-f826-4981-990b-39a4a5064509*

Objective
After completing this lesson, you will be able to implement element binding
## Element Binding
The last of the three binding types to be discussed is element binding.
Element binding plays a role especially in list-detail scenarios. Therefore, a corresponding example will be discussed here.
![Image showing a UI table displaying customer bookings with airline details, linked to JSON model data that includes customer names, cities, airline IDs, flight dates, and booking numbers.](../images/ec14872b54a66eea.png)
In the previous lesson on aggregation binding, the elements of an array named Customers were displayed on a view via a Table UI element. For the element binding, the JSON model data is extended: each customer in the Customers array gets an additional property _Bookings. This property is an array and contains the bookings belonging to the customer (see the figure _Example Scenario_).
Via a second table on the UI, the bookings belonging to a customer are to be displayed, that is, as soon as the user selects an entry in the customer table, the corresponding bookings should appear in the booking table. This behavior is implemented via element binding.
![Diagram showing two data-binding tables, Customer Table and Booking Table, with an event handler function, onCustomerChange, linking customer selection to updating booking details.](../images/886d527fa61ab2ca.png)
The items aggregation of the booking table is bound to the _Bookings property via the items="{_Bookings}" attribute (see the figure _Providing the Binding Context_). Since a relative path is used for the binding, the bookings table cannot display any data yet because the binding context for this relative path is missing.
The missing binding context is provided by the onCustomerChange event handler. This event handler is registered on the selectionChange event of the customer table, that is, the event handler is called every time the user selects a new customer in the customer table. They can do this via a radio button that is displayed on the left side in the customer table (mode="SingleSelectLeft").
In the event handler implementation, the listItem event parameter is queried from the oEvent event object. The parameter provides the column list item for the customer that the user has selected. For this list item belonging to the selected customer, the associated binding context is retrieved via the getBindingContext method.
The requested binding context is set for the booking table, which is accessed in the event handler via its Id. Thus, the relative path _Bookings can now be resolved to an absolute path (/Customers/0/_Bookings or /Customers/1/_Bookings) and the bookings belonging to the selected customer are displayed in the table.
## Use Element Binding
### Business Scenario
In the previous exercise, you created a JSON model and displayed the customer data in it using a table on the Overview view. In this exercise, you create another table on the Overview view to display the flight bookings of a customer. The booking data needed for this is already available in the application via the JSON model created in the last exercise, since each customer object has an array called _Bookings that contains the respective flight bookings. When the user selects a customer in the customer table, the booking table is to display the associated flight bookings. You will use element binding to implement this behavior.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/12_aggregation_binding**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/13_element_binding**  |
### Task 1: Add a Table for the Booking Data from the JSON Model to the Overview View
#### Steps
  1. Open the Overview.view.xml file from the webapp/view folder in the editor.
  2. Insert the following table definition immediately after the </Table> tag of the customer table to display the booking data belonging to a customer:
XML
Copy codeSwitch to dark mode

```

123456789101112131415161718192021222324

<Table id="bookingTable" headerText="Bookings" items="{_Bookings}"
      growing="true" growingThreshold="5" class="sapUiResponsiveMargin" width="auto">
  <columns>
    <Column><header><Text text="Airline ID"/></header></Column>
    <Column><header><Text text="Connection Number"/></header></Column>
    <Column><header><Text text="Flight Date"/></header></Column>
    <Column><header><Text text="Class"/></header></Column>
    <Column><header><Text text="Foreign Currency Payment"/></header></Column>
    <Column><header><Text text="Cancellation Status"/></header></Column>
  </columns>
  <items>
    <ColumnListItem>
      <cells>
        <ObjectIdentifier title="{AirlineID}"/>
        <ObjectIdentifier title="{ConnectionNumber}"/> 
        <ObjectIdentifier title="{FlightDate}"/>
        <Text text="{Class}"/>
        <ObjectNumber number="{ForeignCurrencyPayment}"
              unit="{ForeignCurrency}"/>
        <Text text="{IsCancelled}"/>
      </cells>
    </ColumnListItem>
  </items>
</Table>

```

Note
     * The booking table is bound to the _Bookings property of a customer with its items aggregation. Please note that a relative binding path must be used for this.
     * The used bookingTable Id will be needed later in the view controller to access the table in JavaScript.
     * You can look up the names of the model properties used for binding the table columns in the data.json file from the webapp/model folder.

#### Result
The Overview view should now look like this:
![The Overview.view.xml file, highlighting the Table tag.](../images/57c69eda484760be.png)
### Task 2: Register an Event Handler on the selectionChange Event of the Customer Table
#### Steps
  1. Make sure that the Overview.view.xml file is open in the editor.
  2. Add the attributes mode="SingleSelectLeft" and selectionChange=".onCustomerChange" to the <Table> tag for the customer table.
Note
     * Via mode="SingleSelectLeft" you achieve that only one customer in the table can be selected via a left-positioned selector.
     * Via selectionChange=".onCustomerChange" you register a method - which still has to be implemented - for the event that the user changes the selected customer in the table.

#### Result
The implementation of the customer table should now look like this:
![The Overview.view.xml file, highlighting the mode attribute.](../images/3e5385e08dc6b15e.png)
### Task 3: Implement the Registered Event Handler in the Overview View Controller
#### Steps
  1. Open the Overview.controller.js file from the webapp/controller folder in the editor.
  2. Add the onCustomerChange event handler method, registered above for the selectionChange event of the customer table, to the view controller. Implement this method as follows to set the binding context for the booking table:
JavaScript
Copy codeSwitch to dark mode

```

1234

onCustomerChange: function (oEvent) {
  var oBindingContext = oEvent.getParameter("listItem").getBindingContext();
  this.byId("bookingTable").setBindingContext(oBindingContext);
}

```

#### Result
The view controller should now look like this:![The Overview.controller.js file, highlighting the onCustomerChange function.](../images/afc98d570e7b9db0.png)
  3. Test run your application by starting it from the SAP Business Application Studio.
Make sure that when a customer is selected, the associated flight bookings are displayed in the booking table.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the component works as expected.
