# Modularizing SAPUI5 Applications

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/defining-and-using-modules_ab210fc5-edce-4dfb-920e-4ec152db33f0*

Objective
After completing this lesson, you will be able to modularize SAPUI5 applications
## Modularization
The SAPUI5 framework provides built-in support for application modularization. That is, instead of defining and loading a large bundle of JavaScript code, an application can be split into smaller parts that can then be loaded at runtime when they are needed.
Watch the video to understand important features of this modularization concept.
For details, see the [API Reference](https://ui5.sap.com/#/api) in the _Demo Kit_ and the example in the following section.
## Module Definition
As mentioned previously, an SAPUI5 module is defined by calling the sap.ui.define method. The implementation made via sap.ui.define determines the so-called export value of a module. This export value is typically a JavaScript object that represents the value of a module from a usage perspective. Usually, the export value is determined via a function.
The typical use of sap.ui.define is a single top level call to this method in a JavaScript file. When a module is requested for the first time, the JavaScript file is loaded and executed, which in turn executes the top level call to sap.ui.define.
![Sample simple module definition, as described in the following text.](../images/d3a9d6a85eed2755.png)
The figure, _Simple Module Definition_ , shows a simple example of a module definition. In the index.js file, which is stored in the webapp folder of the project, the sap.ui.define method is called.
The sap.ui.define method can be passed an array. Each entry in this dependencies array then represents the name of another module on which the currently defined module depends. The name of a used SAPUI5 module as well as the name of the currently defined module consists of a non-empty sequence of name segments. The individual segments are separated by a forward slash ('/').
The module defined in the example uses the sap.m.Text control in its implementation. Thus it is dependent on the corresponding module through which the sap.m.Text control is implemented. This module is named sap/m/Text and is added to the dependencies array.
Note
SAPUI5 controls are consistently implemented as modules. The module names are derived from the class names of the controls by replacing the dot in the class name ('.') with a forward slash ('/'). In the [API Reference](https://ui5.sap.com/#/api) in the _Demo Kit_ , you can find the module name belonging to a control in the header of the respective control documentation.
All modules listed in the dependencies array are loaded before the export value of the currently defined module is determined. For this purpose, the export value of each required module is passed as a parameter to a factory function, which in turn is handed over to the sap.ui.define method. The factory function is called as soon as all required modules have been loaded. The order of the factory function parameters matches the order of the modules in the dependencies array. The names for the parameters of the factory function are arbitrary. As a rule, however, the last name segment from the module name is used as parameter name.
In the example shown, the factory function passed to sap.ui.define has a parameter named Text. This parameter is used to reference the export value of the sap/m/Text module from the dependencies array. If the module defined in the example is used for the first time, the factory function is only called when the sap/m/Text module is available in the browser. In the implementation of the factory function, the Text control can then be accessed via the Text parameter.
Usually, the factory function returns a value such as a JavaScript object via the return statement. This value then represents the export value for the module. In the example shown, no value is returned. For simplicity, only the text _Hello World_ is added to a UI area via the Text control.
Note
The use strict; literal expression used in the implementation of the factory function was introduced in JavaScript 1.8.5 (ECMAScript 5). It instructs the browser to execute the code in what is called strict mode. Strict mode helps identify potential coding problems early in the development cycle. For example, it means ensuring that variables are declared before they are used. Strict mode helps avoid common JavaScript pitfalls and is therefore a good practice to use.
## Loading of Modules
In the bootstrap script shown in the figure, _Asynchronous Loading of Modules_ , the default bootstrap file sap-ui-core.js is loaded from the resources folder. By default, SAPUI5 therefore loads all modules relative to this folder. This works for modules that are part of the SAPUI5 delivery. However, it fails for those modules that are created by the developer in an SAPUI5 project.
![Sample configuration code, as described in the following text.](../images/3f8a784f6c6ca7ee.png)
### Configuration Option resourceroots
Using the resourceroots configuration option, it is possible to redirect requests for application-specific modules to the corresponding Web application. To set this configuration option, for example, the attribute data-sap-ui-resourceroots can be added to the bootstrap script. The value of the configuration option is a map of resource locations keyed by a corresponding module Id prefix.
In the example shown, the module Id prefix sap.training.exc is assigned to the current folder, that is, the folder that contains the file in which the bootstrap script shown is located. In the example, this is the webapp folder.
The module discussed above is implemented in a file named index.js, which is stored in the webapp folder. With the module Id prefix defined here, this results in the following Id to request this module:
XML
Copy codeSwitch to dark mode

```

1

sap/training/exc/index

```

Here sap/training/exc points to the webapp folder, and in this folder is the file index.js. The file extension .js is not specified and is automatically added during loading.
### Configuration Option async
For SAPUI5 libraries like sap.ui.core or sap.m there are so-called library preload files named library-preload.js. These preload files contain all modules of the respective library.
Adding the attribute data-sap-ui-async=true to the bootstrap script enables the module loader to load single modules as well as library preload files asynchronously.
### Configuration Option onInit
The attribute data-sap-ui-onInit can be used in the bootstrap script to define code that is executed after initialization. In doing so, modules are indicated by the prefix module:.
In the example shown, the sap/training/exc/index module discussed above is loaded and executed (asynchronously) after the framework has been initialized.
## Work with Modules
### Business Scenario
In this exercise, you will move the logic for creating and placing the **Hello World** Text UI element that you implemented in the previous exercise out of the HTML page and into a separate module. You will then call this module declaratively from the index.html page.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/2_bootstrapping**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/3_modules**  |
### Task 1: Delete the <script> Tag
#### Steps
  1. Make sure that the index.html page is open in the editor.
  2. Delete the <script> tag used to create and place the **Hello World** Text UI element in the file.
    1. Delete the following lines:
JavaScript
Copy codeSwitch to dark mode

```

1234

<script>
  var oText = new sap.m.Text({text: "Hello World"});
  oText.placeAt("content");
</script>

```

#### Result
The <head> tag of the HTML page should now look like this:
![Screenshot of the updated head code.](../images/31b1a44543851399.png)
### Task 2: Implement a Module
#### Steps
  1. Create a new file named index.js in the webapp folder.
    1. Open the context menu for the webapp folder in the project structure.
    2. Select _New File_.
    3. In the field that appears, type **index.js** and press _Enter_.
#### Result
The index.js file is created and displays in the editor.
  2. Add the following code to the index.js file to define a module through which the **Hello World** Text UI element is created and placed on the HTML page:
JavaScript
Copy codeSwitch to dark mode

```

123456

sap.ui.define(["sap/m/Text"], function (Text) {
  "use strict";

  new Text({ text: "Hello World" }).placeAt("content");

});

```

#### Result
The index.js file should be implemented as follows:
![Screenshot of the final index.js file.](../images/a9898389ebdf4c79.png)
### Task 3: Load the Module Declaratively
#### Steps
  1. Make sure the index.html page is open in the editor.
  2. Add the following attributes to the bootstrap script:
XML
Copy codeSwitch to dark mode

```

123

data-sap-ui-async="true"
data-sap-ui-onInit="module:sap/training/exc/index"
data-sap-ui-resourceroots='{"sap.training.exc": "./"}'

```

Note
The added configuration tells SAPUI5 that resources in the _sap.training.exc_ namespace are in the same directory as index.html. The namespace is used to initially load the index.js module. For performance reasons, SAPUI5 is enabled to load modules and library-preload files asynchronously.
    1. The <head> tag of the HTML page should now look like this:
![Screenshot of the updated head tag.](../images/cdd70b3d4b97b974.png)
  3. Test run your application by starting it from the SAP Business Application Studio.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the **Hello World** text of the sap.m.Text UI element is displayed on the HTML page.

[Continue to quiz](https://learning.sap.com/courses/developing-uis-with-sapui5-1/modularizing-sapui5-applications)
