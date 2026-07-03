# Creating Control and Component Libraries

*Source: https://learning.sap.com/courses/advanced-sapui5-development/creating-control-and-component-libraries_de1fb2af-9117-471a-b160-505770bdaf85*

Objective
After completing this lesson, you will be able to recognize the structure of a custom library.
## Implementing Custom Libraries
Creating reusable building blocks is necessary to increase development speed and provide the same intuitive and consistent experience across the enterprise.
A custom library provides reuse functionality and UI controls without copy and paste.
This list enumerates the basic advantages of control libraries:
  * Reuse controls/functionality in different applications
  * Provide automatic support for theming
  * Provide automatic support for right-to-left languages
  * Can be installed on the ABAP-platform
  * Can be installed in the SAP Business Technology Platform

Let's now look at the structure of a custom library together with additional information on library.js and manifest.json.
Settings
## Encapsulate Controls in a Custom Library
The characteristics of controls in a custom library are as follows:
  * Multiple controls can be added to a library
  * The full qualified classname must match the one defined in the library.js
  * Standard JavaScript can be used
  * Defined as a JavaScript module with name, dependencies and factory functionsap.ui.define([...], function() {...});

At the end, you must implement the controls that are going to be encapsulated in the UI library.
![N/A](../images/399bcb7f0e3f3e77.png)
When you are finished with the development, you have to deploy the UI library project to your on-premise or cloud system.
After deployment, the UI library shows up in transaction SICF.
![N/A](../images/a8cd77768dec227a.png)
## Implement a Reusable UI Library
### Business Example
In this exercise, you will build a reusable UI Library and you will use this library in the _fullscreen_ application.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You should have completed the last exercise on custom controls.
Note
You can import the solutions with the 3-customcontrol.tar file.
### Task 1: Create a Yarn Workspace
In order to test the use of a library without having to deploy this library and the project into a backend server, we can use yarn workspaces.
#### Steps
  1. Log into your SAP Business Application Studio.
    1. Perform this step as done in a previous exercise.
  2. Install the following npm packages (globally) to your development environment : yarn, yoman and generator-ui5-library.
    1. Open a new terminal window.
Hint
You can use the _Terminal_ → _New Terminal_ menu option.
    2. Globally install the yarn package by executing the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

npm install -location=global yarn

```

    3. Globally install the yoman package by executing the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

npm install -location=global yo

```

    4. Globally install the generator-ui5-library package by executing the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1

npm install -location=global generator-ui5-library

```

  3. Create a new _library_test_ folder in your _projects_ folder and add a _packages_ sub-folder and a package.json file with the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

{
 "name": "library_test",
 "version": "1.0.0",
 "description": "",
 "keywords": [],
 "author": "",
 "license": "ISC",
 "private": true,
 "workspaces": [
     "packages/*"
 ]
}

```

    1. Make sure you are in your projects folder.
Hint
To be absolutely sure, you can use the _View_ → _Command Palette_ menu option and search for the File: Open Folder... command. Then select your _projects_ folder and select _Go_.
    2. Click into the blank space in the _EXPLORER_ , to make sure you have not selected an existing project, and create a new folder by selecting the _New Folder..._ icon.
    3. Enter **library_test** as the folder name and press the Enter key (on your keyboard).
    4. Make sure that your new folder is selected and click again on the _New Folder..._ icon.
    5. Enter **packages** as the folder name and press the Enter key (on your keyboard).
    6. Select the _library_test_ folder (it should be underlined) and select the _New File..._ icon.
    7. Enter **package.json** as the file name and press the Enter key (on your keyboard). You should now see the following structure:
![Screenshot of the project structure with test-workspace folder.](../images/752b2b03f7b8e73a.png)
    8. Enter the given code in the package.json file.

### Task 2: Create the Reusable UI Library
#### Steps
  1. Generate a new library inside the _packages_ folder using the yoman ui5-library command and following information:
