# Creating an SAP Fiori Elements App Using the Application Generator

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/creating-an-sap-fiori-elements-app-using-the-application-generator*

Objective
After completing this lesson, you will be able to create an app using the App Generator.
## Prepare SAP Business Application Studio for Development
In this exercise, you will create a development space in SAP Business Application Studio. This step is required before you can start working in SAP Business Application Studio. A development space is an environment with the tools, capabilities, and resources required to develop your application.
### Prerequisites
You have created your free trial account on SAP BTP using the details provided in the exercise Getting Started in the unit Getting an Overview of ABAP RESTful Application Programming Model.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_63AC7CC6948251AC:uebung)
### Steps
  1. Open the SAP BTP Cockpit by accessing <https://account.hanatrial.ondemand.com/>.
  2. Select _SAP Business Application Studio_.
  3. Select _Create Dev Space_.
  4. Choose the SAP Fiori option.
  5. Enter a name for your dev space, for example UX406.
  6. Select _Create Dev Space_ from the bottom of the page. You can see that the _UX406_ dev space has been created and is _Starting_.
  7. Launch the dev space by clicking on it when the status changes to _Running_.
  8. Wait for all the tools and templates to be installed once the dev space is launched.

### Result
You successfully created a development space for yourself in SAP Business Application Studio. You will use it in the upcoming exercises.
## Create the Manage Travels App
In this exercise, you will create an app in your development space of SAP Business Application Studio. You will use the travel service that you have created in the previous exercises using ADT. To access the service from SAP Business Application Studio, you have to first log in to Cloud Foundry.
### Prerequisites
You have completed the exercise Prepare SAP Business Application Studio for Development in this lesson. You have also completed the exercise Add Two Subsections to a Section on the Object Page in the unit Configuring ABAP CDS Annotations in the Back end (lesson: Creating an Object Page).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_910C6ACB81A32CAC:uebung)
### Steps
  1. Open the SAP BTP Cockpit using the <https://account.hanatrial.ondemand.com/> link.
  2. Select _Go To Your Trial Account_.
  3. Select _trial_ from the _Subaccounts_ tab of your _Global Account_ view.
  4. Copy the _API Endpoint_ URL mentioned in the _Cloud Foundry Environment_.
  5. Open SAP Business Application Studio.
  6. Open the _Terminal_ within your SAP Business Application Studio.
    1. Select the first icon from the left-hand side menu bar.
    2. Choose the _Terminal_ option.
    3. Choose _New Terminal_ from the subsequent menu. The terminal opens.
  7. Log in to Cloud Foundry.
    1. Enter **cf login** in the terminal after _user $_. Press ENTER on your keyboard.
    2. Paste the _API endpoint_ URL you copied from SAP BTP cockpit in the _Terminal_. Press ENTER on your keyboard.
    3. Add your e-mail address in the _Email_ option. Press ENTER on your keyboard.
    4. Enter your password. Press ENTER on your keyboard. You have logged in to Cloud Foundry.
  8. Generate a project based on your OData service from an existing template.
    1. Select the _New Project from Template_ tab within your development space.
    2. Select the _SAP Fiori generator_ option and select _Start_ from the bottom of the view.
    3. Select _List Report Page_ from the available templates for the _Select Template and Target Location_ step.
    4. Select _Next_ from the bottom of the view.
    5. Select _Connect to a System_ as the _Data Source and Service Selection_ option from the dropdown list that is generated for the _Data Source_ field.
    6. Choose _ABAP Environment on SAP Business Technology Platform_ as the option for the _System_ field.
    7. Choose _default_abap-trial_ as the option for the _ABAP Environment_ field.
    8. To enter the _Service_ name, switch to ADT. Copy _ZUI_FE_TRAVEL_######_O4_ as your service binding name.
    9. Paste the copied service name in the _Service_ field.
    10. Click _Next_ from the bottom of the page.
    11. Choose _Travel_ as the _Main entity_ option for the _Data Source and Service Selection_ section.
    12. Select _Next_ from the bottom of the view.
    13. Select _Main Entity_ as _Travel_ from the _Entity Selection_ view.
    14. Select _Next_ from the bottom of the view.
    15. Maintain the project attributes such as _Module Name_ and _Application Title_.
    16. Scroll down to add the deployment configuration, FLP configuration, or to configure advanced options.
    17. Select _Finish_ from the bottom of the view.
    18. Select the option _Add project to workspace_ from the popup dialog box. The project gets generated, and you can see the _Application Information_.
  9. Select the second icon _EXPLORER_ from the left-hand side menu bar.
  10. Expand the _travels_ option. You can see your travels project in the _EXPLORER_ view.

### Result
You successfully created an SAP Fiori elements app based on your OData service. You selected List Report Page as the template for your app.
## Preview the Application in SAP Business Application Studio
In this exercise, you will preview your application in the browser from SAP Business Application Studio.
### Prerequisites
You have completed the exercise Create the Manage Travels App in this lesson.
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_54546D826ED1BBAC:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. You have the _EXPLORER_ tab open.
  3. Select the _Preview Application_ option from the _Application Information_.
  4. Choose the _start fiori run_ NPM script from the _Preview Options_.
  5. The app preview opens in your browser.
  6. Select the _Go_ option from the list report page.
  7. Select a travel. The object page for the travel opens.
  8. Switch to SAP Business Application Studio. In the terminal, you can see which requests have been sent.
  9. Stop the server by pressing CTRL+C in the terminal.
  10. Once the server stops, you can see another option to start the app preview.
  11. Select the _EXPLORER_ tab from the left-hand side menu.
  12. Right-click the _webapp_ folder from the expanded _travel_ project.
  13. Choose _Preview Application_ from the subsequent menu.
  14. Choose the _start fiori run_ NPM script from the Preview Options.
  15. The app preview opens in your browser.

### Result
You successfully started the app preview in your browser. You also stopped the server and started it again.
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/getting-an-overview-of-sap-fiori-tools)
