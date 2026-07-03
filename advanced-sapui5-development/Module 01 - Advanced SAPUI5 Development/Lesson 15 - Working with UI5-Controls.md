# Working with UI5-Controls

*Source: https://learning.sap.com/courses/advanced-sapui5-development/extending-standard-controls_a98398b4-0412-4253-a520-b896ca4fb067*

Objective
After completing this lesson, you will be able to use the capabilities of the standard controls in the SAPUI5 framework.
## Extension of Standard Controls
Sometimes, the needs of the customer go beyond the capabilities of existing SAPUI5 controls. If this is the case, developers can extend existing controls and elements to fulfill customer needs.
Before we start with a detailed look on how to extend an existing SAPUI5 control, let's understand what makes a control a control.
#### What is a Control?

Conceptually:
    A control is a UI component (usually a visible one) that can react to the activities of the user and expose properties, methods, and events to the application (and other controls) using JS API.

Technically, a UI5 control at design time consists of:

The **Control API** definition that defines the properties, events, methods, and sometimes the associations and aggregations.
The **Control Renderer** that is responsible for creating the HTML string that defines the structure of the control.
The **Control Behavior** , which is the JavaScript code taking care of the control interactivity, reacting to user events, firing control events, handling method calls, and property changes.
The **Control Style** that defines the visuals of the control (usually a control that has different visual designs, bundled as "Themes").
### Control API
The control API is represented by the keyword **metadata**.
Control metadata consists of properties, events, aggregations, and associations. Let's now look at each of these in more detail.
### Control Metadata - Properties
The control properties are made up of a name and a type, and optionally, a default value. Valid types are string (default), boolean, int or float for numeric properties, int[ ] (for example, array of int) and sap.ui.core. CSSSize for a property that holds (for example, px) or rem values for size.
![Sample code of a control extension showing the metadata section where new properties are defined.](../images/dc2c04b74d220779.png)
### Control Metadata - Events
The control events are defined by their name only.
Methods for registering, de-registering, and firing the event are created by the framework. For example, _attachHover_ , _detachHover_ and _fireHover_.
![Sample code of a control extension. Metadata section defining one allowhover property and one hover event.](../images/c18471589a644660.png)
### Control Metadata - Aggregations and Associations
SAPUI5 also knows composite UI-controls. To implement a composite UI-control, the control developer has to define aggregations or associations to other controls.

Aggregations

Aggregations are defined by their name and a configuration object. It is a relationship between two controls. It shows a parent/child relationship. For example, table rows (parent) and cells (children) The name of the aggregation has to be a string value written in plural. The below image shows how to define an aggregation.
![Sample code of a control extension. Metadata aggregations section defining three components: acceptButton, content and worksetItems.](../images/5b947f9f91402c42.png)
  * **Type** The type property contains the subclass of the control. If type is all you want to set, you can do so as a string instead of the configuration object.
  * **Multiple** The property defines the cardinality and can contain the values 0..1 or 0..n. The default is 0..n.
  * **singularName** This property contains the name of the aggregation in singular. The framework will provide methods like addWorksetItem.

Associations
    An association is a relationship between two controls. It is not a parent/child relationship. It represents a loose coupling. For example, a label is associated with a text field.
### Control Behavior
After adding the metadata, you add method implementations to the control.
### Rules for Control Method Naming
  * Do not use names of methods provided in superclass. This would result in overriding the superclass methods.
  * Private methods are identified by name starting with a underscore, for example, _checkForZero. All other methods are considered public.
  * Do not use names starting with get…, set…, insert…, add…, remove… or indexOf… as they could collide with automatically generated methods of the properties or aggregations.
  * Method names with special meanings are as follows:
    * on…: are used for event handlers.
    * init: are used to initialize the control, after its instantiation. This is a private method only called by the SAPUI5 core.
    * renderer: used for the function that creates the control’s HTML.

