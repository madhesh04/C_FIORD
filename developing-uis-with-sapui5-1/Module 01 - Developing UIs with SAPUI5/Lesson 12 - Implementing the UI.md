# Implementing the UI

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/structuring-the-ui-with-controls_b072eddd-a5cf-495f-ac69-aa2c9fb76b5a*

Objective
After completing this lesson, you will be able to create UIs using the Shell, App, Page, Panel and SimpleForm controls
## Simple Form
Before implementing a form, let's first try to understand the structure of a form.
Watch the video to understand the structure of a form.
Settings
### Implementing a Simple Form
Now that you have understood the overall structure of a form, we will look at the implementation of a form using the SimpleForm control.
![Screenshot of the SimpleForm control code.](../images/34b10aa0251edf68.png)
The libraries sap.ui.layout.form and sap.ui.core are required for working with the SimpleForm control. The names of these libraries must therefore be mapped to XML namespaces in an XML view. In the example in the figure, Using the SimpleForm Control, the prefixes f and core, respectively, are used for the mapping.
The layout property of the <f:SimpleForm> tag specifies the form layout that is used to render the form content. There are several layouts available. It is recommended to use the ColumnLayout, as its responsiveness uses the space available in the best way possible.
If editable controls are used as content, the editable property of the <f:SimpleForm> tag must be set to true, otherwise to false. If the editable property is set incorrectly, there will be visual issues like wrong label alignment or wrong spacing between the controls.
The content of the form is specified via the content aggregation. It is structured in the following way:
  * Add a sap.ui.core.Title element (or Toolbar control) to start a new group (FormContainer).
  * Add a Label control to start a new row (FormElement).
  * Add controls such as input and text fields as needed. They will be assigned to the row (FormElement) that started with the last label.

