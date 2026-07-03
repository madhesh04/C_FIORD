# Configuring Side Effects

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-side-effects_a7e5f948-c568-4cb9-acb4-37073eb958fa*

Objective
After completing this lesson, you will be able to configure side effects to immediately update specific UI fields after some changes in the UI.
## Side Effects on the Object Page
When using the _Edit_ and _Create_ modes, certain user actions or updates in one field may require immediate updates in other UI elements.
For example, when a user selects a book in a bookshop app, its price is shown in the _Price_ field. When they select another book, the _Price_ field should display the new price immediately. This means you would need to get the corresponding value from the back end and update the appropriate field in the user interface.
In SAP Fiori elements, these actions are known as side effects. You can use the @Common.SideEffects annotation to indicate that changes in some UI elements (known as source entities or source properties) should trigger a request to update other UI elements (target entities or target properties).
There are some default side effects which apply to all apps. For example, if a user creates a new entity or a draft version in the list report or object page, the list binding of the parent page is refreshed to show the new item. These side effects apply automatically, and you don't need to annotate them. For more information, see [Side Effects](https://sapui5.hana.ondemand.com/sdk/#/topic/18b17bdd49d1436fa9172cbb01e26544.html).
Note that the side effects request will not be triggered if there are any validation errors in the user interface. In this case, the errors should be resolved first.
For more examples of side effects you can add to your app, see [Side Effect Annotations: Examples](https://sapui5.hana.ondemand.com/sdk/#/topic/61cf21d50ed34cbf888713496c618904.html).
## Use Side Effects to Update the Total Price Immediately After Adding Another Booking
Certain actions in the user interface can affect other UI elements. You can use side effects to specify that these actions should immediately trigger an update in the corresponding field.
### Task Flow
In this exercise, you will add a new booking to an existing travel and note the application's behavior. Then, you will use SAP Business Application Studio to add the necessary annotations. Finally, you will check the results.
### Prerequisites
You have completed the exercise Display the Travel Administrative Data Subsection on Demand (by Adding the "Show More" Button) in the unit Configuring the Body of the Object Page (lesson: Suppressing Optional Information in Demand). Alternatively, you can check out its solution branch: [solution/add-show-more-button-on-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-show-more-button-on-op).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_A179B5489DAE5FA3:uebung)
### Steps
  1. Add a new booking to the travel and check the application's behavior.
    1. Select the pin icon on the top of the page and choose _Edit_.
    2. Select _Create_.
    3. Open the _Input Help_ for the new booking and select an item from the list.
    4. Note that the draft has been updated with the new booking but the _Total Price_ in the object page header remains unchanged.
    5. Save the draft. Note that the _Total Price_ is only updated after the new version has been saved.
  2. Add side effects to the booking.
    1. Open layouts.cds in SAP Business Application Studio.
    2. Annotate TravelService.Travel with @Common.SideEffects.
Code Snippet
Copy codeSwitch to dark mode

```

1234

annotate TravelService.Travel @(Common.SideEffects #ReactonItemCreationOrDeletion: {
    SourceEntities  : [to_Booking],
    TargetProperties: ['TotalPrice']
});

```

  3. Check the results.
    1. Add a new booking like you did in the first step.
    2. Note that the _Total Price_ field is updated immediately.
    3. Save the draft. Note that the _Total Price_ does not change anymore as it was already updated.

### Result
In this lesson, you have learned to add and use side effects to update the total travel price immediately after adding a new booking.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/use-side-effects-to-update-total-price](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/use-side-effects-to-update-total-price).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-show-more-button-on-op..solution/use-side-effects-to-update-total-price).

### Next Steps
For more information, see:
  * [Side Effects](https://sapui5.hana.ondemand.com/sdk/#/topic/18b17bdd49d1436fa9172cbb01e26544)
  * [Side Effect Annotations: Examples](https://sapui5.hana.ondemand.com/sdk/#/topic/61cf21d50ed34cbf888713496c618904.html)

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/configuring-the-body-of-the-object-page_d3752eb3-9474-3552-9737-3d7f604c1b4e)
