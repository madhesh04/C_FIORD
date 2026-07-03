# Structuring Applications via Components

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/configuring-and-instantiating-components_f4d569d4-8c84-44f3-8d07-8dce7fd0aa31*

Objective
After completing this lesson, you will be able to implement and use components
## Components
Components are independent and reusable parts used in SAPUI5 applications. They facilitate the encapsulation of closely related parts of an application. This makes the structure of an application and its code easier to understand and to maintain.
SAPUI5 provides the following two types of components:
  * _Faceless components_ (class: sap.ui.core.Component)
Faceless components have no user interface and are used for coding when no UI elements are needed, such as for a service that provides data from a back-end system.
  * _UI components_ (class: sap.ui.core.UIComponent)
UI components extend faceless components and add rendering functionality to the component. They represent a screen area or element on the UI along with the respective settings and metadata. This component type will be covered in the course.

![component.js: Component controlled which provides the component methods. manifest.json: Descriptor for storing metadata associated with the component.](../images/d1ce55a75b327a80.png)
A component has a component controller (Component.js) and a descriptor (manifest.json). Only the component controller is mandatory, but it is recommended to also use the descriptor file. The descriptor then contains the component metadata, and also expresses the component dependencies and configuration (see below).
All required and optional resources of a component are organized in a unique namespace. The namespace of the component equals the component name.
Optional resources of a component are, for example, CSS, js, or i18n files, views, and controllers.
The figure, _Structure of a Component_ , gives an example of the folder structure of a component.
## Descriptor
The descriptor provides a central, machine-readable, and easy-to-access location for storing metadata associated with a component.
The data of the descriptor is stored in JSON format in the manifest.json file.
The existence of the manifest.json file must be declared in the metadata defined in the Component.js file (see below). The declaration in the component metadata makes the component load the manifest.json file and read the relevant entries for SAPUI5.
![Screenshot of the manifest.json file, as discussed in the text.](../images/dedc53a907147654.png)
The content of the descriptor is structured using namespaces, amongst others, the sap.app, sap.ui, and sap.ui5 namespaces (see the figure _Structure of the Descriptor_):
  * The sap.app namespace provides application-specific attributes.
  * The sap.ui namespace provides UI-specific attributes.
  * The sap.ui5 namespace provides SAPUI5-specific attributes.

Each new SAPUI5 version implies a new version of the descriptor. This descriptor format version is described by the value of the mandatory _version property at root level of the descriptor (see the figure _Structure of the Descriptor_). How the value of this property is exactly related to the SAPUI5 version, and the descriptor version can be found in the documentation.
![Screenshot of the sap.app code, as discussed in the following text.](../images/c44596739c1bd85d.png)
The figure, _sap.app Namespace_ , shows some attributes from the sap.app namespace. A complete listing of all attributes can be found in the documentation.
The id attribute is a mandatory attribute that must be provided in dot notation and specifies a unique Id for the project. It must match the namespace provided in the corresponding Component.js file.
If the component controller is created there, for example, via
JavaScript
Copy codeSwitch to dark mode

```

1

UIComponent.extend("sap.training.exc.Component", { . . . });

```

the id attribute must have the value sap.training.exc.
The title and description of the project are maintained using the title and description attributes of the sap.app namespace. To make the attribute values language dependent, a key value is specified in double curly braces: {{key}}
The specified keys are maintained in a file with the extension .properties. The i18n attribute can then be used to specify the URL to this file. The URL is interpreted relative to the manifest.json file. The way in which the maintained texts can be made available in other languages will be discussed later in the course.
The texts referenced in the descriptor for title and description can be read by the SAP Fiori launchpad, for example.
![Screenshot of the sap.ui5 code, as discussed in the following text.](../images/2cd0430549193198.png)
The figure, _sap.ui5 Namespace_ , shows some attributes from the sap.ui5 namespace.
The dependencies attribute contains the external dependencies to libraries and components that are loaded by the SAPUI5 core during the initialization phase of the component. Everything referenced here can be used directly in the component's code.
The libs property contains the libraries that the SAPUI5 core should load for use in the component. In the example, among others, the sap.ui.core and the sap.m library are loaded initially.
The minUI5Version property specifies the minimum SAPUI5 version that the component requires. Since SAPUI5 does not currently enforce the use of the correct version, minUI5Version is used for informational purposes only. If the minimum SAPUI5 version criterion is not met, a warning is issued in the console log.
The rootView attribute specifies the root view to open. The value of this attribute can be the view name as a string for XML views, or the view configuration object with viewName for the view name and type for the view type, id, async and other properties of sap.ui.core.mvc.View.
In the example shown, the XML view with the module name sap.training.exc.view.App is set as the root view of the component. It is loaded asynchronously via the module system and has the id App. This means that when the component is instantiated and embedded in the UI, the App view is automatically displayed as the initial view.
## Using Components
To render UI components, you must wrap them in a sap/ui/core/ComponentContainer. You cannot use the placeAt method to place UI components directly in a page.
The component container separates the application and the nested component. It is an SAPUI5 control that can be nested at any place within the SAPUI5 control tree.
To load and create a UI component, you can use the following options:
  * Create a new component instance asynchronously before creating the container using the create method of sap.ui.core.Component. The separately created component instance can then be passed to the constructor of sap.ui.core.ComponentContainer.
  * Create a new component instance asynchronously when creating the container using the constructor of sap.ui.core.ComponentContainer (see the following example).

![Screenshot of the component instance code, as discussed in the following text.](../images/4ec4fa8242008037.png)
In the figure, _Creating a Component Instance_ , a component instance is instantiated together with the component container. For this reason, the module in which instantiation takes place is dependent on sap/ui/core/ComponentContainer. The constructor of ComponentContainer is passed a settings object with the following properties:
  * id