### Adding a Toolbar
Let's look at how to add a toolbar to a form.
![Screenshot of the toolbar code, as discussed in the text.](../images/6134d8d5645633e9.png)
The toolbar aggregation can be used to optionally add a toolbar to the SimpleForm control. In the example shown in the figure, _Adding a Toolbar_ , a sap.m.Toolbar control is added to this aggregation. The controls to be displayed in the toolbar are placed in its content aggregation.
The ToolbarSpacer used adds horizontal spacing between the elements of a sap.m.Toolbar. This will cause the button to be displayed at the end of the line.
In addition to the text _Create Customer_ , an icon is also displayed on the button. The prefix sap-icon:// indicates that the icon comes from the icon font delivered with SAPUI5. It contains more than 500 icons.
Note
You can look up other icons using the [Icon Explorer](https://ui5.sap.com/#/tools) tool in the _Demo Kit_.
For more details about the SimpleForm control, see the documentation.
## Panel
### Adding a Panel
The sap.m.Panel control provides a container for grouping and displaying information.
It consists of a title bar that can be used to display a header text, an optional header toolbar, an optional info toolbar, and a content area.
![Screenshot of the sap.m.Panel code, as discussed in the text.](../images/a33292c5575cef37.png)
The expandable property (default value: false) can be used to specify whether the content and the info toolbar (if present) of the panel can be collapsed and expanded.
The expanded property (default value: false) specifies whether the panel is initially expanded or not.
The headerToolbar aggregation allows the use of a custom toolbar as header for the panel. The header toolbar is visible in both expanded and collapsed state. It can be used to add extra controls for user interactions in the header.
The infoToolbar aggregation allows the use of a custom toolbar as information bar for the panel. The info toolbar is placed below the header and is visible only in expanded state. It can be used to show extra information to the user.
The content aggregation determines the content of the panel. It can contain any number of controls of any type.
For more information about the panel, see the documentation.
## Page
### Adding a Page
The sap.m.Page control is a container control that holds one whole screen of an application. It is often used as the root control of a view (see the following figure).
![Screenshot of the code, highlighting Page Title, title, and showNavButton.](../images/e65b8a73436b25d6.png)
The page has three distinct areas: a header, a content area, and a footer.
The topmost area of the page is occupied by the header. The title property of the page can be used to set a title that will appear in the header bar.
A navigation button is displayed on the left side of the header bar if the showNavButton property is set to true. When the navigation button is pressed, the navButtonPress event is fired. In the example in the figure, the event handler onNavPress is attached to the event to be able to react to the button click.
The content aggregation determines the content of the page. It occupies the main part of the page and can contain any number of controls of any type.
The footer is optional and occupies the bottom part of the page.
For more information about the page control, see the documentation.
## App and Shell
Applications often consist of multiple pages, where the user can go to detail pages and back again. SAPUI5 supports this pattern by providing the control sap.m.App. The App control inherits the navigation capabilities from the sap.m.NavContainer control.
When developing an SAPUI5 application, the App control is often used as the root element. It adds certain header tags to the HTML page that are necessary for proper display and offers functionality to navigate between pages with animations. The content entities between which sap.m.App navigates can be of type sap.m.Page, sap.ui.core.mvc.View or any other control with full-screen/page semantics. To display the corresponding pages, they are added to the pages aggregation of the App control.
![Diagram illustrating an SAPUI5 app structure with App.view.xml containing sap.m.Shell and sap.m.App using a pages aggregation that links to two XML views with sap.m.Page components.](../images/d923eee945d00896.png)
SAPUI5 gives the developer a lot of freedom to define the design of an application based on the App control. A typical design is to use one view per page to be displayed. The figure, _Typical Approach_ , shows such an application design, which is also used in the exercise scenario.
In this approach, a so-called App view is created (App.view.xml), which contains an empty <App> tag. This App view is specified in the application descriptor manifest.json as the root view of the component to be opened.
The pages to be displayed are implemented as XML views, with each XML view using a sap.m.Page control as its root element. The XML views are then added to the pages aggregation of the App control using the router. This will be discussed later in the course.
In the App view, place the <App> tag inside an sap.m.Shell container.
The use of the Shell container is to control the width of the application on a desktop. On large monitors, a full width rendering of an application can be too wide. Placing the App control inside a Shell container gives you the appropriate left and right vertical margins.
The Shell control provides more options to customize the application, like setting a custom background image or color, and setting a custom logo. Check the _API Reference_ and the _Samples_ in the _Demo Kit_ for more details.
![Screenshot of the App.view.xml code as described in the text.](../images/ddd6e563ee389857.png)
The figure, _The App View_ , shows the App view implementation discussed above in the App.view.xml file.
In the <mvc:View> tag, the attribute displayBlock="true" has been added. This prevents vertical scrollbars appearing with views that are set to 100% height.
Contrary to the description above, the <App> tag is not empty. Instead, an XML view named sap.training.exc.view.Overview is statically embedded in the pages aggregation via the <mvc:XMLView> tag. This is only a preliminary implementation. In the unit on _Routing and Navigation_ , it will be explained how to embed views dynamically via the router. Then it will also be possible to implement navigation between views, that is, to exchange views dynamically in the pages aggregation.
## Add a UI with a Form
### Business Scenario
In this exercise, you will add a form for creating new flight customers to the application. You embed the SimpleForm UI element used for this purpose in a Panel UI element, which in turn is to be contained in a Page UI element.
The nesting of SimpleForm, Panel, and Page UI element is implemented in a separate XML view. You refer to this view from the existing App view. There, the new view is to be embedded in the pages aggregation of the App UI element, which in turn is to be contained in a Shell.
The figure, _UI with Form_ , shows the nested structure of the UI.![Screenshot highlighting the nested elements of the form.](../images/0c424e6bd580683b.png)
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/7_declarative_API_for_components**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/8_SimpleForm**  |
### Task 1: Implement the View with the Form
#### Steps
  1. Open the Overview.view.xml file from the webapp/view folder in the editor.
Note
For simplicity, the XML view file in which the form will be implemented is already included in the project. Also the corresponding view controller file Overview.controller.js is already present in the webapp/controller folder.
  2. Add the following attributes to the <mvc:View> tag to declare the XML namespaces required for the view implementation:
XML
Copy codeSwitch to dark mode

```

12

xmlns:f="sap.ui.layout.form"
xmlns:core="sap.ui.core"

```

#### Result
The Overview view should now look like this:![The resulting Overview.view.xml code.](../images/844dd0c3ab1b7420.png)
  3. Insert the following coding into the <mvc:View> tag to define a sap.m.Page on the view with a sap.m.Panel, which in turn contains the desired sap.ui.layout.form.SimpleForm.
Note
The functionality of the _Create Customer_ button in the toolbar of the form will only be implemented in a later exercise via an event handler.
XML
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223242526272829303132333435363738394041

<Page title="Flight Customers">
  <content>
    <Panel headerText="New Customer" expandable="true" expanded="true">
      <content>
        <f:SimpleForm layout="ColumnLayout" editable="true">
          <f:toolbar>
            <Toolbar>
              <content>
                <ToolbarSpacer/>
                <Button icon="sap-icon://create" text="Create Customer"/>
              </content>
            </Toolbar>
          </f:toolbar>
          <f:content>
            <core:Title text="General Data"/>
            <Label text="Form"/>
            <Input value=""/>
            <Label text="Customer Name"/>
            <Input value=""/>
            <Label text="Discount"/>
            <Input value=""/>
            <core:Title text="Address Data"/>
            <Label text="Street"/>
            <Input value=""/>
            <Label text="Post Code"/>
            <Input value=""/>
            <Label text="City"/>
            <Input value=""/>
            <Label text="Country"/>
            <Input value=""/> 
            <core:Title text="Contact Data"/>
            <Label text="Email"/>    
            <Input value=""/>
            <Label text="Telephone"/>
            <Input value=""/>     
          </f:content>
        </f:SimpleForm>
      </content>
    </Panel>
  </content>
</Page>

```

#### Result
The Overview view should now look like this:
![The Overview.view.xml file, highlighting the Page tag.](../images/2e67dc15b1d92b4f.png)
### Task 2: Refer to the Form View from the App View
#### Steps
  1. Open the App.view.xml file from the webapp/view folder in the editor.
  2. Add the following attribute to the <mvc:View> tag to make the full-screen height of the view work properly:
XML
Copy codeSwitch to dark mode

```

1

displayBlock="true"

```

#### Result
The App view should now look like this:![The app.view.xml file, highlighting the displayBlock attribute.](../images/d53bee672d13fac4.png)
  3. Delete the _Say Hello_ button from the App view.
    1. Delete the following line:
XML
Copy codeSwitch to dark mode

```

1

<Button text="Say Hello" press=".onSayHello"/>

```

  4. Insert the following code into the<mvc:View> tag to embed the Overview view in the pages aggregation of a sap.m.App UI element, which in turn is wrapped in a sap.m.Shell:
XML
Copy codeSwitch to dark mode

```

1234567

<Shell>
  <App>
    <pages>
      <mvc:XMLView viewName="sap.training.exc.view.Overview"/>
    </pages>
  </App>
</Shell>

```

#### Result
The App view should now look like this:
![The App.view.xml file, highlighting the Shell tag.](../images/d2b9bb50255a3301.png)
### Task 3: Adjust the App View Controller
#### Steps
  1. Open the App.controller.js file from the webapp/controller folder in the editor.
Note
Since the _Say Hello_ button on the App view was deleted in the previous step, all button-related code is now deleted from the view controller.
  2. Delete the onSayHello event handler method from the view controller.
    1. Delete the following lines:
JavaScript
Copy codeSwitch to dark mode

```

123

onSayHello: function () {
  MessageBox.information("Hello World");
}

```

  3. Remove module sap/m/MesssageBox from the dependency array and the corresponding interface parameter MessageBox from the factory function of the view controller.
#### Result
The view controller should now look like this:![The resulting App.controller.js file.](../images/187578a7599f9683.png)
  4. Test run your application by starting it from the SAP Business Application Studio.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the component with the form is displayed as expected.
