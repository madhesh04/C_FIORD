# Verifying the User Input

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/verifying-the-user-input_e7f23ca9-d9f8-4bc6-906a-97e5c11b9b21*

Objective
After completing this lesson, you will be able to help users see if their input is incorrect.
## User Input Validation
As a user creates a new business object item or changes an existing one by selecting the _Edit_ button on the object page, the system creates a draft which is automatically saved in the background. The message _Draft updated_ is displayed in the footer after each update of the draft. It is allowed to update draft while it is still incomplete and inconsistent. In order to activate the draft (that is to save the draft as an active document), the input should be consistent. For that, there are different validation checks which can be done.
For more information about draft handling, see [Draft Handling](https://sapui5.hana.ondemand.com/sdk/#/topic/ed9aa41c563a44b18701529c8327db4d.html).
### Client Side Validations
Client side validations, as the name suggests, are executed on the front end and are done and visualized immediately after the focus leaves the input field. For example, a user can enter the wrong date format or more characters than the field length allows. The field is marked red and a message button appears in the footer of the object page ( bottom left). It displays the number of errors and, when choosing it, a message popover opens and displays the messages. They are displayed as long as the errors are not corrected.
![Client side error message displayed in a popover](../images/7f00425524f3e7bd.png)
You can also navigate to the corresponding field and see the same error message there.
![The error message displayed in the End Date field](../images/c407d2d3743df6d6.png)
### Back-end validations
Other input consistency checks may require some validations in the back end. Usually such validations are triggered as a user chooses the _Save_ button on the object page (correspondingly the _Apply_ button on the subobject page).
The app is responsible for preparing such consistency checks in the back end.
For example, CAP runtimes automatically validate user input in the fields which correspond to the properties annotated with @assert.integrity, @assert.target, and some others. Check the CAP documentation for the complete list of supported input validation annotations [Input Validation](https://cap.cloud.sap/docs/guides/providing-services#input-validation).
SAP Fiori elements automatically displays messages that are sent from the back end as part of the request-response cycle. The messages for subitems are also displayed.
Messages referring to the state of an instance, for example input consistency checks, are called state messages. They are displayed in the Edit mode on the object page and the subobject page in the same popover as the client side validation messages. The messages are displayed on the UI as long as the inconsistencies are not corrected. The state messages can be persisted in the back end.
For the sake of completeness we have to mention the transition messages which can also be sent from the back end.
They are 'transient' in nature and do not affect the state of the object. They refer only to the last action that was executed. These messages are not relevant for the user input validation. These messages can be displayed in the list report or on the object page in the display mode. For more information, see [Using Messages](https://sapui5.hana.ondemand.com/sdk/#/topic/239b1922758645e7b451e01ded7f56bc).
For more annotations for User Input validation with CAP, see [Common Annotations](https://cap.cloud.sap/docs/cds/annotations).
## Add the Validation for the Field Agency on the Object Page
### Usage Scenario
In the Manage Travels app, you want to prevent users from adding an incorrect agency name. To achieve this, you want to add a validation so that an error is displayed each time when the user tries to save a travel entry with an agency name that doesn't exist in the database.
### Task Flow
In this exercise, you will add an annotation that validates the user input for the field Agency.
In the CAP CDS data model, to_Agency is a managed to-one association in the Travel entity to the TravelAgency entity. So, a CAP validation will be triggered for to_Agency during Create and Edit events. In UI terms, this is when the user selects _Save_ to save the travel entry on the object page.
### Prerequisites
You have completed the exercise Hide the Starting Date and End Date for Travels with the Canceled Travel Status in the unit Applying Dynamic Field Control and Validating User Input on the Object Page (lesson: Dynamically Affecting the Visibility and Editability of UI Elements). Alternatively, you can check out its solution branch: [solution/hide-starting-and-end-dates-for-canceled-travels](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/hide-starting-and-end-dates-for-canceled-travels).
### Watch the Simulation and/or Perform the Steps
This exercise provides a simulation that guides you through the list of steps below. Performing these steps allows you to follow the simulation in your trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_49C4C18FC5DA0F91:uebung)
### Steps
  1. Open your CAP project in SAP Business Application Studio.
  2. In the Explorer view, under Projects, select db/data/schema.cds.
  3. Open the schema.cds file.
  4. In the Travel entity, add the @assert.target annotation for to_Agency.
It is a managed to-one association to the TravelAgency entity. The annotation checks if the user input for the _Agency_ field has a corresponding entry in the associated or referenced target table for the TravelAgency entity.
  5. Perform the following steps to check.
    1. Open the Manage Travels app.
    2. Click _Edit_.
    3. Enter a value in the _Agency_ field. This value must not exist in the reference table.
    4. Click _Save_.

### Result
You cannot save the document as the value entered in the Agency field is incorrect.
Note
  * You can find the project files for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/add-validation-for-field-agency-on-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/add-validation-for-field-agency-on-op).
  * You can find the link to the direct comparison of the branch to the previous one on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/hide-starting-and-end-dates-for-canceled-travels..solution/add-validation-for-field-agency-on-op).

[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/applying-dynamic-field-control-and-validating-user-input-on-the-object-page_2799f50f-80b6-30ff-8a19-8e37eb2ec9f3)