This property is used to pass the Id for the component container instance to be created.
  * name
The name property contains the name of the component to be instantiated.
  * manifest
Via manifest: true the so called "manifest first" function is used. This allows SAPUI5 to load and evaluate the manifest.json descriptor before the component controller. This is recommended because it improves the performance of the initial load. The loading process can be parallelized and optimized this way. After the descriptor is loaded, the component factory can load the dependencies (SAPUI5 libraries and other dependent components) in parallel with the component preload.
  * async
async: true is used to specify that the component should be created asynchronously.
  * settings
The settings object is passed to the component instance when it is created. In the example, it is used to set the component instance Id.

After the component container is created, the placeAt method is called on it to add it to a UI area.
## Encapsulate an Application as a Component
### Business Scenario
In this exercise, you will rebuild the application from the previous exercise into an SAPUI5 component. The application descriptor (manifest.json file) and the component controller (Component.js file) required for this are already included in the project. For the encapsulation, you will make some adjustments in these files. Finally, you will instantiate the component and embed it in the HTML page.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/5_controllers**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/6_components**  |
### Task 1: Adjust the Application Descriptor
#### Steps
  1. Open the manifest.json file from the webapp folder in the editor.
  2. Set the id property from the sap.app namespace to the value **sap.training.exc** to specify the ID for the project.
    1. Modify the content of line 4 in the manifest.json file as follows:
XML
Copy codeSwitch to dark mode

```

1

 "id": "",

```

  3. Set the rootView property from the sap.ui5 namespace to the value **sap.training.exc.view.App** to specify the _App_ view from the project as the root view that shall be opened.
    1. Modify the content of line 102 in the manifest.json file as follows:
XML
Copy codeSwitch to dark mode

```

1

 "viewName": "",

```

### Task 2: Maintain the Title and the Description of the Component
#### Steps
  1. Open the i18n.properties file from the webapp/i18n folder in the editor.
  2. Add the following lines there to maintain a language dependent title as well as a language dependent description for the component:
XML
Copy codeSwitch to dark mode

```

123

# App Descriptor
appTitle=Exercise Application
appDescription=A simple app that demonstrates important concepts of SAPUI5

```

Note
The appTitle and appDescription keys are used in the manifest.json file (properties sap.app/title and sap.app/description) to set the title and description for the component.

#### Result
The i18n.properties file should now look like this:
![The i18n.properties file, as described in the preceding text.](../images/eaf99b7d4871b7f1.png)
### Task 3: Adapt the Bootstrap Script
#### Steps
  1. Open the index.html page from the webapp folder in the editor.
  2. Delete the following attribute in the bootstrap script:
XML
Copy codeSwitch to dark mode

```

1

data-sap-ui-libs="sap.m"

```

Note
The libraries that are required by the component and therefore need to be loaded by SAPUI5 are specified in the application descriptor of the component (property sap.ui5/dependencies). The sap.m library is listed there, so it does not need to be loaded by the bootstrap script anymore.

#### Result
The bootstrap script should now look like this:
![Screenshot of the script tag in the HTML file.](../images/d10e5f868777b65a.png)
### Task 4: Edit the Component Controller
#### Steps
  1. Open the Component.js file from the webapp folder in the editor.
  2. Add the following code to the component controller implementation to ensure that the application descriptor manifest.json is loaded and used:
JavaScript
Copy codeSwitch to dark mode

```

12345678

metadata: {
  manifest: "json"
},

init: function () {
  // call the base component's init function
  UIComponent.prototype.init.apply(this, arguments);
}

```

Note
The init() method is called by the framework when the component is instantiated. Later, you will implement necessary initializations for the component in this method. It is obligatory to make a super call to the init() function of the base class in the overridden init() method.

#### Result
The Component.js file should now look like this:
![The Component.js file, highlighting the metadata code.](../images/9fcba03ae5565680.png)
### Task 5: Instantiate the Component
#### Steps
  1. Make sure the index.js module is open in the editor.
  2. Delete the code that instantiates the XML view and places it on the HTML page in the index.js module.
    1. Delete the following lines:
JavaScript
Copy codeSwitch to dark mode

```

123456

XMLView.create({
  id: "App",
  viewName: "sap.training.exc.view.App"
}).then(function (oView) {
  oView.placeAt("content");
});

```

Note
Instead of the XML view, you will instantiate the component in the next step and place it on the HTML page. The component instance will then display the _App_ view as the root view.
#### Result
The index.js module should now look like this:![The resulting index.js file.](../images/440f615139b96067.png)
  3. Now modify the implementation of the index.js module as follows to instantiate the component and place it on the HTML page:
JavaScript
Copy codeSwitch to dark mode

```

123456789101112131415

sap.ui.define(["sap/ui/core/ComponentContainer"], function (ComponentContainer) {
  "use strict";

  var oContainer = new ComponentContainer({
      id: "container",
      name: "sap.training.exc",
      manifest: true,
      async: true,
      settings: {
        id: "sap.training.exc"
      }
  });
  oContainer.placeAt("content");

});

```

Note
Pay attention to the changed dependency array and parameter of the factory function. index.js now depends on sap/ui/core/ComponentContainer instead of sap/ui/core/mvc/XMLView.
#### Result
The index.js file should be implemented as follows:![The resulting index.js file,](../images/5e1ae33d43365d76.png)
  4. Test run your application by starting it from the SAP Business Application Studio.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the component is displayed with the _App_ view as the root view.