#### Library Creation Wizard
| Question  | Answer  |
| --- | --- |
| How do you want to name this library?  | **uicontrols**  |
| Which namespace do you want to use?  | **student.com.sap.training.advancedsapui5**  |
| Which framework do you want to use?  | **SAPUI5**  |
| Which framework version do you want to use?  | **1.126.0**  |
| Who is the author of the library?  | keep default value  |
| Would you like to create a new directory for the library?  |  **Y** (Yes)  |
Note
If you are asked to migrate your library project, go and start the migration.
    1. Select the new _packages_ folder and select the _Open in Integrated Terminal_ option in the contextual menu.
    2. Enter the following command: yo ui5-library.
    3. Enter **uicontrols** for the library name.
    4. Enter **student.com.sap.training.advancedsapui5** for the namespace.
    5. Select **SAPUI5** for the framework.
    6. Enter **1.126.0** as framework version.
    7. Keep the default values for author and create a new directory.
  2. If you prefer to display the whole folder tree structure, you can change the settings of your Explorer and deselect the compact folder option.
![Screenshot of the BAS settings for Explorer.](../images/ab10355a39162827.png)
    1. Go to the _File_ → _Preferences_ → _Settings_ menu option.
    2. Select _Features/Explorer_ in the left pane.
    3. Deselect the _Compact Folders_ option.
    4. Close the _Settings_ tab.
  3. Copy the HoverButton.js, PlaneInfo.js, and PlaneInfoRenderer.js files from the _fullscreen_ (or _customcontrol_) project into the _uicontrols_ folder. Change the namespace of the HoverButton.js, PlaneInfo.js and PlaneInfoRenderer.js files from student.com.sap.training.advancedsapui5.fullscreen.control to **student.com.sap.training.advancedsapui5.uicontrols**. Be sure to update all of the namespace references.
    1. Open the _control_ folder of the _fullscreen_ (or _customcontrol_) project and select the HoverButton.js, PlaneInfo.js, and PlaneInfoRenderer.js files.
    2. Press _Ctrl + C_ (on your keyboard) to copy the selected files.
    3. Select the _uicontrols_ folder of the new library and press _Ctrl + V_ on your keyboard.
Note
You'll find this folder in the library_test>packages>student.com.sap.training.advancedsapui5.uicontrols>src>student>com>sap>training>advancedsapui5 folder.
    4. Open the HoverButton.js file and change the namespace like in the following code:
Code Snippet
Copy codeSwitch to dark mode

```

123456789

sap.ui.define([
  "sap/m/Button"
],

  function (Button) {
  "use strict";

  return Button.extend("student.com.sap.training.advancedsapui5.uicontrols.HoverButton", {

```

    5. Open the PlaneInfo.js file and adjust the namespace and the referenced namespace for _PlaneInfoRenderer_. Use the following code:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910

