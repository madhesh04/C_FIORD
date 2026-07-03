# Creating Custom Controls

*Source: https://learning.sap.com/courses/advanced-sapui5-development/creating-custom-controls_d03c403b-4360-49b7-8fd1-fbf5d2696a18*

Objective
After completing this lesson, you will be able to implement custom controls using the SAPUI5 framework.
## Custom Controls
### Developing Your Own Controls
Sometimes, requirements go beyond the possibilities of extending standard controls. In other cases, it is necessary to implement a reusable custom control by combining existing controls. Using SAPUI5, it is also possible to implement your own customer-specific controls, so-called custom controls. In this lesson, you will learn how to implement such custom controls.
### Creating Custom Controls
When you are able to extend an existing control, creating a custom control is not really that different. When you create a custom control, you simply change what the control is extending and then you have to implement the renderer fully on your own.
Watch this video to know more.
Settings
### Control vs. Element
As you already know, SAPUI5 offers more than just basic controls. In addition, the SAPUI5 framework does provide more complex controls with dependencies to other controls. The framework also has visual aspects called elements. An element in SAPUI5 cannot be used by itself, it has to be used in combination with a control. They live in a parent-child dependency. The control in the relationship is the parent and the element is the child. The parent knows, for example, how to display or render the child during runtime.
The following rules are applied to elements :
  * sap.ui.core.Element is base class of sap.ui.core.Control
  * It does have an API but not a renderer.
  * It is not meant to be used as a standalone.
  * Typically, it is aggregated by a control (for example, MenuItems in a Menu).
  * The control does the rendering and uses the Element as data container.

