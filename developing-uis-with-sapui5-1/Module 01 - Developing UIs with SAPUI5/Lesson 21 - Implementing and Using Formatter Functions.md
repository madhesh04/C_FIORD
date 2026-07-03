# Implementing and Using Formatter Functions

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/implementing-and-using-formatter-functions_c7f9608b-de6f-44a4-b022-98cab121a6d2*

Objective
After completing this lesson, you will be able to implement and use formatter functions to convert model data into an external format
## Creating Formatter Functions
SAPUI5 provides two different options to convert model data to an external format for visual representation: data types and formatter functions.
While data types provide the possibility to format, parse and validate data, formatter functions allow one-way conversion only.
A formatter function has a single parameter, which is the value which needs to be formatted to an external representation.
A formatter function can be used not only to format a value, but also to do type conversion or calculate results from a given value.
Note
When using formatter functions, the binding is automatically switched to "one-way". So you can’t use a formatter function for "two-way" scenarios.
Formatter functions can be defined in a separate module or locally in a view controller.
Note
It is recommended to use a separate module file that groups the formatters and makes them globally available in the application.
![Sample formatter.js code, as described in the following text.](../images/570137b107e7d2b1.png)
The coding example in the figure _Defining a Formatter Function_ shows the definition of a formatter function called classText. It is created in a separate module that is implemented in the formatter.js file. The classText formatter translates keys used in the model data into texts that are understandable to the user. For example, for the key value "Y", the text "Economy Class" is returned.
## Using Formatter Functions
![Sample code highlighting the formatter function, as described in the following text.](../images/975ab86b22cf974c.png)
The figure, _Using a Formatter Function_ , shows how a formatter function defined in a separate module can be used in an XML view.
To do this, it must first be ensured that the module containing the formatter function is loaded. This is achieved by requiring the formatter module by its module name in the <mvc:View> tag, as shown in the figure.
The loaded module is assigned to the alias formatter. The name of this alias is arbitrary, the crucial thing is that the alias can be used as a variable in the binding.
To specify the formatter function in the binding, the complex binding syntax is used. The model property to be formatted is specified via the path property, and the formatter function is assigned to the formatter property via the following syntax:
XML
Copy codeSwitch to dark mode

```

1

<alias of the formatter module>.<name of the formatter function>.

```

So in the example, the content of the Class model property is passed to the classText formatter function . The string returned by this formatter function is then displayed on the UI via the Text control.
Note
In addition to custom formatter functions, you can also use predefined formatter functions for standard use cases, such as sap/base/strings/formatMessage.
## Implement a Formatter Function
### Business Scenario
In the booking table, the booked class of a flight is currently displayed using the values C, Y, and F respectively. In this exercise, you will implement a formatter function to convert these technical values from the Class model property into a meaningful text for the user. For C, the text _Business Class_ , for Y, the text _Economy Class_ , and for F, the text _First Class_ should be set. Then you will integrate the implemented formatter function into the data binding of the corresponding table column in order to format the flight class accordingly.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/14_data_types**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/15_formatters**  |
### Task 1: Create the Formatter Function
#### Steps
  1. Create a new file named formatter.js in the subfolder model of the webapp folder.
    1. Open the context menu for the webapp/model folder in the project structure.
    2. Select _New File_.
    3. In the field that appears, type **formatter.js** and press _Enter_.
#### Result
The formatter.js file is created and displays in the editor.
  2. Add the following code to the formatter.js file to create a formatter function named classText that transforms passed values from the model into meaningful texts.
JavaScript
Copy codeSwitch to dark mode

```

123456789101112131415161718192021

sap.ui.define([], function () {
  "use strict";

  return {

    classText: function (sClass) {
      switch (sClass) {
        case "C":
          return "Business Class";
        case "Y":
          return "Economy Class";
        case "F":
          return "First Class";
        default:
          return sClass;
      }
    }

  };

});

```

#### Result
The formatter function should be implemented as follows:
![Screenshot of the formatter function, as described in the text.](../images/82b1c5885620221d.png)
### Task 2: Use the Formatter Function for the Display of the Flight Class
#### Steps
  1. Open the Overview.view.xml file from the webapp/view folder in the editor.
  2. Add the following attribute to the <mvc:View> tag:
XML
Copy codeSwitch to dark mode

```

1

core:require="{formatter: 'sap/training/exc/model/formatter'}"

```

Note
The additional attribute ensures that the module with the classText formatter function is loaded and assigns it to the formatter alias.
#### Result
The <mvc:View> tag should now be similar to the following:![XML code, highlighting the formatter function.](../images/ef6f6e9690a800f3.png)
  3. Adapt the data binding for the flight class column (model property Class) in the booking table as follows to transfer the content of the Class model property to the external representation via the formatter function:
| **Old**  | **New**  |
| --- | --- |
|  XML Copy codeSwitch to dark mode
```
1
<Text text="{Class}"/>
```
 |  XML Copy codeSwitch to dark mode
```

1234

<Text text="{
  path: 'Class',
  formatter: 'formatter.classText'
}"/>
```
 |
#### Result
The data binding for the flight class column in the booking table should now look like this:![XML code, highlighting the <Text> tag.](../images/7326e2672d126fba.png)
  4. Test run your application by starting it from the SAP Business Application Studio.
Make sure that the technical values from the data model (C, Y, or F) are no longer displayed in the flight class column of the booking table, but the meaningful texts from the formatter function.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the component works as expected.
