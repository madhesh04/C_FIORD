# Using metadata to implement UI5 controls

*Source: https://learning.sap.com/courses/advanced-sapui5-development/working-with-sapui5-smart-controls*

Objective
After completing this lesson, you will be able to work with Smart Controls.
## Introduction to Smart Controls
### Introduction to Smart Controls
Occasionally, implementing SAPUI5 applications can become a repetitive task. Some applications may have a different use case and OData service but have exactly the same UI. Moreover, a lot of metadata comes with the backend OData service, for example, internationalization or field length, and if these metadata could be used from SAPUI5 controls, it would save a lot of developing time.
Smart Controls do use these metadata to provide powerful functionality. They are a specific category of SAPUI5 controls that have some special features in addition to the standard SAPUI5 features and thus make it easier to use the control in certain scenarios. Smart controls are part of the _sap.ui.comp_ library and are focusing strongly on SAP Fiori elements.
The namespace _sap.ui.comp_ contains the following control types:
  * SmartField
  * SmartTable and SmartList
  * SmartFilterBar
  * SmartChart and SmartMicrochart
  * SmartVariants
  * SmartGroup

SAP will continue to maintain the library and all of its controls in the future. However, there will be no development of new features unless specifically requested by SAP Fiori elements.
### Implementing the OData Service
OData Service can be implemented using the SAP Gateway Builder or ABAP CDS (for example, leveraging the SAP RESTful Application Programming Model).
![Screen capture of the SEGW transaction displaying the properties of the Flight Entity Type.](../images/c7dc0be3e3991e3e.png)
The figure shows the properties of an entity with the name Flight. As you can see, each property of the entity has various attributes. As the figure shows for some attributes, the attribute Sortable and Filterable is ticked. The property Currency is bound to the _currency-code_ semantic. This information can be used at runtime in the application to provide certain features - for example, a value help at the _Currency_ field.
### Checking OData Service Implementation
Navigate through the following simulation to learn how to check the OData service implementation.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_45474AB690E5880:uebung)
## Using Smart Controls
### Working with SmartForm Controls
Now, we will take a closer look at smart controls, starting with SmartForms.
The SmartForm control displays form content and can be used in combination with SmartField controls and OData metadata annotations along with additional configuration. The control allows you to create a form with minimal effort. Depending on their user authorizations, the form enables users to do the following:
  * Switch from display to edit mode
  * Add and group fields
  * Rename field labels
  * Implement a user input check

SmartForms only define the layout, that is, the form. In order to be able to display data, we have to use sap.ui.comp.smartfield.SmartField controls.

SmartForm Controls consist of

  * groups (sap.ui.comp.smartform.Group)
  * group elements (sap.ui.comp.smartform.GroupElement)

The SmartForm control aggregates groups, and a group aggregates group elements. The group elements themselves aggregate elements of type sap.ui.core.Control

Group Elements are
    collections of controls that are displayed along with a label.
Typically, a group element consists of exactly one control and the respective label. ![Sample view.xml file. Code shows a page with a smartForm control. containing differetn groups and several smartField controls.](../images/b68ce8e1517b8282.png)
The figure shows the implementation of a SAPUI5 view using SmartControls. As you can see inside the sap.ui.core.mvc.View implementation, we have XML-Aliases for the SAPUI5 namespaces of sap.ui.comp.smartfield and sap.ui.comp.smartform. The SmartField-Controls are bound to fields of the underlying OData service.
At runtime, the above view looks as follows. Take note that you have the above implementation in mind, especially the Price andPaymentsum fields.
![The resulting view with the three groups of fields.](../images/09424f39e22049fa.png)
As you can see from this figure, the _Airfare_ and the _Total_ fields do not simply show the price, they also display the currency. These values are displayed because the semantic information of the OData-service is used. The switch-to-edit button is visible in the UI. This is because the editTogglable was set to true in the view implementation.
When you select the button, the UI will provide the possibility to change data.
![The same view in Edit mode.](../images/78b9dc8d99297d5b.png)
In the display above, not all fields are editable in the form. The information about what field can be changed is also fetched from the OData Service.
### Using SmartField Controls
SmartField Controls
  * Provide an efficient way to add input-enabled fields.
  * Automatically adjust to the metadata of the underlying OData service, for example, by doing the following:
    * Hosting controls for editing and displaying the values of OData properties.
    * Providing value help automatically.
    * Performing input checks.
  * Implement field control and support message handling.

SmartField controls can be used in different scenarios:
  * As a standalone control, for example, in XML views.
  * In combination with a SmartForm control.
  * In combination with a SmartTable control.

They are used in particular as cell editor in editing scenarios.
Navigate through the following simulation to learn how to use smartfield controls.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_59922D797D83278C:uebung)
### The SmartTable Control
The SmartTable control
  * Is a wrapper control around any SAPUI5 table.
  * Analyzes the $metadata document of an OData service and renders a table for a specific entitySet.
  * Allows the consuming application to build list patterns in an efficient and consistent way and therefore makes it easy for the user to create tables without much effort.

The _SmartTable_ control offers you additional built-in features, such as a row count and the ability to export to a spreadsheet application.
Navigate through the following simulation to learn how to implement a smart table
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_C2CB0A84440B4698:uebung)
