# Creating App-Specific Actions

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/creating-app-specific-actions_af7b882c-aca4-4c12-9cbf-02e568901501*

Objective
After completing this lesson, you will be able to create actions with parameters.
## App-Specific Actions
In SAP Fiori elements, you can use generic actions such as _Delete_ and _Create_. If your app needs actions beyond this scope, you can create your own application-specific actions.
App-specific actions can be either annotation-based actions or custom actions.
### Annotation-Based Actions
Annotation-based actions are created using corresponding annotations. They can be used in the following cases:
  * User confirmation is required, for example for critical actions. A popover dialog opens, and the user has to confirm the action. For more information, see [Adding Confirmation Popovers for Actions](https://sapui5.hana.ondemand.com/sdk/#/topic/87130de10c8a44269c605b0322df6b1a.html).
  * Additional user input is required. Some values may already be filled in.
  * The action triggers a back-end call through an OData service, such as _Approve_.
  * The action triggers navigation, for example to a different app. For more information, see [Configuring Navigation.](https://sapui5.hana.ondemand.com/sdk/#/topic/a42427550b72436a8bdf53045b06effb)

### Custom Actions
Custom actions can be created if the action you need cannot be covered by annotation-based actions. They are created using extension points which need to be registered in the manifest.json file. For more information, see [Adding Custom Actions Using Extension Points](https://sapui5.hana.ondemand.com/sdk/#/topic/7619517a92414e27b71f02094bd08d06.html).
### Visibility of Annotation-Based Actions
You can change the visibility of annotation-based actions with the @Core.OperationAvailable annotation.
The annotation can either have a static value (Boolean true or false) or a dynamic value (a path pointing to a property). If the value is static and set to true, the action will always be available, regardless of which item is selected. If the value is dynamic, the action can be enabled or disabled dynamically, depending on a certain condition.
Have a look at the following CAP CDS annotation:
Code Snippet
Copy codeSwitch to dark mode

```

12345

actions {
   deductDiscount @(
    Core.OperationAvailable : { $edmJson: { $Eq: [{ $Path: 'in/TravelStatus_code'}, 'O']}}
  );
}

```

In this example, the action deductDiscount will only be available for items with the TravelStatus'O' (open). The value for the annotation Core.OperationAvailable is a dynamic expression enclosed in { $edmJson: { … }}.
For more information about dynamic expressions in OData Version 4, see [OData Common Schema Definition Language (CSDL) JSON Representation Version 4.01 (oasis-open.org)](http://docs.oasis-open.org/odata/odata-csdl-json/v4.01/odata-csdl-json-v4.01.html#_Toc38466479).
The CDS compiler translates the expression into the corresponding XML code. The annotation above is translated to the following OData representation:
Code Snippet
Copy codeSwitch to dark mode

```

12345678

<Annotations Target="TravelService.deductDiscount(TravelService.Travel)">
	<Annotation Term="Core.OperationAvailable">
	  <Eq>
	    <Path>in/TravelStatus_code</Path>
	      <String>O</String>
	  </Eq>
	</Annotation>
</Annotations>

```

For more information about CAP CDS and dynamic expressions, see: [Dynamic Expressions](https://cap.cloud.sap/docs/advanced/odata#dynamic-expressions).
## Create an Application-Specific Action with a Mandatory Parameter
In addition to generic actions common to all SAP Fiori elements apps, you can also create app-specific actions.
In this exercise, you will create an annotation-based action for the _Travels_ table. It will deduct a discount from both the booking fee and the total price. The action will have a mandatory parameter: the discount percentage with the default value of 5. The action will be added to the table toolbar in the list report.
### Task Flow
In this exercise, you will first create the deductDiscount action and implement it. The action will only apply to travels with the travel status _Open_. Then, you will use the Page Editor to add the action to the table toolbar in the list report. Finally, you will test the newly created action.
### Prerequisites
You have completed the exercise Make the Delete Action Unavailable for Accepted and Canceled Travels in the unit Examining Actions Available on the List Report (lesson: Applying Generic Actions Provided by SAP Fiori Elements). Alternatively, you can check out its solution branch: [solution/make-delete-action-unavailable-for-accepted-travels](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/make-delete-action-unavailable-for-accepted-travels).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_216A48765613BBB0:uebung)
### Steps
  1. Create the action and implement it.
    1. Open the travel-service.cds file in SAP Business Application Studio.
    2. Add the definition of the new action deductDiscount. Note that it has a mandatory parameter, and its default value is five percent.
Add the following code snippet to the actions section of the travel-service.cds file:
Code Snippet
Copy codeSwitch to dark mode

```

1

action deductDiscount(@(UI.ParameterDefaultValue : 5)percent: Percentage not null @mandatory ) returns Travel;

```

    3. Open the travel-service.js file to implement the action. The action will update both the TotalPrice and BookingFee properties if the _Travel Status_ is not 'A' (Accepted) and the _Booking Fee_ is not null.
Add the following code snippet to the srv/travel-service.js file:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415161718

  this.on ('deductDiscount', async req => {
    let discount = req.data.percent / 100
    let succeeded = await UPDATE (req.subject)
      .where `TravelStatus_code != 'A'`
      .and `BookingFee is not null`
      .with (`
        TotalPrice = round (TotalPrice - BookingFee * ${discount}, 3),
        BookingFee = round (BookingFee - BookingFee * ${discount}, 3)
      `)
    if (!succeeded) { //> let's find out why...
      let travel = await SELECT.one `TravelID as ID, TravelStatus_code as status, BookingFee` .from (req.subject)
      if (!travel) throw req.reject (404, `Travel "${travel.ID}" does not exist; may have been deleted meanwhile.`)
      if (travel.status === 'A') req.reject (400, `Travel "${travel.ID}" has been approved already.`)
      if (travel.BookingFee == null) throw req.reject (404, `No discount possible, as travel "${travel.ID}" does not yet have a booking fee added.`)
    } else {
      return this.read(req.subject)
    }
  })

```

  2. Restrict the availability of the action to travels with the _Open_ travel status.
    1. Open the field-control.cds file and add the @Core.OperationAvailable annotation to the deductDiscount action.
Add the following code snippet to the app/travel_processor/field-control.cds file:
Code Snippet
Copy codeSwitch to dark mode

```

123

deductDiscount @(
    Core.OperationAvailable : { $edmJson: { $Eq: [{ $Path: 'in/TravelStatus_code'}, 'O']}}
  );

```

    2. The action will now only be available if the _Travel Status_ is 'O' (Open).
  3. Open the Page Editor to add the changes.
    1. Go to _List Report_ > _Toolbar_ and add the TravelService.deductDiscount action to the table toolbar.
    2. Select the action you've just added. Note that you can change its settings in the pane on the right.
    3. Select the _Label_ annotation to generate a text key in the i18n.properties file.
  4. Return to the app to check your newly created action.
    1. The action _Deduct Discount_ now appears in the table toolbar.
    2. Select a travel with the _Accepted_ travel status. Note that the action is not available.
    3. Now select a travel with the _Open_ travel status. The action is now available and can be applied.
    4. Apply the _Deduct Discount_ action to the selected travel. Both the _Booking Fee_ and _Total Price_ have now been decreased by the specified amount.

### Result
In this lesson, you have added an app-specific action to the table toolbar and restricted the availability of the action for specific items.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/create-action-with-a-mandatory-parameter](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/create-action-with-a-mandatory-parameter).
  * You can find the link to the direct comparison of the branch to the previous one on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/make-delete-action-unavailable-for-accepted-travels..solution/create-action-with-a-mandatory-parameter).

### Next Steps
For more information, see [Actions in the List Report](https://sapui5.hana.ondemand.com/sdk/#/topic/993e99eae4414b73bc7afef9518c79bf.html).
[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/examining-actions-available-on-the-list-report_e8e764b6-ba66-3cf7-becd-07af6f2c5dfa)
