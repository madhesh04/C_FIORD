# Adapting Applications to Different Device Types

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/adapting-applications-to-different-device-types_a0e82bfa-56b0-4288-9fd3-eb8b7cc14b97*

Objective
After completing this lesson, you will be able to use a device model to adapt applications to different device types
## Controls with Built-In Device Adaptation
SAPUI5 comes with several controls that are already able to react to the available screen real estate and resolution by themselves. Some require particular properties to be set, and with some, everything just works out of the box.
Such controls with built-in device adaptation are for example sap.m.SplitApp, sap.m.ResponsivePopover, sap.m.OverflowToolbar, and sap.m.PullToRefresh.
The forms sap.ui.layout.form.SimpleForm and sap.ui.layout.form.Form can also adapt to the available screen size. It is recommended to set the sap.ui.layout.form.ColumnLayout for them, as its responsiveness allows the available space to be used in the best way possible.
![XML table definition with responsive attributes for columns. Desktop and tablet display shows Customer Name, City, and Email in table format. Phone display shows Customer Name and Email in a stacked list.](../images/341bc58676c04799.png)
One control that is widely used across all kinds of different applications is sap.m.Table (also called the "Responsive Table"), which has several features you can use for device adaptation. On smaller devices, for example, you can set certain properties that will make particular columns pop in instead of being displayed as a normal column, or show and hide columns completely.
For example, you can set a minScreenWidth for the columns. This will cause columns to only show up if a certain screen width is matched. You can define this minScreenWidth in px or rem, but here you can also use the standard categories that come from the Device API (Phone, Tablet, or Desktop). Setting the additional property demandPopin to true for a column will also react to the minScreenWidth you specify. In such a case, the column will be shown as a popin on smaller screens, instead of being completely hidden.
In the example in the figure _Responsive Table_ , three columns are defined in an XML view for a sap.m.Table: Customer Name, City and Email.
No minScreenWidth attribute is set for the Customer Name column. It is therefore displayed on all device types, i.e. desktops, tablets and phones.
For the City column, the minScreenWidth="Tablet" attribute is specified. This column is therefore displayed only on tablets and desktops, but not on phones.
In the Email column, the attribute demandPopin="true" has been added to the attribute minScreenWidth="Tablet". As a result, this column does not disappear completely on phones, but is displayed there as a popin (see the figure). On tablets and desktops, the Email column is displayed in the same way as the City column.
## Device Model
### Instantiating a Device Model
Depending on the capabilities of the device running an application, the functionality and design of an application may vary.
For example, on a desktop device, it is not necessary to display a back button on a detail view in a list-detail scenario because the list and detail views are displayed simultaneously. On a phone, on the other hand, where there is navigation between list and detail view, such a back button is required. To control the visibility of the back button, a device model can be used.
A device model is based on the Device API (sap.ui.Device). This API provides information about device specifics, like the operating system along with its version, the browser and browser version, screen size, current orientation and support for specific features such as, touch event support, orientation change, and so on. For more information, see the API reference for the sap.ui.Device namespace.
With a device model, you can make most properties of the Device API available as a JSON model.
![Sample device model code in the component.js file, as described in the following text.](../images/0f32e6944caab345.png)
Typically, a device model is created in the initialization method of the component controller Component.js, as shown in the figure _Creating a Device Model in the Component Controller_.
To create a device model, dependencies to modules sap/ui/Device and sap/ui/model/json/JSONModel are added to the component controller. The device model is then instantiated in the controller's initialization method by simply passing the loaded Device module to the constructor function of the JSON model. The binding mode is set to OneWay since the device model is read-only. The device model is set as a named model (name: device) for the component.
### Using a Device Model
![Sample binding control properties, as described in the following text.](../images/e81655a5c20e4cdb.png)
After the device model has been created, the properties from the Device API (such as /system/desktop) can be used in the data binding to adapt controls to the current platform. The figure, _Binding Control Properties to Device Capabilities_ , shows some examples of how this is achieved.
Note
Do not forget to prefix the binding path with the name of the device model ("device") plus a ">" character.
If property values from the Device API are to be negated, the expression binding syntax can be used as shown in the figure.
## Adapt the Application to Different Devices
### Business Scenario
In this exercise, you will adapt the display of the panel on the Overview view to different devices: On desktops, the panel should be expanded and it should not be possible to collapse it. On all other devices, however, the panel should be initially collapsed with the option to expand it. To implement this behavior, you will create a device model.
You will also adapt the display of the columns in the two tables on a device-specific basis: you will specify which columns should be displayed on which devices and whether columns should be displayed as pop-ins instead of being hidden.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/17_expression_binding**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/18_device_adaptation**  |
### Task 1: Create a Device Model in the Component Controller
#### Steps
  1. Open the Component.js component controller from the webapp folder in the editor.
  2. Add the sap/ui/model/json/JSONModel module to the dependency array of the component controller and a corresponding parameter named JSONModel to the factory function.
