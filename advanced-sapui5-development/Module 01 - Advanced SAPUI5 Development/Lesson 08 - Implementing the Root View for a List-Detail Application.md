# Implementing the Root View for a List-Detail Application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/implementing-the-root-view-for-a-list-detail-application*

Objective
After completing this lesson, you will be able to implement the root view of a List-Detail application.
## The Flexible Column Layout
As described in the previous lessons, an application should implement a root view - usually named App - that acts as central starting point of the view composition.
Watch this video to know more about implementing the App View for a List-Detail application.
Settings
### App View Xml
The following figure will show you the implementation of the App.view.xml file.
![An App.view.xml file defining a FlexibleColumnLayout control](../images/ff2e57dc3e7dd91d.png)
### App View Controller
As described in the video, a model is used to control the behavior of the _sap.f.FlexbileColumnLayout_ control. It is a very common practice to instantiate and initialize the model in the onInit function of the App view controller.
![The app controller defining a JSONModel to manage the FlexibleColumnLayout](../images/71cf045301b134d2.png)
## Implement the root view of a List-Detail application
### Business Example
In this unit exercises, you learn how to implement a List-detail Application with SAPUI5. You'll start with a full-screen application and change it to a list detail one.
First, you'll implement the root view of the application.
### Prerequisites
Before you start this exercise, you should have downloaded the prepared files from Github: <https://github.com/SAP-samples/sapui5-development-advanced-learning-journey>..
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Task 1: Import and Review the Base List-Detail Application
#### Steps
  1. Import the listdetail.tar project into your Business Application Studio.
    1. Locate the listdetail.tar file in your training files.
    2. Log into the training SAP Business Application Studio as shown in a previous training.
    3. Select the menu _File_ → _Open Folder..._.
    4. Select or Enter the **/home/user/projects/** folder and choose _OK_.
    5. Select the menu _File_ → _Import Project.._.
    6. Select the listdetail.tar file and choose _OK_.
  2. Preview the application. For the moment it is the same as the previous full-screen application
    1. Right-click on the webapp folder and choose _Preview Application_.
    2. Select _start local..._
A list of carriers should be displayed.

### Task 2: Define the Main View of the Application
#### Steps
  1. Open the Application main view and add an sap.f.FlexibleColumnLayout element inside the App element with the listed properties and values:
| Attribute  | Value  |
| --- | --- |
| id  | **layout**  |
| layout  | **{mainView >/layout}**  |
| backgroundDesign  | **Translucent**  |
    1. Open the App.view.xml file in the _view_ folder of your project.
    2. Add the sap.f namespace with the prefix f to the App.view.xml file. Add following code after xmlns="sap.m":
Code Snippet
Copy codeSwitch to dark mode

```

1

xmlns:f="sap.f"

```

    3. Add an sap.f.FlexibleColumnLayout element inside the App element with the given attribute-value pairs :
Code Snippet
Copy codeSwitch to dark mode

```

123456

<f:FlexibleColumnLayout
  id="layout"
  layout="{mainView>/layout}"
  backgroundDesign="Translucent">
</f:FlexibleColumnLayout>

```

    4. Save your changes. Your code should now look like the following:
![Screenshot of the resulting App view XML code.](../images/dddbe923f3f55d2b.png)

### Task 3: Implement the Application Controller for Flexible Column Layout
In this task, you implement the controller of the _App_ view to link the JSON model for layout to the Application.
#### Steps
  1. Open the App.controller.js file. Add sap/ui/model/JSONModel to the namespace.
    1. Open the App.controller.js file located in the _controller_ folder of your project.
    2. Update the code as follows :
Code Snippet
Copy codeSwitch to dark mode

```

12345678

sap.ui.define(
    [
        "sap/ui/core/mvc/Controller",
        "sap/ui/model/json/JSONModel"
    ],
    function(BaseController, JSONModel) {
...

```

  2. Implement the onInit function. Create an JSON-Model with an attribute layout and assign the created Model to the App view.
    1. Add the following code into the onInit function:
Code Snippet
Copy codeSwitch to dark mode

```

123456

  var oViewModel = new JSONModel({
    layout : "OneColumn"
  });

  this.getView().setModel(oViewModel, "mainView");

```

#### Result
Note
You won't be able to test the changes yet. Your application should still work as before.