Event handler methods are called automatically. For example, if you hover the mouse on top of a control, the system automatically fires the onmouseover event.
You can find the automatically managed events in the API reference .[sap/ui/events/ControlEvents](https://ui5.sap.com/#/api/module:sap/ui/events/ControlEvents%23overview)
Inside the event handler method, we have access to getters and setters of properties. Those are automatically provided by the framework.
Our example extended button control has an _allowHover_ property. As a result of that, you should understand that the framework creates the _getAllowHover( )_ method as seen in the code below.
![Sample code of a control extension showing the onmouseover method definition that fires the hover event..](../images/e9dc7e51d4273ff9.png)
To handle the event at runtime, you should know that the framework creates a method with "on" in front of the event name.
Our extended control has an event named "hover", so we must use the onHover method.
![Sample View.xml file with the new control added in the namespaces and content of the page. the hover event is defined with the value onHover. In the view controller.js file, the onHover method is defined to display a message.](../images/ad29d225bfd4ee44.png)
### Control Rendering

The Control Renderer

  * The renderer is responsible for creating the HTML structure for the control.
  * A renderer is assigned to the render method of the control.
  * It is static, so you cannot use "this". _Control_ instance and _RenderManager_ instance are given to the method.
  * The renderer method has access to the control’s property getters and setters, as well as to any aggregations and associations defined by the control.

The RenderManager

_RenderManager_ collects and concatenates string fragments and places them in the DOM at the appropriate position by using its methods such as the following:
  * _openStart_ - Opens the start tag of an HTML element,
  * _openEnd_ - Ends an open tag started with openStart,
  * _style_ - Adds a style name-value pair to the style collection of the last open HTML element. This is only valid when it is called between openStart/voidStart and openEnd/voidEnd.

### Referencing the Control Renderer
The UI-control definition takes a reference to the renderer class.
![Sample code of a control extension with a control renderer.](../images/7c44e2cde803bd34.png)
### Sample: Control Renderer
The following figure shows you (in a sample implementation) the anatomy of a renderer implementation.
![Sample code of a control renderer.](../images/efc5eb94ef2bfd7c.png)
As of SAPUI5 1.67, the RenderManager provides a set of new APIS to describe the structure of the DOM that can be used by the control renderers. To use the new API, assign the property **apiVersion** with the value 2 to your Renderer implementation.
### Render Function Implementation
The following figure shows a sample implementation of the render method. The method has access to the RenderManager instance and to the control that should be rendered.
![Sample code of a control renderer render function.](../images/6b2f609342b65089.png)
## Extend an Existing Control
### Business Example
In this exercise, you will extend one of the standard SAPUI5 controls to add functionality. The Button control will be extended and the new control added to the Flights table. The control will be modified to add a hover event and display text that is controlled through a custom property on the control. To save some time, you will adjust the _fullscreen_ application.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and the naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You need to have completed the previous exercises to implement a fullscreen application.
Note
You can import the 1-Fullscreen complete.tar file from the solutions if you want.
### Task 1: Extend the Button Control
In this step, you will create the JavaScript file that contains the new _HoverButton_ control, extension of a sap.m.Button control.
#### Steps
  1. Open the SAP Business Application Studio.
  2. Open the _fullscreen_ project from the previous exercises.
    1. Perform this step as shown in a previous exercise.
  3. Create a new folder with the name **control** in the _webapp_ folder of your project _fullscreen_ and add a file with the name **HoverButton.js** to the newly created folder.
    1. Select your project _webapp_ folder and from the context menu, choose _New Folder_.
    2. In the entry field, enter the name **control** as the folder name and choose the _Enter_ key (on your keyboard).
    3. Select the newly created folder and from the context menu, choose _New File_.
    4. In the new entry field, enter **HoverButton.js** as file name and choose the _Enter_ key (on your keyboard).
  4. In the HoverButton.js file, extend the standard Buttoncontrol from the _sap.m_ library, and name the extension HoverButtonin the student.com.sap.training.advancedsapui5.fullscreen.control namespace.
    1. Enter the following code in the HoverButton.js file:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213

sap.ui.define([
  "sap/m/Button"
],

  function (Button) {
    "use strict";

    return Button.extend("student.com.sap.training.advancedsapui5.fullscreen.control.HoverButton", {
    });
  }
);

```

  5. Define the metadata and add the properties allowHover and hoverText with the following attributes and value assignments to the metadata:
#### Property-value pairs for allowHover
| Property  | Value  |
| --- | --- |
| type  | **boolean**  |
| defaultValue  | **false**  |
#### Property-value pair for hoverText
| Property  | Value  |
| --- | --- |
| type  | **string**  |
    1. Enter the following code in the extend function:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

metadata: {
  properties: {
    "allowHover": {
      type: "boolean",
      defaultValue: false
    },
    "hoverText": {
      type: "string"
    }
  }
},

```

  6. Add a new custom event called hover with empty brackets {} as the value.
    1. Enter the following code after the properties definition:
Code Snippet
Copy codeSwitch to dark mode

```

12345

,
events: {
  "hover": {}
}

```

  7. Add an onmouseover function after the metadata.
    1. Enter the following code after the metadata definition :
Code Snippet
Copy codeSwitch to dark mode

```

1234

onmouseover: function(evt) {

}

```

  8. In the onmouseover function, check if allowHover is true, and if it is, fire the hover event.
Hint
Remember that the properties will have getter and setter methods created by the framework. Events will have the fire method created, for example firePress, for an event named press.
    1. Enter the following code inside the onmouseover function:
Code Snippet
Copy codeSwitch to dark mode

```

1234

if (this.getAllowHover()) {
  this.fireHover();
}

```

  9. Add a renderer with empty brackets {} as the value. Then save your changes.
Note
There should be no syntax errors. If you have an event parameter for the onmouseover method, you can ignore the error that it is unused.
    1. Enter the following code after the onmouseover definition:
Code Snippet
Copy codeSwitch to dark mode

```

123

,
renderer: {}

```

    2. Save your changes. Your HoverButton implementation should now look like the following:
![Screenshot of the resulting code for the](../images/2d337f64d083ddc6.png)

### Task 2: Add the HoverButton Control to the Application
#### Steps
  1. Open the Flights.view.xml file. In order to use the new HoverButton control, an XML namespace must be added to the view so that it can address the control properly. At the top of the Flights.view.xml file, several namespaces are defined pointing to SAP provided libraries. Add a new XML namespace with the prefix of cust pointing to the namespace where the HoverButton control is located.
    1. Enter the following code after xmlns:l="sap.ui.layout" :
Code Snippet
Copy codeSwitch to dark mode

```

1

xmlns:cust="student.com.sap.training.advancedsapui5.fullscreen.control"

```

  2. As a last element of the columns aggregation, add a new mobile enabled Column element with the following attributes and values:
#### Attribute-value Pairs for the Column Element
| Attribute  | Value  |
| --- | --- |
| id  | **flbooking**  |
| minScreenWidth  | **Tablet**  |
| demandPopin  | **true**  |
| hAlign  | **Center**  |
    1. Enter the following code after the column4 declaration:
Code Snippet
Copy codeSwitch to dark mode

```

12345

<Column id="flbooking" minScreenWidth="Tablet" demandPopin="true" hAlign="Center">

</Column>

```

  3. Add a new sap.m.Text element with the following attribute to the new Column element:
#### Attribute-value Pair for the Text Element
| Attribute  | Value  |
| --- | --- |
| id  | **flbookingtext**  |
| text  | **{i18n >bookaction}**  |
    1. Enter the following code inside the column definition:
Code Snippet
Copy codeSwitch to dark mode

```

1

<Text id="flbookingtext" text="{i18n>bookaction}"/>

```

  4. As a last element of the cells aggregation, add a HoverButton element with the following attributes and values. Now, save your changes.
#### Attribute-value Pairs for the HoverButton Element
| Attribute  | Value  |
| --- | --- |
| text  | **{i18n >bookaction}**  |
| allowHover  | **true**  |
| hoverText  | **{=${Seatsmax} - ${Seatsocc}}**  |
| hover  | **onHover**  |
| id  | **hoverButton1**  |
Note
The HoverButton is placed in a project specific namespace.
    1. Enter the following code after the flseatsocctext element:
Code Snippet
Copy codeSwitch to dark mode

```

12345

<cust:HoverButton id="hoverButton1" text="{i18n>bookaction}"
      allowHover="true"
      hoverText="{=${Seatsmax} - ${Seatsocc}}"
      hover="onHover"
/>

```

    2. Save your changes.
  5. Add the following key-value pair to the i18n.properties file:
#### Key-value Pair within the i18n.properties File
| Key  | Value  |
| --- | --- |
| bookaction  | Book flight  |
    1. Perform this step as shown in a previous exercise.
  6. Run the application.
Note
Be aware that since we are not testing the application in a real SAP Fiori environment you will get errors in the console if you use Dev Tools to debug your application. Please, dismiss any message about resource preload.
    1. Perform this step, as shown in a previous exercise.
  7. Verify that the application runs properly and that a new Button is shown in each row of the Flights table. The functionality for the hover has not been implemented yet so there are no added features at this point.
![Resulting application screen. A button is displayed on every flight row.](../images/104a6a991a97b706.png)
    1. Choose a carrier in the Carriers table.
    2. Verify that the application runs properly and that a new Button is shown in each row of the Flights table.

### Task 3: Implement the Hover Action
#### Steps
  1. Open the i18n.properties file and add the following key-value pair (with a leading blank at the value) to the file. Now, save your changes.
#### Key-value Pair within the i18n.properties File
| Key  | Value  |
| --- | --- |
| msgSeatsAv  | seats are available  |
    1. Open the i18n.properties file and enter the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123

#MSG
msgSeatsAv=seats are available

```

    2. Save your changes.
  2. The HoverButton control that was added has the hover method set to call a method called **onHover**. This method is not yet implemented by the application. Open the Flights.controller.js file and add a new dependency to the sap.m.MessageToast control.
    1. Open the Flights.controller.js file located in the _controller_ folder of your project.
    2. Update the code as follows :
Code Snippet
Copy codeSwitch to dark mode

```

1234567

sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast"
],
function (Controller, MessageToast) {
    "use strict";

```

  3. Add the onHover function to the controller implementation. The function takes one argument with the name, evt.
    1. Enter the following code after the onNavBack function implementation :
Code Snippet
Copy codeSwitch to dark mode

```

1234

,
onHover: function(evt) {

}

```

  4. In the onHover method, add code to display a MessageToast with the HoverButton controls hoverText displayed for 1000 milliseconds. Read the hoverText from the source of the event. Use the i18n capabilities of UI5. Now, save your changes.
    1. Enter the following code inside the onHover function:
Code Snippet
Copy codeSwitch to dark mode

```

123

var sText = this.getOwnerComponent().getModel("i18n").getProperty("msgSeatsAv");
MessageToast.show(evt.getSource().getHoverText() + " " + sText, {duration: 1000});

```

  5. Start the application.
    1. Perform this step as shown in a previous exercise.
  6. Select a carrier and navigate to the Flights table.
    1. Perform this step as shown in a previous exercise.
  7. Hover over the button in the table. A _MessageToast_ dialog box with the available seats for booking appears.
![Resulting message displayed when hovering on top of the new button.](../images/fe531eb3c58befdd.png)
    1. Hover over the button in the table.
    2. A _MessageToast_ dialog box with the available seats for booking appears.
  8. Since we will further develop your fullscreen project in a following exercise, you can save the current state of the project by downloading it. Select the _fullscreen_ project and from the context menu, choose _Download_.
