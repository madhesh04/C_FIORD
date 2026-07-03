# Implementing the CrossApplicationNavigation Service

*Source: https://learning.sap.com/courses/ui-development-with-sap-fiori/implementing-the-crossapplicationnavigation-service_fb4e7db5-b59c-43a4-8a41-8a1f34a0bda1*

Objective
After completing this lesson, you will be able to implement the CrossApplicationNavigation service to navigate between SAP Fiori applications
## Cross Application Navigation
### Using the CrossApplicationNavigation-Service
After the recap of the target mapping and the tile configuration, we want to take a look on how to implement navigation using the class [sap.ushell.services.CrossApplicationNavigation](https://ui5.sap.com/#/api/sap.ushell.services.CrossApplicationNavigation).
The **CrossApplicationNavigation** service is used to navigate from one SAP Fiori application to another. We will next see how to implement navigation using the class [sap.ushell.services.CrossApplicationNavigation](https://ui5.sap.com/#/api/sap.ushell.services.CrossApplicationNavigation) and how to use CrossApplicationNavigation service in custom SAP Fiori Application implemented as SAPUI5-freestyle application.
Let's look at the code snippet that triggers navigation using the CrossApplicationNavigation service.
![Screenshot of the code snippet, as described in the text.](../images/4c9dccb00df30df0.png)
The code snippet shows how to use the sap.ushell.services.CrossApplicationNavigation. In the display onInit implementation, we will check in the first line of code whether the application is running in the SAP Fiori Launchpad or not.
Remember one of the golden SAPUI5 rules was Every SAP Fiori app must run as a web app. This says that it should also be possible to run the application outside of the SAP Fiori Launchpad, of course we limited features, but it runs.
If the reference to **sap.ushell.Container.getService** can be resolved, the reference to the **getService** function is stored in the variable **_fnGetService**. Next we can call the function and pass the value CrossApplicationNavigation as a parameter. In the third line of the implementation we call the function hrefForExternal and pass the name of the semantic object and the action to the function as parameter.
The parameter _hash will contain the calculated hash. In the shown example the value is **#UX410NavEnd00-display**. And this is the value that was created automatically during target mapping configuration.
The implementation of the **onPress** function in the code snippet will trigger the navigation directly.
As you can see in the implementation, it is also possible to pass simple key-value pairs as navigation parameter to the target. The target application is able to fetch these data and work with them.
Next, we will look at the code snippet that shows how to work with navigation parameters.
![Screenshot of the code snippet, as described in the text.](../images/0e0bf560c0307619.png)
In the code snippet, you can see how to handle parameters that were passed during intent-based navigation. The navigation parameters sent by the navigation initiator will be stored in the parameter startupParameters of the target application. In our example the first application passed a parameter with the name helloText and the value Hello UX410. Please have in mind that the parameter helloText is handled as an array inside the target application.
### Navigating in SAP Fiori Using the CrossApplicationNavigation Service
Time to look at an end-to-end example to explain implementation of CrossApplicationNavigation service.
Let's say that the user has two applications in the SAP Fiori Launchpad. These applications are named startnavigation and endnavigation. To complete a business process, the user has to navigate, after the user has completed the first task of the process, to another application, pass arguments to that second application, and proceed in the second application.
We will next look at a series of videos explaining the usage of CrossApplicationNavigation service to navigate from the startnavigation application to the endnavigation application.
Watch the first video to see how to implement the link and button controls to navigate from the startnavigation application to the endnavigation application.
The following code shows how to implement the onInit function to check if the application is running the SAP Fiori Launchpad.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223242526272829303132

sap.ui.define([
        "sap/ui/core/mvc/Controller"
    ],
        /**
        * @param {typeof sap.ui.core.mvc.Controller} Controller
        */
        function (Controller) {
            "use strict";

            return Controller.extend(
               "student##.sap.training.startnavigation.controller.Main", {

          onInit: function () {
  this._fnGetService = sap.ushell &&
       sap.ushell.Container &&
       sap.ushell.Container.getService;
  this._oCrossAppNavigation = this._fnGetService &&
       this._fnGetService("CrossApplicationNavigation");

  this._hash = (this._oCrossAppNavigation&&
       this._oCrossAppNavigation.hrefForExternal({

    target : {
      semanticObject : "UX410NavEnd00",
      action: "display"
    }

  })) || "";

  let _oLink = this.byId("idNavLink");
  _oLink.setHref(this._hash);
}

```

The following code shows how to implement the onPress event handler in the controller Main.controller.js of the Main view of project startnavigation.
Code Snippet
Copy codeSwitch to dark mode

```

123456789

onPress : function(oEvent) {
    if(this._oCrossAppNavigation) {
     var oHref = this._oCrossAppNavigation.toExternal({
      target : {
       shellHash : this._hash
      }
    })
  }
}

```

Watch the next video to see how to extend your implementation of the startnavigation application and pass a parameter to the navigation target.
Settings
The following code shows how to pass parameters to the navigation target.
Code Snippet
Copy codeSwitch to dark mode

```

12345678910111213141516171819

onInit: function () {
  this._fnGetService = sap.ushell &&
       sap.ushell.Container &&
       sap.ushell.Container.getService;
  this._oCrossAppNavigation = this._fnGetService &&
       this._fnGetService("CrossApplicationNavigation");

  this._hash = (this._oCrossAppNavigation&&
                this._oCrossAppNavigation.hrefForExternal({
    target : {
      semanticObject : "UX410NavEnd00",
      action: "display"
    }

  })) || "";

  let _oLink = this.byId("idNavLink");
  _oLink.setHref(this._hash);
}

```

Watch the last video in the series to see how to extend your implementation of the endnavigation application to fetch a parameter passed from another application.
The following code shows how to extend the endnavigation Application to fetch a parameter passed from another application.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920

sap.ui.define([
  "sap/ui/core/mvc/Controller"
],

  function (Controller) {
    "use strict";

    return Controller.extend(
        "student##.sap.training.endnavigation.controller.Main", {
      onInit: function () {
        var oComponentData = this.getOwnerComponent().getComponentData();
        if(oComponentData && oComponentData.startupParameters &&
           oComponentData.startupParameters.helloText) {
        var sHelloText = oComponentData.startupParameters.helloText[0];
        var oLabel = this.byId("idInfo");
        oLabel.setText(sHelloText);
      }
    }
  });
});

```

## How to Navigate in SAP Fiori
For the steps and data of this demonstration, refer to the exercise **Navigate in SAP Fiori**.
## Navigate in SAP Fiori
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, naming of fields and buttons as well as steps may differ from the exercise solution.
Caution
Please be aware that in some code blocks, the code of previous implementation steps is not shown. In the following steps, please do not delete any code that you have added in previous steps.
Note
In the following exercises please replace ## with your user group.
Hint
Don't bother with the errors about missing id shown by the code editor. IDs are mandatory if you want your application to be enabled for UI Adaptation. If this is not the case, you can simply set the FlexEnabled property to False in the manifest.json file.
### Business Example
In the SAP Fiori Launchpad the user has two applications. To complete a business process the user has to navigate, after the user has completed the first task of the process to another application, pass arguments to that second application and proceed in the second application.
### Task 1: Create a SAPUI5 Project for the first application
#### Steps
  1. Create a new project with a deployment configuration using the SAP Fiori application – project generator.
#### Project properties
| Parameter  | Value  |
| --- | --- |
| Project type  | SAP Fiori application  |
| Template Type  | SAP Fiori  |
| Template  | Basic  |
| Data source  | None  |
| View  | Main  |
| Module name  | startnavigation  |
| Application namespace  | student##.sap.training  |
#### Deployment configuration
| Parameter  | Value  |
| --- | --- |
| Target  | **ABAP**  |
| Destination  | **S4D_100**  |
| Name  | **ZUX410NavStar##**  |
| Description  | **UX410 navigation starter ##**  |
| Package  | **ZTRAIN_##**  |
| Transport Request  | Transport assigned to your user, see transaction SE01  |
    1. Start the SAP Business Application Studio.
    2. To create a new project at the _Welcome_ page, choose the tile _Start from template_.
    3. Choose _SAP Fiori application_ from the list of available templates and choose _Start_.
    4. Choose **SAP Fiori** as _Template Type_
    5. Select the _Basic_ template and choose _Next_.
    6. Select **None** from the _Data source_ list and choose _Next_.
    7. Insert **Main** as _view name_ and choose _Next_.
    8. Insert **startnavigation** as _module name_ and **student##.sap.training** as _namespace_.
    9. Select _Yes_ at the Add deployment configuration and choose _Next_.
    10. Select **ABAP** as target and choose the destination **S4D_100** from the list of available destinations
    11. Insert **ZUX410NavStar##** as name for the _ABAP Repository_.
    12. Insert the description **UX410 navigation starter ##** into the description field.
    13. insert **ZTRAIN_##** as _package_ and insert the transport request assigned to your user. You can use transaction SE01 at the S4D-system to find the transport assigned to your user.
    14. Choose _Finish_.
  2. Remove the generated routing pattern _:?query:_ to replace it with an empty string.
    1. Open the file manifest.json.
    2. Scroll down to the routes configuration.
    3. Remove the string literal :?query: to replace it with an empty string.
  3. Implement the basic _startnavigation_ project by adding a new sap.ui.layout.VerticalLayout control to the page control of the Main.view.xml and add a sap.m.Link and a sap.m.Button control to UI controls to the VerticalLayout control. Add the following attributes to the newly added controls.
#### Properties of sap.m.Link control
| Attribute  | Value  |
| --- | --- |
| id  | **idNavLink**  |
| text  | **Navigate to Fiori-app with link**  |
#### Properties of sap.m.Button control
| Attribute  | Value  |
| --- | --- |
| press  | **onPress**  |
| text  | **Navigate to Fiori-app using event handler**  |
    1. Open the file Main.view.xml.
    2. Add an XML-namespace alias with the value **layout** and assign the value **sap.ui.layout**.
    3. Add an sap.ui.layout.VerticalLayout to the content aggregation of the generated sap.m.Page control.
    4. Add a control of type sap.m.Link to the VerticalLayout control and assign the attributes listed in the first table.
    5. Add a control of type sap.m.Button and assign the button attributes listed in the second table.
    6. Your view implementation should now look like the following figure:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415161718

<
mvc:View controllerName="student##.sap.training.startnavigation.controller.Main"
xmlns:mvc="sap.ui.core.mvc" displayBlock="true"
xmlns="sap.m"
xmlns:layout="sap.ui.layout">
    <Page id="page" title="{i18n>title}">
        <content>
            <layout:VerticalLayout id="_IDGenVerticalLayout1">
                <Link id="idNavLink"
                      text="Navigate to Fiori-app with link"/>
                <Button id="_IDGenButton1"
                        press="onPress"
                        text="Navigate to Fiori-app using event handler"/>
            </layout:VerticalLayout>
        </content>
    </Page>
</mvc:View>

```

  4. Build and deploy the _startnavigation_ project to the connected SAP system _S4D_100_ using the npm run deploy command.
    1. Select the project and from the context menu choose _Open in Terminal_.
    2. Insert in the console the command **npm run deploy**.
    3. Confirm to start the deployment.
  5. Close all tabs in Business Application Studio.

### Task 2: Create a SAPUI5 project for the second application
#### Steps
  1. Create a new project with a deployment configuration using the SAP Fiori application – project generator.
#### Project properties
| Property  | Value  |
| --- | --- |
| Template Type  | SAP Fiori Generator  |
| Template  | Basic  |
| Data source  | None  |
| View  | **Main**  |
| Module name  | **endnavigation**  |
| Application namespace  | **student##.sap.training**  |
#### Deployment configuration
| Property  | Value  |
| --- | --- |
| Target  | ABAP  |
| Destination  | S4D_100  |
| Name  | **ZUX410NavEnd##**  |
| Package  | **ZTRAIN_##**  |
| Transport Request  | Transport assigned to your user, see transaction SE01  |
| Description  | **UX410 navigation end ##**  |
#### .env content
| Property  | Value  |
| --- | --- |
| UI5_USERNAME  | **TRAIN-##**  |
| UI5_PASSWORD  | Password of SAP user TRAIN-##  |
    1. If not still open, start the SAP Business Application Studio.
    2. Choose the link _New Project from template_ in the Get Started Page of the SAP Business Application Studio or go to the menu entry _File_ → _New Project from Template_ .
    3. Choose **SAP Fiori Generator** as _Template Type_.
    4. Select the _Basic_ template and choose _Next_.
    5. Select **None** from the _Data source_ list and choose _Next_.
    6. Insert **Main** as _view name_ and choose _Next_.
    7. Insert **endnavigation** as _module name_ and **student##.sap.training** as _namespace_.
    8. Select _Yes_ at the Add deployment configuration and choose _Next_.
    9. Select **ABAP** as target and choose the destination **S4D_100** from the list of available destinations.
    10. Insert **ZUX410NavEnd##** as name .
    11. Insert the description **UX410 navigation end ##** into the description field.
    12. Insert **ZTRAIN_##** as package and insert the transport request assigned to your user. You can use transaction SE01 at the S4D-system to find the transport assigned to your user.
    13. Choose _Finish_.
  2. Remove the generated routing pattern _:?query:_ to replace it with an empty string.
    1. Open the file manifest.json.
    2. Scroll down to the routes configuration.
    3. Remove the string literal :?query: to replace it with an empty string.
  3. Implement the basic **endnavigation** project by adding a new sap.ui.layout.VerticalLayoutcontrol to the page control of Main.view.xml and insert the following UI controls to the VerticalLayout.
#### sap.m.Label Control Properties
| Attribute  | Value  |
| --- | --- |
| id  | **idinfo**  |
| text  | **Hello world**  |
    1. Open the file Main.view.xml.
    2. Add an XML-namespace alias with the value **layout** and assign the value **sap.ui.layout**.
    3. Add a control of type sap.ui.layout.VerticalLayout to the content aggregation of the generated sap.m.Page control.
    4. Add a control sap.m.Label to the VerticalLayout control and assign the attributes listed in the table. Your implementation should now look like the following figure:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112

<mvc:View controllerName="student##.sap.training.endnavigation.controller.Main"
    xmlns:mvc="sap.ui.core.mvc" displayBlock="true"
    xmlns="sap.m"
    xmlns:layout="sap.ui.layout">
    <Page id="page" title="{i18n>title}">
        <content>
            <layout:VerticalLayout>
              <Label id="idInfo" text="Hello world"/>
            </layout:VerticalLayout>
        </content>
    </Page>
</mvc:View>

```

  4. Build and deploy the _endnavigation_ project to the connected SAP system _S4D_100_ using the npm run deploy command.
    1. Select the project and from the Context menu, choose _Open in Terminal_.
    2. Insert in the console the command **npm run deploy**.
    3. Confirm to start the deployment.
    4. IIf you are asked to insert your credentials insert user **TRAIN-##** and your password

### Task 3: Configure Two Tiles in the SAP Fiori Launchpad
#### Steps
  1. Create two semantic objects in the _S4D_ system using the following details.
#### Semantic Object Configuration
| Semantic Object  | Semantic Object Name  | Semantic Object Description  |
| --- | --- | --- |
| UX410NavStart##  | UX410NavStart##  | Semantic Object for start app##  |
| UX410NavEnd##  | UX410NavEnd##  | Semantic Object for end app##  |
    1. Start _SAP GUI_ and log in to _S4D_ system using your user **TRAIN-##** login details.
    2. From the user menu of the _SAP Fiori_ → _Configuration_ , choose _Define Semantic Object – Customer_ or use the transaction code /UI2/SEMOBJ.
Add the prefix **/n** if you start the transaction using the transaction code.
    3. Select _Edit_ to switch to edit mode.
    4. Confirm the cross-client message.
If a message informs you that the table is currently locked by another user, this means that another course participant is currently running the transaction for their exercise. Confirm the message, wait until the other participant has finished, and then try again.
    5. Choose _New Entries_ on the toolbar.
    6. Add the semantic object configuration with the data from the Table: Semantic Object, Name and Description.
    7. Save your changes and assign them to your transport request.
    8. Confirm the transport assignment dialog and close the transaction.
It is important to close the transaction as soon as you have finished your configuration. If you do not leave, you will lock the table.
  2. Create a Catalog in the _S4D_ system with the _Launchpad Content Manager_ app using the attributes from the following table:
#### Catalog Configuration
| Property  | Value  |
| --- | --- |
| Title  | **UX410_BC_##**  |
| ID  | **ZUX410_BC_##**  |
    1. Open Chrome navigator.
    2. In the favorites bar, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_
    3. Enter your credentials and login. You can save your password for future logins.
    4. If the _Quick Tour_ Popup opens, close it.
    5. Navigate to _SAP Fiori Launchpad_ space and start the Launchpad _Content Manager_ app.
Note
It may take some time to open.
![System screenshot](../images/44b6566240af2200.png)
    6. Choose _Create_ after the app starts.
    7. Insert the values from the Catalog configuration table and choose _Continue_.
    8. Choose an assigned transport request and confirm the dialog.
  3. Create a tile mapping for application _ZUX410NavStar##_ using _SAP Fiori Launchpad Designer_ and the configuration properties shown in the following table.
#### Target mapping configuration for Start-navigation App
| Property  | Value  |
| --- | --- |
| Semantic Object  | **UX410NavStart##**  |
| Action  | **display**  |
| Application Type  | SAPUI5 Fiori App  |
| Title  | **UX410 start navigation**  |
| URL  | **/sap/bc/ui5_ui5/sap/zux410navstar##**  |
| ID  | **student##.sap.training.startnavigation**  |
Hint
If you get an error when creating the target mapping, refreshing your browser tab should get rid of the issue.
    1. Refresh the _Launchpad Content Manager_ app if it's still opened, or open it again.
    2. Search for your newly created catalog in the _Launchpad Content Manager_ app.
    3. Choose _Open in Designer_.
    4. Select the _Target Mapping_ icon inside the new catalog.
    5. Select _Create Target Mapping_.
    6. Insert the properties from the table into the form.
    7. Choose _Save_.
  4. Create a new tile mapping for application _ZUX410NavEnd##_ using the configuration properties shown in the following table:
#### Target mapping configuration for End-navigation App
| Property  | Value  |
| --- | --- |
| Semantic Object  | **UX410NavEnd##**  |
| Action  | **display**  |
| Application Type  | SAPUI5 Fiori App  |
| Title  | **UX410 end navigation**  |
| URL  | **/sap/bc/ui5_ui5/sap/zux410navend##**  |
| ID  | **student##.sap.training.endnavigation**  |
    1. Select _Create Target Mapping_.
    2. Insert the properties from the table into the form.
    3. Choose _Save_.
  5. Create two static tiles in your catalog with the following attributes:
#### Title Configuration for Start
| Attribute  | Value  |
| --- | --- |
| Title  | **Navigation start**  |
| Subtitle  | **Group ##**  |
| Semantic Object:  | **UX410NavStart##**  |
| Action  | **display**  |
#### Title Navigation for End
| Attribute  | Value  |
| --- | --- |
| Title  | **Navigation end**  |
| Subtitle  | **Group ##**  |
| Semantic Object:  | **UX410NavEnd##**  |
| Action  | **display**  |
    1. Choose the first _Tiles_ icon and select the tile with the _plus_ sign.
    2. Choose _App Launcher – Static_.
    3. Enter the values as provided in the table.
    4. Save your changes.
    5. Repeat to create a tile for the second target.
    6. Close the SAP _Fiori Launchpad Designer_ tab and Exit the _Content Manager_ app.
  6. Create a new Launchpad Space including a new Launchpad Page with the following properties
#### Properties of Space/Page configuration
| Property  | Value  |
| --- | --- |
| Space ID  | **ZSPACE_##**  |
| Space Description  | **Space of group ##**  |
| Space Title  | **Navigation exercise ##**  |
| Page ID  | **ZPAGE_##**  |
| Page Description  | **Page of group ##**  |
| Page Title  | **Navigation exercise ##**  |
| Transport  | Use the transport assigned to your user  |
    1. Start the _Manage Launchpad Spaces_ App from the _SAP Fiori Launchpad_.
    2. Click the _Create_ Button in the toolbar of the _Spaces_ table
    3. Select the _Also create a page_ option
    4. Insert the values of the above table
    5. Click _Create_.
  7. Assign the SAP Fiori catalog _UX410_BC_##_ to the page _ZPAGE_##_ and use **Navigation exercise ##** as Section Title and add the tiles from the catalog to the page.
    1. Click on the newly created page and select _Edit_.
    2. Insert the value **Navigation exercise ##** in the _Section Title_ input field.
    3. Select the three dots on the right side of the page toolbar and click on the button labeled _Catalogs_.
    4. Search in the upcoming dialog for catalog **UX410_BC_##**.
    5. Select the catalog and press _Select_.
    6. Press on each tile the button labeled _Add_ to add the tile to the page
![System screenshot](../images/9ad35f63d3b80c48.png)
    7. Press _Save_.
  8. Set the page visibility to Visible
    1. Go back to the Space configuration of your newly created space _ZSPACE_##_.
![System screenshot](../images/4c410e9541d27671.png)
    2. Press the _Edit_ button to enter the edit mode
![System screenshot](../images/cc7350824ed5503c.png)
    3. Mark the page as selected by choosing the radio button
![System screenshot](../images/0991cf95867d8f39.png)
    4. Press the _Set Visible_ button.
    5. Press _Save_.
    6. Go back to the SAP Fiori Launchpad _Home_ page.
  9. Create a new single role with the name **Z_BR_UX410_##** and add the space _ZSPACE_##_ to the role. Assign your user **TRAIN-##** to the role _Z_BR_UX410_##_.
    1. Open the SAP GUI and logon to the S4D-system
    2. Start transaction PFCG.
    3. Insert the value **Z_BR_UX410_##** in the input field and press _Single Role_.
    4. Click _Menu_ and confirm that you want to save your changes.
    5. Choose from the _Transaction_ DropDown Field _SAP Fiori Launchpad_ → _Launchpad Catalog_.
    6. Search for your catalog **ZUX410_BC_##** , select the catalog and confirm the dialog.
    7. Choose from the _Launchpad Catalog_ DropDown Field _SAP Fiori Launchpad_ → _Launchpad Space_.
    8. Insert in the upcoming dialog the space id **ZSPACE_##** or use the F4-value help to search for it and press _Continue_.
    9. Select the _User_ tab and assign your **TRAIN-##** user to the role
    10. Press _Save_.
  10. Test your configuration.
    1. Open _SAP Fiori Launchpad_ or Refresh the browser page if it's already opened.
    2. Select the _Navigation exercise ##_ space.
    3. Click on the tiles and verify that the applications are shown
  11. Close the SAP Fiori Launchpad.

### Task 4: Use the CrossApplicationNavigation Service
Implement the link and button controls to navigate from the _Navigation start_ application to the _Navigation end_ application.
#### Steps
  1. Implement the onInit function so it checks that the application is running the SAP Fiori Launchpad. Obtain a reference to the CrossApplicationNavigation service ShellContainer and store the reference in a member variable. Create the navigation link to the intent UX410NavEnd## - display created in the previous task and assign the navigation link to the href attribute of the sap.m.Link control that was created in the previous task.
    1. Start the SAP Business Application Studio and Open the Dev Space _UX410_.
    2. Open the Main.controller.js file of the _startnavigation_ project.
    3. If not already created, create an empty implementation of the onInit function.
    4. Implement theonInit function to check whether the application is running the SAP Fiori Launchpad. Obtain a reference to the CrossApplicationNavigation Service and assign the reference to a member variable.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617

sap.ui.define([
    "sap/ui/core/mvc/Controller"
],
    function (Controller) {
        "use strict";

        return Controller.extend(
           "student##.sap.training.startnavigation.controller.Main", {

          onInit: function () {
            this._fnGetService = sap.ushell &&
                  sap.ushell.Container &&
                  sap.ushell.Container.getService;
            this._oCrossAppNavigation = this._fnGetService &&
                  this._fnGetService("CrossApplicationNavigation");
         });
    });

```

    5. Invoke the function hrefForExternal and pass the value UX410NavEnd## as semanticObject and the value display as action.
    6. Obtain a reference to the sap.m.Link control implemented in the Main.view.xml view and assign the return value to a local variable.
    7. Call the setHref function on the sap.m.Link reference and pass the hash to the function.
    8. Your code should now look like the following :
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920

onInit: function () {
  this._fnGetService = sap.ushell &&
       sap.ushell.Container &&
       sap.ushell.Container.getService;
  this._oCrossAppNavigation = this._fnGetService &&
       this._fnGetService("CrossApplicationNavigation");

  this._hash = (this._oCrossAppNavigation&&
                this._oCrossAppNavigation.hrefForExternal({
    target : {
      semanticObject : "UX410NavEnd00",
      action: "display"
    }

  })) || "";

  let _oLink = this.byId("idNavLink");
  _oLink.setHref(this._hash);
}

```

  2. Implement the onPress event handler in the controller Main.controller.js of the _Main_ view of project _startnavigation_. Use the reference to the CrossApplicationNavigation service that was obtained in the onInit function. Call the toExternal function on the reference and pass the value UX410NavEnd##as semantic object and the value display as action to the function.
    1. If not already open, open the Main.controller.js file in the _controller_ folder of the _startnavigation_ project.
    2. Add an empty implementation for the eventhandler function _onPress_ right after the onInit implementation.
    3. Check that the reference to the CrossApplicationNavigationservice is available. If the reference is available call the toExternal function on the reference and pass the target configuration with attribute shellHash to the function. Assign to shellHash the hash-string stored in the member variable that was obtained in the onInit function.
    4. Save your changes. Your implementation should now look like the following:
Code Snippet
Copy codeSwitch to dark mode

```

12345678910

onPress : function(oEvent) {
  if(this._oCrossAppNavigation) {
    var oHref = this._oCrossAppNavigation.toExternal({
      target : {
        shellHash : this._hash
      }
    })
  }
}

```

  3. Deploy the _startnavigation_ project to the S4D-system.
    1. Select the _startnavigation_ application and choose from the context menu _Open in Terminal_.
    2. Enter **npm run deploy** and follow the instructions.
  4. Log on to the _SAP Fiori launchpad_ to test your implementation. Start your application and try the link and button to test the navigation.
    1. Select the bookmark in Google Chrome to start the _SAP Fiori launchpad_.
    2. Enter your log on credentials.
    3. Start the _startnavigation_ application.
    4. Choose the link to initiate the navigation.
    5. Navigate back to the _startnavigation_ application using the back button of the _SAP Fiori launchpad_.
    6. Select the button control to navigate.

### Task 5: Passing Parameters to the Navigation Target
#### Steps
  1. Extend your implementation of the _startnavigation_ application and pass a parameter with the name **helloText** during the navigation. Assign the string **Hello UX410** to the helloText parameter.
    1. If not still open, start the SAP Business Application Studio and open the Dev Space _UX410_.
    2. Open the Main.controller.js file of the project _startnavigation_.
    3. Enhance the onInit function of your controller by passing the configuration objectparams to the hrefForExternal function and assign the parameter helloText with value **Hello UX410** to the parameter.
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223

onInit: function () {
  this._fnGetService = sap.ushell &&
        sap.ushell.Container &&
        sap.ushell.Container.getService;
  this._oCrossAppNavigation = this._fnGetService &&
        this._fnGetService("CrossApplicationNavigation");

  this._hash = (this._oCrossAppNavigation&&
                this._oCrossAppNavigation.hrefForExternal({
    target : {
      semanticObject : "UX410NavEnd00",
      action: "display"
    },
    params : {
      "helloText" : "Hello UX410"
    }

  })) || "";

  let _oLink = this.byId("idNavLink");
  _oLink.setHref(this._hash);
}

```

  2. Deploy the updated _startnavigation_ project.
    1. Select the _startnavigation_ project and choose from the context menu the _Open in Terminal_ option.
    2. Enter **npm run deploy** and follow the instructions.

### Task 6: Extend the endnavigation Application to Fetch a Parameter Passed from Another Application
Extend your _endnavigation_ application so that when the user navigates from the _startnavigation_ application to the _endnavigation_ application, the passed parameter is fetched from the component and shown inside the UI.
#### Steps
  1. Implement the onInit function of the Main.controller.js file of the _endnavigation_ project. Read the helloText parameter that is passed by the _startnavigation_ application and assign the parameter value to the text attribute of the label that is part of the Main.view.xml implementation.
    1. Open the file Main.controller.js of the _endnavigation_ project.
    2. Implement an empty onInit function inside the controller implementation.
    3. Obtain the component data and assign the component data to a local variable with the name oComponentData.
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415161718

sap.ui.define([
  "sap/ui/core/mvc/Controller"
],

  function (Controller) {
    "use strict";

    return Controller.extend(
        "student##.sap.training.endnavigation.controller.Main", {
      onInit: function () {
        var oComponentData =
            this.getOwnerComponent().getComponentData();

      }
    }
  });
});

```

    4. Check if the startupParameters of the component contains the parameter helloText. If the parameter is available obtain the value of the parameter and assign it to local variable.
Code Snippet
Copy codeSwitch to dark mode

```

12345678

onInit: function () {
  var oComponentData = this.getOwnerComponent().getComponentData();
  if(oComponentData && oComponentData.startupParameters &&
       oComponentData.startupParameters.helloText) {
    var sHelloText = oComponentData.startupParameters.helloText[0];
  }
}

```

    5. Obtain a reference to a UI control of type sap.m.Label with ID idInfo and assign the reference to a local variable. Call the setText function on the object and pass the start-up parameter value to the text attribute of the UI control.
Code Snippet
Copy codeSwitch to dark mode

```

12345678910

onInit: function () {
  var oComponentData = this.getOwnerComponent().getComponentData();
  if(oComponentData && oComponentData.startupParameters &&
     oComponentData.startupParameters.helloText) {
    var sHelloText = oComponentData.startupParameters.helloText[0];
    var oLabel = this.byId("idInfo");
    oLabel.setText(sHelloText);
  }
}

```

  2. Deploy the updated _endnavigation_ project.
    1. Select the _endnavigation_ and choose from the context menu the _Open in Terminal_ option.
    2. Enter **npm run deploy** and follow the instructions.
  3. Logon to the SAP Fiori Launchpad to test your implementation. Open the _startnavigation_ app and test the navigation implementation.
    1. Start the _SAP Fiori launchpad_ using the bookmark in Google Chrome.
    2. Enter your details to log in.
    3. Start the _startapplication_ application.
    4. Choose the link to initiate the navigation.
    5. Navigate back to the _startapplication_ application using the back button of the SAP Fiori Launchpad.
    6. Select the button control to navigate.

[Continue to quiz](https://learning.sap.com/courses/ui-development-with-sap-fiori/sap-fiori-launchpad-configuration_db1c61d4-e7ff-3d95-82a0-c8016ab0ca97)
