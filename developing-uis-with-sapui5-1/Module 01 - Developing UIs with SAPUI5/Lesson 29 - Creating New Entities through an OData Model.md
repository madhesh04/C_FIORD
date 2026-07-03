# Creating New Entities through an OData Model

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/creating-new-entities-through-an-odata-model_aba01a3c-b613-4526-b4fa-c72a05596e2a*

Objective
After completing this lesson, you will be able to create new entities for an OData service via an SAPUI5 OData model
## Batch Control
### Group IDs
The OData V4 model sends requests in the following cases:
  * Implicit read requests to retrieve data for a binding
For example, a list binding with the absolute path /UX_Customer triggers a GET UX_Customer to read data.
  * Implicit update requests via two-way binding
For example, update a customer’s name through a property binding with the relative path CustomerName, which has a context with path /UX_Customer(00505604-4e85-1edd-818f-21e64b9cd2cf) triggering PATCH UX_Customer(00505604-4e85-1edd-818f-21e64b9cd2cf) with the customer name's value as JSON payload.
  * Explicit requests triggered through API calls like ODataListBinding.refresh() or ODataContextBinding.execute()

For each of these cases, it is possible to specify a _Group ID_ of type string that allows you to group multiple operations into a single HTTP request payload (batch request).
![OData batch requests use Group IDs: `$auto` for auto-batched, `$direct` for direct, and developer-defined Application Group IDs for custom batching.](../images/58775ab112573465.png)
A _Group ID_ has one of the following submit modes to control the use of batch requests:
  * **sap.ui.model.odata.v4.SubmitMode.API**
Requests associated with this submit mode are sent in a batch request via sap.ui.model.odata.v4.ODataModel#submitBatch().
  * **sap.ui.model.odata.v4.SubmitMode.Auto**
Requests associated with this submit mode are sent in a batch request which is triggered automatically before rendering.
  * **sap.ui.model.odata.v4.SubmitMode.Direct**
Requests associated with this submit mode are sent directly without batch.

The following _Group IDs_ are possible:
  * $auto and $auto.*
Predefined batch _Group ID_ , which is the default if no _Group ID_ is specified. You can use different $auto.*_Group IDs_ to use different batch requests. The suffix can be any non-empty string consisting of alphanumeric characters from the basic Latin alphabet, including the underscore. They have the submit mode **sap.ui.model.odata.v4.SubmitMode.Auto**.
  * $direct
Predefined batch _Group ID_ , which has the submit mode **sap.ui.model.odata.v4.SubmitMode.Direct**.
  * Application Group IDs
An Application Group ID is a non-empty string consisting of alphanumeric characters from the basic Latin alphabet, including the underscore. By default, an Application Group ID has the submit mode **sap.ui.model.odata.v4.SubmitMode.API**.
On construction of the OData model, it is possible to define different submit modes for Application Group IDs. This is useful when you want to separate requests requiring short processing time on the server from those requiring long processing time, so that responses to "fast" requests are visible earlier on the UI.

