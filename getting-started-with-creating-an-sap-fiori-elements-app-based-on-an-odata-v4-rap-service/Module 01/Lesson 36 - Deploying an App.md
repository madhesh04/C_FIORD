# Deploying an App

*Source: https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/deploying-an-app*

Objective
After completing this lesson, you will be able to manually deploy your SAP Fiori elements app to your account on SAP BTP.
## Deploy the Manage Travels App to SAP BTP
In this exercise, you will manually deploy the _Manage Travels_ app to your trial account on SAP BTP, ABAP environment. You will do the following in SAP Business Application Studio:
  * Login to the corresponding Cloud Foundry endpoint
  * Add a deploy configuration
  * Create an MTA archive from your project
  * Deploy your app

### Prerequisites
You have completed the exercise Add a Field Building Block to Your Custom Section in the unit Examining the Flexible Programming Model (lesson: Using Building Blocks).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_DDAFA4D3689AFA8:uebung)
### Steps
  1. Open SAP Business Application Studio.
  2. Select the first icon from the left-hand side menu.
  3. Select _View_ from the list.
  4. Choose _Command Palette_ from the subsequent menu.
  5. Log in to the corresponding Cloud Foundry endpoint
    1. Search for CF:LOGIN TO CLOUD FOUNDRY in the command palette.
    2. Select _CF:Login to Cloud Foundry_ from the list.
    3. Choose _Credentials_ from _Select authentication method_ option on the _Cloud Foundry Sign In and Targets_ view.
    4. Enter your username and password in the respective fields.
    5. Select _Sign in_ from the bottom of the view.
    6. Select the dropdown for the _Select Cloud Foundry Organization_ field once you sign in.
    7. Select the trial account that you have created.
    8. Select _dev_ for the _Select Cloud Foundry Space_ field.
    9. Select _Apply_ from the bottom of the view. You have logged in to the corresponding Cloud Foundry endpoint.
  6. Add a deployment configuration.
    1. Right-click _travels_ from the _EXPLORER_.
    2. Select _Open Application Info_ from the subsequent menu.
    3. Select _Add Deploy Config_ from the _Application Info - travels_.
    4. Select the dropdown for the _Please choose the target_ field in the _Deploy Configuration_ view.
    5. Choose _Cloud Foundry_ from the list.
    6. Select the dropdown for the _Destination name_ field.
    7. Select _abap-cloud-default_ link for your trial account.
    8. Select _Finish_ from the bottom of the view.
    9. A popup message confirms that the files containing deployment configuration have been generated. You can see them within the _travels_ project.
  7. Create an MTA archive from your project.
    1. Right-click _mta.yaml_ from within the _webapp_ on your _EXPLORER_.
    2. Choose _Build MTA Project_ from the subsequent menu. You can see that the _mta_archives_ are built within the _travels_ project.
  8. Deploy your app.
    1. Select _Deploy_ from the _Application Info - travels_ view.
    2. The app is deployed. You can see the progress at the bottom of the view.

### Result
You successfully deployed your app to your trial account on SAP BTP, ABAP environment.
## View the Deployed App in Your Trial Account on SAP BTP
In this exercise, you will launch the deployed app from your trial account on SAP BTP.
### Prerequisites
You have completed the exercise Deploy the Manage Travels App to SAP BTP in the same unit (lesson: Deploying an App).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through detailed steps. You can find all the steps after the simulation. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_BBB7D296685C52B4:uebung)
### Steps
  1. Open the SAP BTP Cockpit using the <https://account.hanatrial.ondemand.com/> link.
  2. Select _Go To Your Trial Account_.
  3. Select _trial_ from the _Subaccounts_ tab of your _Global Account_ view.
  4. Select _Subscribe to SAP Build Work Zone, standard edition_ from _Subaccounts_.
  5. Select _Create_ from the subsequent view.
  6. Choose the dropdown for the _Plans_ field from the _New Instance or Subscription_ dialog.
  7. Select the _standard_ option from the dropdown.
  8. Select _Create_ from the bottom of the _New Instance or Subscription_ dialog.
  9. Select _View Subscription_ from the _Creation in Progress_ dialog. You have now subscribed to the _SAP Build Work Zone_.
  10. Select _HTML5 Applications_ from the left-hand side menu of your trial account.
  11. Select _travels_ from the _Subaccount: trial - HTML5 Applications_ view. The _Manage Travels_ app opens in your browser.

### Result
You successfully launched the previously deployed _Manage Travels_ app in your browser from your trial account on SAP BTP .
[Continue to quiz](https://learning.sap.com/courses/getting-started-with-creating-an-sap-fiori-elements-app-based-on-an-odata-v4-rap-service/deploying-an-sap-fiori-elements-app)
