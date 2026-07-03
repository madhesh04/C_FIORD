# Applying Dynamic Field Control and Validating User Input on the Object Page

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/dynamically-affecting-the-visibility-and-editability-of-ui-elements_dc77e765-a36d-4054-ba1d-d1fc9ab3ddfd*

Objective
After completing this lesson, you will be able to influence the visibility and editability of some UI elements.
## Dynamic Field Control
In the lesson Suppressing Optional Information on Demand, you learned how to hide sections, subsections and separate fields on the object page. In this case, the _Show More_ or _Show Less_ buttons appear in the app; selecting them displays the sections.
You can also hide some content on the object page either permanently or based on some condition. In this case, the user will not be able to open this content; it will not appear in the object page. For example, you may want to hide the _Starting Date_ and _End Date_ fields for canceled travels as they are not relevant in this situation.
To do this, you can use the @UI.Hidden annotation. It has a boolean value that can either be static (true or false for all object instances) or dependent on some other property that can have different values for different object instances.
In addition to hiding fields, you can also control other field properties such as making them read only or mandatory. You can do it either in the Page Map or directly with the corresponding annotations. For more information, see [Further Features of the Field](https://sapui5.hana.ondemand.com/sdk/#/topic/f49a0f7eaafe444daf4cd62d48120ad0).
## Hide the Starting Date and End Date for Travels with the Canceled Travel Status
There are two date fields in the _General Information_ subsection: _Starting Date_ and _End Date_. You will hide them for travels with travel status _Canceled_.
### Task Flow
In this exercise, you will add a new property cancelRestrictions to the TravelStatus entity. This will indicate that certain restrictions apply for these travels: its value will be true for _Canceled_ travels and false for _Open_ and _Accepted_ travels.
Then, you will add an @UI.Hidden annotation to both date fields: _Starting Date_ and _End Date_. It will hide the fields based on the value of the cancelRestrictions property created before.
### Prerequisites
You have completed the exercise Use Side Effects to Update the Total Price Immediately After Adding Another Booking in the unit Configuring the Body of the Object Page (lesson: Configuring Side Effects). Alternatively, you can check out its solution branch: [solution/use-side-effects-to-update-total-price](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/use-side-effects-to-update-total-price).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation displaying all the steps. You can follow the simulation with your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_91FCB10F64DA59BA:uebung)
### Steps
  1. Add a new property to indicate the canceled travels.
    1. Open the schema.cds file from your project in SAP Business Application Studio.
    2. Add a cancelRestrictions property to the TravelStatus entity.
Sample code:
Code Snippet
Copy codeSwitch to dark mode

```

1

cancelRestrictions: Boolean; // is true for cancelled travels

```

    3. Open the sap.fe.cap.travel-TravelStatus.csv file from the db>data folder.
    4. Add a new property: cancelRestrictions and its corresponding values: 1 (true) for Canceled, 0 (false) for Open and Accepted.
  2. Add @UI.Hidden annotations to the layouts.cds file.
    1. Annotate the BeginDate and EndDate properties with ![@UI.Hidden]: TravelStatus.cancelRestrictions.
  3. Return to the app to check the results.
    1. Select a travel and choose _Reject Travel_.
    2. Open its object page. Note how the _Starting Date_ and _End Date_ fields are not displayed for this travel as its _Travel Status_ is _Canceled_.

### Result
In this lesson you learned how to hide some content on the Object Page with the help of the @UI.Hidden annotation based on some static or dynamic Boolean value.
Note
  * You can find the files for this solution on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/hide-starting-and-end-dates-for-canceled-travels](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/hide-starting-and-end-dates-for-canceled-travels).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/use-side-effects-to-update-total-price..solution/hide-starting-and-end-dates-for-canceled-travels).

### Next Steps
For more information, see
  * [Hiding Features Using the UI.Hidden Annotation](https://sapui5.hana.ondemand.com/sdk/#/topic/ca00ee45fe344a73998f482cb2e669bb)
  * [Different Representations of a Field](https://sapui5.hana.ondemand.com/sdk/#/topic/c18ada4bc56e427a9a2df2d1898f28a5)
  * [Further Features of the Field](https://sapui5.hana.ondemand.com/sdk/#/topic/f49a0f7eaafe444daf4cd62d48120ad0)