An Element is the most basic building block for UI5 UIs. An Element has a state like a ManagedObject and it has a unique ID by which the framework remembers it. It can have an associated DOM, but it cannot render itself. Only [Controls](https://ui5.sap.com/api/sap.ui.core.Control) can render themselves and also take care of rendering Elements, which they aggregate as children. If an Element has been rendered, its related DOM gets the same ID as the Element and thereby can be retrieved through API.
### Working with elements
The following figure shows you how to use elements during aggregation binding.
![Sample code of a view.xml file. A person control is inserted into the page, bound with /persons, and the PersonItem element is added in the items aggregation displaying firstname and lastname. The resulting screen is shown.](../images/90772e9a6a613403.png)
The code shown in the following figure shows you the implementation and relationship of a control and an element.
![Sample code of Person.js and PersonItem.js files.](../images/87e50acaa3962538.png)
The code shown in the following figure shows you how to access the list of PersonItem-elements.
![Sample code of the PersonRenderer.js file.](../images/2e4a9a3332b3fb83.png)
## Create a Custom Control
### Business Example
In this exercise, you will extend the _fullscreen_ application by adding a custom control. The control shows data about the plane in the Flights table, including the following:
  * Maximum number of passengers
  * Current number of passengers booked

This is shown in the following figure:![Plane Infos details with maximum of passengers and current passengers.](../images/02957f75cfb008cf.png)
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures, and the naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You need to have completed the previous exercise on implementing a full-screen application. The solutions show the application after completion of exercise on extending controls but this part is not needed for the following exercise.
Note
You can download either the 1-Fullscreen complete.tar or the 3-controlextend.tar files in the solution to start with if you want.
### Task 1: Create the Custom Control
#### Steps
  1. Open the SAP Business Application Studio.
  2. In the _control_ folder of the _fullscreen_ (or _controlextend_) project, create a new file named **PlaneInfo.js**.
    1. Perform this step as shown in a previous exercise.
  3. In the PlaneInfo.js file, create a custom control named **PlaneInfo** by extending the sap.ui.core.Control.
    1. Use the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314

sap.ui.define([
    "sap/ui/core/Control"
  ],

    function (Control) {
      "use strict";

      return Control.extend("student.com.sap.training.advancedsapui5.fullscreen.control.PlaneInfo", {

      });
    }
  );

```

  4. Add a metadata section. Add the following properties to the metadata definition and assign the given type as a type attribute. Then save your changes.
#### Properties within the Metadata Section of the PlaneInfo.js File
| Property  | Type  |
| --- | --- |
| seatsMax  | string  |
| seatsOcc  | string  |
    1. Enter the following code inside the extend function:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011

metadata:{
  properties: {
    "seatsMax" : {
      type: "string"
    },
    "seatsOcc" : {
      type: "string"
    }
  }
}

```

    2. Save your changes.

### Task 2: Implement the Renderer
It is necessary to implement the renderer for the PlaneInfo control. The renderer follows the naming standards for renderer.
#### Steps
  1. In the _control_ folder of the _fullscreen_ (or _controlextend_) project, create a new file named **PlaneInfoRenderer.js**.
    1. Perform this step as shown in a previous exercise.
  2. In the PlaneInfoRenderer.js file, create a custom control named **PlaneInfoRenderer** by extending the base sap.ui.core.Renderer, assign the extended object to a variable named PlaneInfoRenderer, and return the created object to the caller.
    1. Use the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

sap.ui.define([
    "sap/ui/core/Renderer"
  ],

    function (Renderer) {
      "use strict";

      var PlaneInfoRenderer = Renderer.extend("student.com.sap.training.advancedsapui5.fullscreen.control.PlaneInfoRenderer");
      return PlaneInfoRenderer;
    }
);

```

  3. To enable the incremental DOM-like API, set the apiVersion of the PlaneInfoRenderer object to **2**.
    1. Add the following code before the return PlaneInfoRenderer statement :
Code Snippet
Copy codeSwitch to dark mode

```

1

PlaneInfoRenderer.apiVersion = 2;

```

  4. Add a function render to the PlaneInfoRenderer object created in step 2. The function takes two arguments. Name the first argument **oRm**. It will contain a reference to the RenderManager at runtime. Name the second argument **oControl**. This variable will contain a reference to the control that the renderer should render. Add code to the render function to render the control. The HTML table control should have three rows of data from the PlaneInfo control properties: seatsMax and seatsOcc. Do not put in the icons at this point (as seen at the beginning of the exercise). Now, save your changes.
Hint
The table being rendered is an HTML table, not an SAPUI5 table. The data from the PlaneInfo control can be accessed from the oControl object passed in using the automatically generated getter methods.
    1. Use the RenderManager passed in to write out an opening div and write the control data for the oControl object passed in. Use the openStart function of the RenderManager.
    2. Write an HTML table control with three rows of data from the PlaneInfo control properties: seatsMax and seatsOcc. Do not put in the icons at this point (as seen at the beginning of the exercise). Use the openStart, openEnd, close, attr, and text functions of the RenderManager.
    3. Close the table and the div. Use the close function of the RenderManager.
    4. The implementation should look like the following code:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213141516171819202122232425

PlaneInfoRenderer.render = function(oRm, oControl) {
  oRm.openStart("div",oControl);
  oRm.openEnd();
  oRm.openStart("table");
  oRm.attr("align", "center");
  oRm.openEnd();
  oRm.openStart("tr");
  oRm.openEnd();
  oRm.openStart("td");
  oRm.openEnd();
  oRm.text(" "+oControl.getSeatsMax());
  oRm.close("td");
  oRm.close("tr");
  oRm.openStart("tr");
  oRm.openEnd();
  oRm.openStart("td");
  oRm.openEnd();
  oRm.text(" "+oControl.getSeatsOcc());
  oRm.close("td");
  oRm.close("tr");
  oRm.close("table");
  oRm.close("div");

}

```

Note
For less code, you could use method chaining.
    5. Save your changes.

### Task 3: Add the PlaneInfoRenderer to the PlaneInfo Control
#### Steps
  1. Open the PlaneInfo.js file and add a reference to the new PlaneInfoRenderer to the implementation.
    1. Open the PlaneInfo.js file located in the _control_ folder of your project.
    2. Update the code as follows:
Code Snippet
Copy codeSwitch to dark mode

```

12345678

sap.ui.define([
    "sap/ui/core/Control",
    "student/com/sap/training/advancedsapui5/fullscreen/control/PlaneInfoRenderer"
  ],

    function (Control, PlaneInfoRenderer) {
      "use strict";

```

  2. Add an attribute renderer to the implementation and assign the PlaneInfoRenderer reference to it.
    1. Add the following code after the metadata definition:
Code Snippet
Copy codeSwitch to dark mode

```

12

,
renderer: PlaneInfoRenderer

```

    2. Save your changes.

### Task 4: Add the PlaneInfo Control to the Application
#### Steps
  1. Open the i18n.properties file and add the following key-value pair. Now, save your changes.
#### Key-value Pair within the i18n.properties File
| Key  | Value  |
| --- | --- |
| planeInfo  | Plane Infos  |
    1. Perform this step as shown in a previous exercise.
  2. Open the Flights.view.xml file. Before the last Column element, add a new mobile-enabled Column element with the following attributes to the columns aggregation:
#### Attribute-value Pairs for the Column Element within the Flights.view.xml File
| Attribute  | Value  |
| --- | --- |
| id  | **flplaneinfo**  |
| minScreenWidth  | **Tablet**  |
| demandPopin  | **true**  |
| hAlign  | **Center**  |
    1. Open the Flights.view.xml file.
    2. Add the following code between flseatocccolumn and flbooking elements:
Code Snippet
Copy codeSwitch to dark mode

```

123

<Column id="flplaneinfo" minScreenWidth="Tablet" demandPopin="true" hAlign="Center">

</Column>

```

  3. Add a sap.m.Text element with the following attribute and value to the newly created Column element:
#### Attribute-value Pair for the Text Element within the Flights.view.xml File
| Attribute  | Value  |
| --- | --- |
| id  | **flplaneinfotext**  |
| text  | **{i18n >planeInfo}**  |
    1. Add the following code inside the new Column definition :
Code Snippet
Copy codeSwitch to dark mode

```

1

<Text id="flplaneinfotext" text="{i18n>planeInfo}"/>

```

  4. Before the HoverButton element of the cells aggregation, add a PlaneInfo element with the following attributes and values. Bear in mind that PlaneInfo is placed in a project specific namespace. Now, save your changes.
#### Attribute-value Pairs for the PlaneInfo Element within the Flights.view.xml File
| Attribute  | Value  |
| --- | --- |
| seatsMax  | **{Seatsmax}**  |
| seatsOcc  | **{Seatsocc}**  |
| id  | **planeInfo1**  |
    1. Add the following code in the cells aggregation, before the HoverButton definition:
Code Snippet
Copy codeSwitch to dark mode

```

1234

<cust:PlaneInfo id="planeInfo1"
      seatsMax="{Seatsmax}"
      seatsOcc="{Seatsocc}"
/>

```

    2. Save your changes.
  5. Run the application.
Note
Be aware that since we are not testing the application in a real SAP Fiori environment you will get errors in the console if you use Dev Tools to debug your application. Please, dismiss any message about resource preload.
    1. Perform this step as shown in a previous exercise.
  6. Verify that the row in the Flights table now shows the PlaneInfo control with the three pieces of data. If the control does not display or the application fails to load, open Chrome DevTools and look at the HTML code generated.
![Resulting Application Plane Infos with both numbers.](../images/553a80bdca5a4e02.png)
    1. Choose a carrier in the Carriers table.
    2. Verify that the row in the Flights table now shows the PlaneInfo control with the three pieces of data.
    3. Adjust the _PlaneInfoRenderer.js_ file as needed to get the HTML correct. Use Chrome DevTools as needed to look at the HTML code that is inserted by the custom control. This may take several attempts.

### Task 5: Add Icons to the PlaneInfo Control
#### Steps
  1. Open the PlaneInfoRenderer.js file.
    1. Perform this step as shown in a previous exercise.
  2. To show clearly what the numbers mean, add icons before the numbers of the PlaneInfo table. Show the listed icons at the appropriate position. Use the icon function of the RenderManager. It takes the URL of the icon as a parameter. The URL prefix for the SAP icons is sap-icon://.
#### Icons within the PlaneInfoRenderer.js File
| Icon  | Infront Of  |
| --- | --- |
| **person-placeholder**  | seatsMax  |
| **suitcase**  | seatsOcc  |
    1. Open the PlaneInfoRenderer.js file.
    2. Add the following code before oRm.text(" "+oControl.getSeatsMax()); :
Code Snippet
Copy codeSwitch to dark mode

```

1

oRm.icon("sap-icon://person-placeholder");

```

    3. Add the following code before oRm.text(" "+oControl.getSeatsOcc()); :
Code Snippet
Copy codeSwitch to dark mode

```

1

oRm.icon("sap-icon://suitcase");

```

  3. Run the application.
    1. Perform this step as shown in a previous exercise.
  4. Verify that the icons are appearing on the _PlaneInfo_ control. You may need a few spaces after the icon to move the numbers away from the icon slightly.
![Resulting application Plane Infos with both numbers and icons.](../images/d66b85cc1984a831.png)
    1. Choose a carrier in the Carriers table.
    2. Verify that the icons are appearing on the _PlaneInfo_ control.
  5. You can now close the browser tab in which your application is running.
  6. Since we will further develop your fullscreen project in a following exercise, you can save the current state of the project by downloading it. Select the _fullscreen_ project and from the context menu, choose _Download_.