### Usage of Group IDs in XML Views
![To specify a Group ID for implicit requests, use the following parameters for the binding: $$groupId – Group ID for read requests; $$updateGroupId – Group ID for update requests](../images/c8a7b308bab31299.png)
In the example shown in the figure, _Usage of Group IDs in XML Views_ , the binding context of the form is set to /UX_Customer(00505604-4e85-1edd-818f-21e64b9cd2cf) via the binding attribute of the <SimpleForm> tag. In addition, the _Group ID_ for read and update requests is set to $direct ($$updateGroupId and $$groupId parameters). Therefore, the data for the form, that is, name and city of the customer with Id 00505604-4e85-1edd-818f-21e64b9cd2cf, is read directly without batch. Likewise, updates for the name and the city through two-way binding are sent directly without batch.
The default for the _Group ID_ of the OData model is $auto. The value of _Group ID_ is used as default for the _Update Group ID_ of the OData model.
On instantiation of the OData model, you can also provide both a _Group ID_ and an _Update Group ID_ ; if specified, these values are used as defaults if the corresponding binding parameters are not explicitly set.
For explicit requests, the _Group ID_ can be specified as an optional parameter to the corresponding API method. The _Group ID_ or _Update Group ID_ of the binding is used as a default.
## Creating an Entity
In the example shown in the figure, _Creating an Entity - Example_ , a new customer is created when the _Create Customer_ button on the UI is pressed.
![sap.ui.model.odata.v4.ODataListBinding#create creates a new entity. For creating the new entity, the binding’s Update Group ID is used. sap.ui.model.odata.v4.Context#created returns a Promise that is resolved when the entity has been created in the back-end.](../images/ee9322de1bc7ea94.png)
The sample application uses a table with Id customerTable on the UI, via whose items aggregation the customer entity set is displayed. For this entity set, a new entity is to be created.
The getBinding method is used in the event handler of the _Create Customer_ button to query the binding object for the items aggregation of the UI table. This binding object is of type sap.ui.model.odata.v4.ODataListBinding. The create method of this list binding creates a new customer entity and inserts it at the beginning of the list. The method is passed the data for the entity to be created. The customer data is not shown in the coding example. For example, it can come from a form that the user has filled in.
For creating a new entity, the _Update Group ID_ of the list binding is used. In the example, neither the $$groupId parameter nor the $$updateGroupId parameter is explicitly set for the list binding, so by default the $auto _Update Group ID_ is used for the create operation. That is, the customer is created in the back-end via a corresponding batch request, which is automatically triggered before rendering.
The create method returns the context object for the newly created entity. It is of type sap.ui.model.odata.v4.Context. The created method of this context object returns a promise that is resolved without data when the entity represented by the context has been created in the back-end. The function registered for this case can be used, for example, to display a success message.
## Implement an OData Create Operation
### Business Scenario
When pressing the _Create Customer_ button on the Overview view, a popup currently displays with the info text that the customer will be created later via an OData service. In this exercise, you will implement this create operation. To do this, you will first delete the implementation of the popup and the info text used there. Then you will reimplement the event handler method for the _Create Customer_ button so that a new customer is created via the OData service already integrated in the application.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/20_OData_model_(read)**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/21_OData_model_(create)**  |
### Task 1: Delete the Implementation of the Popup as well as the Used Info Text
#### Steps
  1. The implementation of the popup can be found in the Dialog.fragment.xml file. Delete this file from the webapp/view folder.
    1. Open the context menu for the Dialog.fragment.xml file in the project tree.
    2. Choose _Delete Permanently_.
    3. Confirm in the dialog by choosing _Delete_.
  2. Open the i18n.properties resource bundle file from the i18n folder in the editor.
  3. Delete the following key-value pair from the file, which is now no longer needed:
JSON
Copy codeSwitch to dark mode

```

12

# Fragment
dialogText=Customer {0} is later saved via an OData service.

```

### Task 2: Create a New Customer via the OData Service when the Button is Pressed
#### Steps
  1. In the next steps, you will implement the creation of a new customer via the OData service. In doing so, a corresponding translatable message will be displayed on the UI in case of success. For this purpose, create the following key-value pair in the i18n.properties resource bundle file:
JSON
Copy codeSwitch to dark mode

```

1

customerCreatedMessage=Customer successfully created

```

#### Result
The i18n.properties resource bundle file should now look like this:![Screenshot of the i18n.properties file.](../images/43564a31ae99956a.png)
  2. Now open the Overview.controller.js file from the webapp/controller folder in the editor.
  3. The success message created above is to be displayed via a message toast on the UI. For this purpose, add the sap/m/MessageToast module to the dependency array of the view controller and a corresponding parameter named MessageToast to the factory function.
#### Result
The view controller should now look like this:![The Overview.controller.js file highlighting the sap/m/MessageToast attribute.](../images/0d729777f08f2de9.png)
  4. Replace the current implementation of the onSave event handler method with the following coding:
JavaScript
Copy codeSwitch to dark mode

```

123456789101112131415161718

var oModelData = this.getView().getModel("customer").getData();
var oResourceBundle = this.getView().getModel("i18n").getResourceBundle();

if (oModelData.Discount === undefined) { oModelData.Discount = 0; }

this.byId("customerTable").getBinding("items").create({
  "Form": oModelData.Form,
  "CustomerName": oModelData.CustomerName,
  "Discount": oModelData.Discount + "",
  "Street": oModelData.Street,
  "PostCode": oModelData.PostCode,
  "City": oModelData.City,
  "Country": oModelData.Country,
  "Email": oModelData.Email,
  "Telephone": oModelData.Telephone
}).created().then(function () {
  MessageToast.show(oResourceBundle.getText("customerCreatedMessage"));
});

```

Note
The coding creates a new customer entity with the data entered in the form. After the creation is finished, the success message from the resource bundle is displayed as a message toast.
#### Result
The onSave event handler method should now look like this:![The Overview.controller.js file highlighting the onSave function.](../images/a77a3c94690bc735.png)
  5. Test run your application by starting it from the SAP Business Application Studio.
Caution
As in the previous exercise, the OData service is not called in the back-end system for testing. Instead, access to the remote system is simulated via a mock server. To do this, use the npm script called **start-mock** to start the application instead of the _start-noflp_ script used previously.
Make sure that when you press the _Create Customer_ button, a new customer is created with the data entered in the form. The success message should appear as a message toast and the customer should be automatically added to the customer table.
Note
Be aware that the customer data is not really persisted via the mock server. That is, if you restart the application, all newly created customers will be lost. (Be also aware that, if you are connected to a back-end system, the data will be persisted in the system.)
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-mock_ in the dialog that appears.
    3. In the opened application, check if the component works as expected.

[Continue to quiz](https://learning.sap.com/courses/developing-uis-with-sapui5-1/odata-model)