sap.ui.define([
  "sap/ui/core/Control",
  "student/com/sap/training/advancedsapui5/uicontrols/PlaneInfoRenderer"
],

  function (Control, PlaneInfoRenderer) {
    "use strict";

    return Control.extend("student.com.sap.training.advancedsapui5.uicontrols.PlaneInfo", {

```

    6. Open the PlaneInfoRenderer.js file and update the namespace.
Code Snippet
Copy codeSwitch to dark mode

```

123456789

sap.ui.define([
  "sap/ui/core/Renderer"
],

  function (Renderer) {
    "use strict";

    var PlaneInfoRenderer = Renderer.extend("student.com.sap.training.advancedsapui5.uicontrols.PlaneInfoRenderer");

```

  4. Extend the library.js file. Add the following entries to the controls list:
#### New Controls for the initLibrary Function within the library.js File
| Parameter  | Value  |
| --- | --- |
| controls  |  Code Snippet Copy codeSwitch to dark mode
```

123

"student.com.sap.training.advancedsapui5.uicontrols.PlaneInfo",
"student.com.sap.training.advancedsapui5.uicontrols.HoverButton",
"student.com.sap.training.advancedsapui5.uicontrols.PlaneInfoRenderer"
```
 |
    1. Open the library.js file.
    2. Add the three controls to the control list. Your code should look like the following:
![Screenshot of the resulting library.js code](../images/3ef58fdbe0648ae6.png)

## Custom Library Usage
A dependency is defined in the _manifest.json_ file of the application that uses the UI library. The dependency triggers the get response of the _library.js_ file from the dependent UI library.
![Sample manifest.json file with the library added to the dependencies.](../images/04f9b0100c4d05be.png)
## Use a custom library
In this exercise you will learn how to use the control library created in the previous exercise.
### Prerequisites
You need to have completed previous exercise on library creation. If not, you can import the solution.
### Task 1: Copy and Adapt the fullscreen Application
In the next step, you must copy and change the _fullscreen_ application to consume the created library.
#### Steps
  1. Copy the whole _fullscreen_ (or _customcontrol_) project folder inside the _packages_ folder.
Note
The copy can take some time.
    1. Select the _fullscreen_ (or _customcontrol_) project folder and press _Ctrl + C_ (on your keyboard) to copy the selected files.
    2. Select the _packages_ folder under _library_test_ and press _Ctrl + V_ on your keyboard.
  2. Open the manifest.json file of the _fullscreen_ project and add a dependency to the student.com.sap.training.advancedsapui5.uicontrols library. Then save your changes.
    1. Open the manifest.json file of your copied _fullscreen_ project.
    2. Navigate to the sap.ui5 configuration.
    3. Add the dependency to the student.com.sap.training.advancedsapui5.uicontrols library in the dependencies configuration section like in the following code:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910

"sap.ui5": {
  "flexEnabled": false,
  "dependencies": {
    "minUI5Version": "1.102.1",
    "libs": {
      ...
      "student.com.sap.training.advancedsapui5.uicontrols" : {}
    }
  },

```

    4. Save your changes.
  3. Change the namespace of the cust XML alias in the Flights.view.xml file to the new student.com.sap.training.advancedsapui5.uicontrols namespace.
    1. Open the Flights.view.xml file, located in the _view_ folder, with the Code Editor and change the namespace of the cust xml alias to student.com.sap.training.advancedsapui5.uicontrols. Your code should look like the following:
Code Snippet
Copy codeSwitch to dark mode

```

123456

<mvc:View controllerName="student.com.sap.training.advancedsapui5.fullscreen.controller.Flights"
    xmlns:mvc="sap.ui.core.mvc" displayBlock="true"
    xmlns="sap.m" xmlns:l="sap.ui.layout"
    xmlns:cust="student.com.sap.training.advancedsapui5.uicontrols">

```

    2. Save your changes.
  4. Add the uicontrols library reference to the package.json file.
    1. Open the package.json file of the _fullscreen_ copied project.
    2. Add "uicontrols":"1.0.0" to the "dependencies":{} section as in the following code:
Code Snippet
Copy codeSwitch to dark mode

```

1234

"main": "webapp/index.html",
"dependencies": {
  "uicontrols":"1.0.0"
},

```

  5. Delete the _control_ folder of your copied _fullscreen_ project.
    1. Select the library_test/packages/fullscreen/webapp/control folder
    2. Press _Delete_.
  6. Resolve local dependencies by executing **yarn** command in the _library_test_ workspace.
    1. Select the _library_test_ folder and choose _Open in Integrated Terminal_ from the contextual menu.
    2. Enter the **yarn** command and press the Enter key (on your keyboard).
  7. Test your application in Google Chrome. Check also with Chrome DevTools to ensure that the new library is used.
Note
Be aware that since we are not testing the application in a real SAP Fiori environment you will get errors in the console if you use Dev Tools to debug your application. Please, dismiss any message about resource preload.
    1. Preview your fullscreen application, as shown in previous exercises.
    2. In the displayed application, choose a carrier from the list of available carriers.
![Screenshot of the resulting application with list of carriers.](../images/60be7202d52c46a5.png)
    3. The carrier details and the available flights are displayed as they are shown in the following figure.
![Resulting application screen with selected carrier details and list of flights.](../images/a327786c01b951b0.png)
    4. Press F12 (on your keyboard) to access Chrome DevTools. Select the _Sources_ tab in Chrome DevTools. You will see that the new library is used by the application.
![Screenshot of the Sources folder of the Chrome DevTools.](../images/265923643e79a9b7.png)

[Continue to quiz](https://learning.sap.com/courses/advanced-sapui5-development/working-with-ui5-controls)
