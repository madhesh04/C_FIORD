# Examining Actions Available on the List Report

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/applying-generic-actions-provided-by-sap-fiori-elements_ee9f52af-318a-4979-a8b5-929c5edebbee*

Objective
After completing this lesson, you will be able to influence the visibility and enablement of the Delete and Create actions.
## Generic Actions
### What are Actions?
Actions trigger either an interaction with the back end (calling the OData service) or they initiate an external navigation to another app. You can see actions displayed as buttons on the apps.
### Placement of Actions in Apps
The SAP Fiori design guidelines define where the actions can be placed as buttons on the UI. According to the guidelines, actions must be placed close to the information they act upon. An example can be placing the actions on the toolbar of the table or chart in the list report. Another example would be placing the global actions in the header area of the object page.
For more information about actions, see [Actions](https://sapui5.hana.ondemand.com/sdk/#/topic/cbf16c599f2d4b8796e3702f7d4aae6c).
For more information about the action placement, see [Action Placement](https://experience.sap.com/fiori-design-web/action-placement/).
### Generic Actions
SAP Fiori elements provides generic actions, such as:
  * Trigger external navigation to related apps.
  * Create a new item.
  * Delete a single item or multiple items.
  * Edit an existing item.

In the list report, the _Create_ and _Delete_ actions are placed in the table toolbar.
![User interface of the list report, highlighting the Create button and the Delete button, which is disabled](../images/d0fbaa470b6d49f6.png)
On the object page, the _Edit_ and _Delete_ actions are global actions placed in the header area.
![User interface of the object page, highlighting the Edit and Delete buttons](../images/6f2a2619af2fde93.png)
The  _Delete_ button is an action on the table and is enabled only if the user selects an item.
### Visibility of the _Delete_ and _Create_ Buttons
You can control the visibility of the _Delete_ button by using the @UI.DeleteHidden annotation. Its value can be a Boolean value (true or false), or a path that points to a Boolean property of an entity. If the value of the property is true, then the _Delete_ button is hidden; if it's false, it's visible.
Code Snippet
Copy codeSwitch to dark mode

```

12345

annotate TravelService.Travel with @UI : {
  DeleteHidden : true
}

```

Similarly, you can control the visibility of the _Create_ button using the @UI.CreateHidden annotation. Its value can be a Boolean value (true or false), or a path that points to a Boolean property of an entity. If the value of the property is true, then the _Create_ button is hidden; if it's false, it's visible.
Code Snippet
Copy codeSwitch to dark mode

```

12345

annotate TravelService.Travel with @UI : {
  CreateHidden : true
}

```

### Disable the _Delete_ Button
Instead of hiding the _Delete_ button, you can choose to disable it in the app by using the @Capabilities.DeleteRestrictions annotation. You can set its Deletable property to true or false. If the value of this property is true, the _Delete_ button is enabled for all items; if it's false, it's disabled for all items.
Code Snippet
Copy codeSwitch to dark mode

```

12345678

annotate TravelService.Travel with @(
Capabilities.DeleteRestrictions : {
$Type : 'Capabilities.DeleteRestrictionsType',
Deletable: false
}
);

```

You can also disable the delete action for specific items by assigning a path to the Deletable property that points to a particular Boolean property of the entity.
Code Snippet
Copy codeSwitch to dark mode

```

12345678

annotate TravelService.Travel with @(
Capabilities.DeleteRestrictions : {
$Type : 'Capabilities.DeleteRestrictionsType',
Deletable: TravelStatus.insertDeleteRestriction
}
);

```

The items in the _Manage Travels_ app have various statuses such as _Open_ , _Accepted_ , and _Canceled_.
You can see that for the status _Open_ the value for insertDeleteRestriction is true, and for the statuses _Accepted_ and _Canceled_ the value is false. This means that for travels with the status _Accepted_ and _Canceled_ , the _Delete_ action is disabled.
You can see the values for the insertDeleteRestriction in the sap.fe.cap.travel-TravelStatus.csv.
Code Snippet
Copy codeSwitch to dark mode

```

123456

code;name;criticality;fieldControl;createDeleteHidden;insertDeleteRestriction
O;Open;2;7;0;1
A;Accepted;3;1;1;0
X;Canceled;0;7;1;0

```

For more information about enabling or disabling of the _Create_ button, see [Adding Actions to Tables](https://sapui5.hana.ondemand.com/sdk/#/topic/b623e0bbbb2b4147b2d0516c463921a0.html).
## Make the Delete Action Unavailable for Accepted and Canceled Travels
### Context
In this exercise, you will learn to disable the _Delete_ action based on some conditions.
### Task Flow
In the _Manage Travels_ app, you can see that the _Delete_ action is displayed in the table toolbar of the list report. You will disable the delete action for travels with the travel status Accepted and Canceled.
### Prerequisites
First, you have to enable the filter bar again, because it was hidden in the previous exercise Hide the Filter Bar in the List Report in the unit Configuring the List Report Filter Bar (lesson: Hiding the Filter Bar). Alternatively, you can check out the branch: [solution/add-semantic-fields-to-filterbar](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-semantic-fields-to-filterbar).
### Watch the Steps and Perform the Simulation
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_65FF40DB97656B95:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. In the _Explorer_ view, select _Projects_ → _schema.cds_. The entity TravelStatus has a definition for all three travel statuses _Open_ , _Accepted_ , and _Canceled_. The entity also has a property named insertDeleteRestriction with the value Boolean.
  3. Open the TravelStatus.csv file. You can see that the insertDeleteRestriction has the value 1 for the Open status and 0 for the Accepted and Canceled statuses.
  4. Select the schema.cds file. Add the following annotation to it:
Code Snippet
Copy codeSwitch to dark mode

```

123456

annotate Travel with @(
   Capabilities.DeleteRestrictions : {
       $Type : 'Capabilities.DeleteRestrictionsType',
      Deletable: TravelStatus.insertDeleteRestriction
   }
);

```

Note that the Deletable property is bound to the value of the insertDeleteRestriction property of the TravelStatus entity.
  5. View the _Delete_ action in the _Manage Travels_ application.
    1. Open the _Manage Travels_ application.
    2. Select any travels with the travel statuses _Accepted_ and _Canceled_.
#### Result
The _Delete_ action is disabled for travels with the travel statuses _Accepted_ and _Canceled_.
    3. Select a travel with the travel status _Open_.
#### Result
The _Delete_ action is enabled for travels with the travel status _Open_.

### Result
The generic actions such as _Delete_ and _Create_ are provided by SAP Fiori elements. As an app developer, you can choose to control their visibility. You can also hide or disable the actions for some instances of the object (entity).
Note
  * You can find the files for this solution on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/make-delete-action-unavailable-for-accepted-travels](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/make-delete-action-unavailable-for-accepted-travels).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/add-semantic-fields-to-filterbar..solution/make-delete-action-unavailable-for-accepted-travels).