#### Result
The component controller should now look like this:![the XML code, highlighting the sap/ui/model/json/JSONModel line.](../images/4fe3dd8e953aeed6.png)
  3. Now add the following code at the end of the init() initialization method to instantiate the device model and set it under the device name for the component:
JavaScript
Copy codeSwitch to dark mode

```

1234

 // set device model
var oDeviceModel = new JSONModel(Device);
oDeviceModel.setDefaultBindingMode("OneWay");
this.setModel(oDeviceModel, "device");

```

Note
Make sure to add the coding after the call of the base component's init() method.
To create the device model, the already declared Device module is passed to the constructor of JSONModel. This makes most of the SAPUI5 Device API properties available as a JSON model.
The binding mode is set to OneWay because the device model is read-only.
The model is set as a named model for the component so that it can be referenced in the data binding under the name device, as you will do in the next step.

#### Result
The init() method of the component controller should now look like this:
![The XML file, highlighting the device model code.](../images/f6762f2220e1a3ec.png)
### Task 2: Set the expandable and expanded Properties of the Panel Depending on the Device
#### Steps
  1. Open the Overview.view.xml file from the webapp/view folder in the editor.
  2. Adapt the display of the _New Customer_ panel on the view to different devices: On desktops, the panel should be expanded and it should not be possible to collapse it. On all other devices, however, the panel should be initially collapsed with the option to expand it.
To do this, bind the expanded attribute of the panel to the device model as follows:
XML
Copy codeSwitch to dark mode

```

1

expanded="{device>/system/desktop}"

```

Accordingly, bind the expandable attribute of the panel to the device model using expression binding syntax as follows:
XML
Copy codeSwitch to dark mode

```

1

expandable="{= !${device>/system/desktop} }"

```

#### Result
The _New Customer_ panel should now look like this:
![The resulting New Customer panel, highlighting the expandable and expanded code.](../images/559dd71693f5a86d.png)
### Task 3: Make the Display of the Table Columns Device Specific
#### Steps
  1. Make sure that the Overview.view.xml file is open in the editor.
  2. In the customer table, add the following attribute to the <Column> tags for _Street_ and _Post Code_ to display these columns on desktops, but hide them on tablets and phones:
XML
Copy codeSwitch to dark mode

```

1

minScreenWidth="Desktop"

```

Further, in the customer table, add the following attribute to the <Column> tag for _Country_ to display this column on tablets and desktops, but hide it on phones:
XML
Copy codeSwitch to dark mode

```

1

minScreenWidth="Tablet"

```

Finally, add the following attributes to the <Column> tag for _Email_ to display this column on tablets and desktops. On phones, the column will be displayed as a pop-in instead of being hidden:
XML
Copy codeSwitch to dark mode

```

1

minScreenWidth="Tablet" demandPopin="true"

```

#### Result
The definition of the columns of the customer table should now look like this:![The XML code, highlighting minScreenWidth attributes.](../images/1f68bbb3c3db3e84.png)
  3. In the booking table, add the following attributes to the <Column> tag for _Class_ to display this column on desktops. On tablets and phones, the column will be displayed as a pop-in instead of being hidden:
XML
Copy codeSwitch to dark mode

```

1

minScreenWidth="Desktop" demandPopin="true"

```

Finally, in the booking table, add the following attributes to the <Column> tags for _Foreign Currency Payment_ and _Cancellation Status_ to display these columns on tablets and desktops. On phones, the columns will be displayed as a pop-in instead of being hidden:
XML
Copy codeSwitch to dark mode

```

1

minScreenWidth="Tablet" demandPopin="true"

```

#### Result
The definition of the columns of the booking table should now look like this:![The XML code, highlighting minScreenWidth attributes.](../images/259d9318e3078e04.png)
  4. Test run your application by starting it from the SAP Business Application Studio.
Make sure that the _New Customer_ panel is expanded on desktops and it is not possible to collapse it. On all other devices, the panel should be initially collapsed with the option to expand it.
Note
Please note that the panel is hidden on phones because of the sapUiHideOnPhone CSS class assigned. Therefore, you should use a tablet as a comparison to the desktop.
To test the difference between desktop and tablet, you can use the device toolbar in the developer tools of the Google Chrome, Firefox or Microsoft Edge browser: Start your application and, in the developer tools (F12), call the device toolbar with the key combination _Ctrl + Shift + M_. You can use the device toolbar to select a device you want to emulate. After you select the device, you have to refresh the browser (F5), to ensure that the init() method of the component controller is called, where the device model is initialized.
Note
Do not pay attention to the errors displayed in the console when in the developer tools. This is due to some code prepared for future exercises that is then not yet complete.
Also make sure that the columns of the two tables are displayed in a device-specific way.
Note
To test the responsive behavior of the tables, it is sufficient - in contrast to the display of the panel - to change the size of the browser window. This allows you to simulate the display of the tables on desktops, tablets and phones.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the component works as expected.

[Continue to quiz](https://learning.sap.com/courses/developing-uis-with-sapui5-1/models-and-data-binding)
