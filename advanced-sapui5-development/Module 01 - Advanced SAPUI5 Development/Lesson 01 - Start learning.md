# Start learning

*Source: https://learning.sap.com/courses/advanced-sapui5-development/designing-a-full-screen-application_d32759a4-f312-4539-9b52-a0999fa4fcb7*

Objective
After completing this lesson, you will be able to design a full-screen application using sap.m.App.
## Understanding the basic application design of a fullscreen application
The Model View Controller (MVC) concept is used in SAPUI5 to separate the representation of information from the user interaction. This separation facilitates development and the changing of parts independently. In general, when you are implementing the information architecture of an application, it consists of more than one page. Apps are composed of several pages. Based on user interaction, the user will navigate from one view to multiple related views. An example of this is as follows: the user will navigate from an overview view to one or more views where other related types of information are displayed.
### The sap.m.App
SAPUI5 supports this pattern by providing the control, _sap.m.App_. The default type of transition when navigating is "slide". Other predefined options are "fade", "flip", and "show".
![An illustration of the pages aggregation of the sap.m.App control](../images/6c184db6ad415170.png)
The figure illustrates the technical design of the _sap.m.App_ control. _sap.m.App_ inherits the navigation capabilities from the  _sap.m.NavContainer_ control. Although the _sap.m.App_ control provides functionality for navigation, it is not recommended that you use this approach for productive applications (see routing).
### Typical MVC Approach
The separation of concerns is also a very important concept, even when it comes to implementing SAPUI5 views.
Watch this video to know more about a typical MVC approach.
The recommended application design is to have one XML that only contains the implementation of the _sap.m.App_ control as a root control. The remaining Views (also XML Views) are used for the pages.
The _sap.m.App_ control provides an aggregation called pages. The controls aggregated by the pages aggregation of _sap.m.App_ receive navigation events like beforeShow. These navigation events are documented in the pseudo interface,  _sap.m.NavContainerChild_.
### The index.html File
The starting point of each SAPUI5 application is the index.html file.
![An index.html file example](../images/d692627fdfd79433.png)
The index.html file contains the SAPUI5-bootstrapping implementation. The SAPUI5 bootstrap script in your page initialize SAPUI5 runtime automatically as soon as the script is loaded and executed by the browser. The html-body contains all the necessary implementation details for loading the SAPUI5-component using the namespace.
### The App.view.xml File
Each application contains a view implementation that contains the _sap.m.App_ as the central control. This view is shown right after the application has been loaded on the client. As you can see in the following figure, the App.view.xml file contains a _sap.ui.core.mvc.View_ control. The control itself only contains the _sap.m.App_ control with an assigned id.
![A sample App.view.xml file](../images/5ef15876131b65c5.png)
The description is as follows:
  * The App view only contains the empty **App** tag (1).
  * The App view is specified in the Application Descriptor (_manifest.json_) as the root View that will be opened.
  * The pages will be added automatically into the App control according to the current URL by the router.
  * The router identifies the App control by means of the id.
  * The displayBlock="true" prevents vertical scrollbars appearing with Views that are set to 100% height (2).

### Example Page of Carrier.view.xml
As already discussed, it is good practice to separate the different aspects of our application in different view implementations. The following figure shows you a view implementation related to displaying a list of carriers provided by an OData-service.
![A sample Carrier.view.xml file](../images/c60387b13906599b.png)
_sap.m.Page_ provides a basic container for an application screen.
_sap.m.Page_ provides an aggregation with the name content. The aggregation takes to 0..n controls. In the implementation above, an sap.m.Table control is added to the content aggregation for the purposes of displaying a list of entities from the entity set CarrierCollection.
## Explore the design of a Full-screen Application
### Business Example
In the following exercise, you will explore the design of a Full-screen Application with SAPUI5.
### Prerequisites
  1. Before you start this exercise, you should have already downloaded the prepared files from Github : <https://github.com/SAP-samples/sapui5-development-advanced-learning-journey>
  2. In the following exercises, SAP Business Application Studio is used as the development environment. It is assumed that you already have access to this development tool.
If this is not yet the case, you can gain access to the SAP Business Application Studio free of charge using the free tier model for SAP Business Technology Platform (SAP BTP). To do this, read this tutorial [Get an Account on SAP BTP to Try Out Free Tier Service Plans](https://developers.sap.com/tutorials/btp-free-tier-account.html) on how to create a free account on SAP BTP. Based on this, the video [SAP Business Application Studio Free Tier Model Onboarding](https://www.youtube.com/watch?v=-g7LZHqcbDQ) shows you the necessary steps to set up the free tier plan for SAP Business Application Studio.
  3. You might also want to setup your browser to allow all popups, if possible. If you are not allowed to change those settings, you will be notified each time you preview your application in Business Application Studio and have to select _Open_ in the displayed dialog.

Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Steps
  1. Import the fullscreen.tar project into your Business Application Studio.
    1. Locate the fullscreen.tar file in your training files.
    2. Log into the training SAP Business Application Studio as shown in a previous training.
    3. Select the menu _File_ → _Open Folder..._.
    4. Select or Enter the **/home/user/projects/** folder and choose _OK_.
    5. Select the menu _File_ → _Import Project.._.
    6. Select the fullscreen.tar file and choose _OK_.
  2. Look at the views and controllers.
What is the name of the main application control?
What is the _App_ view displaying?
What is the _Carrier_ view displaying?
What is the _Flights_ view displaying?
What is the _NotFound_ view displaying?
    1. Expand the view sub folder.
The main application control is named App.
    2. Open the _App_ view.
The _App_ view is only containing the sap.m.App control.
    3. Open the _Carrier_ View.
The _Carrier_ view is displaying a table listing carriers from the UX_C_Carrier_TP entity.
    4. Open the _Flights_ view.
The _Flights_ view is displaying a table listing flights from the to_flights association of a carrier id.
    5. Open the _NotFound_ view.
The _NotFound_ view is displaying a message with a Go Back button to navigate back to previous screen..
    6. Expand the controller sub folder and open the files.
For the moment no script is provided for the views, except for the NotFound view which contains the script to manage navigation to the previous screen.
