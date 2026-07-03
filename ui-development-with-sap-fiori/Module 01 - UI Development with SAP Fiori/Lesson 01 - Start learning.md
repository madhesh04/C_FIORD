# Start learning

*Source: https://learning.sap.com/courses/ui-development-with-sap-fiori/deconstructing-the-golden-rules-of-sapui5-development_a5937529-71dd-4804-9da0-6fcaa4308a91*

Objective
After completing this lesson, you will be able to apply the golden rules of SAPUI5 development to develop SAP Fiori apps
## Golden Rules of SAPUI5 Development
In this lesson, you'll see how developers can benefit from applying the golden rules of SAPUI5 development while building SAP Fiori apps.
Before introducing you to the golden rules, we have organized these rules into groups to make them easier to understand and apply when developing SAP Fiori apps.
| How to Design and Build SAP Fiori App?  |
  * SAP Fiori apps must have an approved UX design
  * SAP Fiori UIs are built with SAPUI5

 |
| --- | --- |
| How to Use OData services in SAP Fiori?  |
  * SAP Fiori apps are based on OData services
  * SAP Fiori UIs and OData Services must be defined in different software components
  * One SAP Fiori app - One OData service

 |
| Why Use Declarative Design for SAP Fiori Apps?  |  Every SAP Fiori app is defined by a set of metadata  |
| Why Use UI Theme Designer to Apply Corporate Design?  |  No custom CSS is allowed for SAP Fiori apps  |
| How to Make SAP Fiori Apps Platform Independent?  |
  * Every SAP Fiori app must run as a web app and must run in the SAP Fiori Launchpad
  * Every SAP Fiori app must run on mobile devices in the native app paradigm

 |
Let's go through each golden rule in detail.
### How to Design and Build SAP Fiori App?
We will start with golden rules that will help developers design and build SAP Fiori apps.
| SAP Fiori Apps Must Have an Approved UX Design |
| --- |
|
  * Use the Design-led Development process as it is valid for all UI scenarios.
  * Ensure there is a common and holistic understanding of the end-user tasks to be solved and the app that should be built before starting.
  * Ensure that the design complies with the Fiori Design Guidelines (or your own).
  * Ensure that the designs only use existing controls and patterns.

 |
| SAP Fiori UIs Are Built with SAPUI5 |
| --- |
|
  * Use SAPUI5 UI technology to build new SAP Fiori applications.
  * Use Smart Templates (metadata driven UIs) and, if possible, SAP Fiori Elements and the SAP ABAP RESTful Application Programming Model for standard SAP S/4HANA applications.
  * Use UI5 freestyle for pixel perfect applications that do not follow a pattern-like approach.
  * Use Smart controls to create applications following pattern-like approach. To provide smart behaviour, smart controls interprets OData metadata.
  * Use a combination of UI5 freestyle and Smart Controls for pixel perfect applications that only have minor deviations from Smart Template applications.
  * Use technologies like SAP Web Dynpro ABAP, SAP Floorplan Manager and SAP Web GUI for existing apps that are not built from scratch.

 |
### How to Use OData services in SAP Fiori?
Next, we will cover the set of golden rules that are related to OData services.
| SAP Fiori Apps Are Based on OData Services |
| --- |
|
  * An OData service is required for each app.
  * Other considerations for building SAP Fiori apps include:
    * An app must be able to use several OData services.
    * An app must be able to indirectly view reusable app parts.
    * An app must be able to direct data binding at run-time derived from metadata.
    * An SAP Fiori app also relies on the central UI2 services.
    * An SAP Fiori app uses one central reuse service to provide message long texts.
    * An SAP Fiori app may use a separate service to implement value helps.

 |
| SAP Fiori UIs and OData Services Must Be Defined in Different Software Components |
| --- |
|
  * The system landscape for SAP Fiori Apps supports two different deployment options: embedded deployment and hub deployment.
  * The UI, the gateway, and the business back end are deployed on the business back-end system in the Embedded deployment.
  * The UI and the gateway are deployed on a different system from the business back-end system in the hub deployment.
  * The mandate is to package all UI relevant artefact in a separate software component to support Hub deployment, it is mandatory.
  * The OData service development package should be treated as an add-on.

 |
| One SAP Fiori App - One OData Service |
| --- |
|
  * There is a one-to-one relationship between the OData service and the app.
  * The individual entity-relationship model is tailored to the data needs of the SAP Fiori app.
  * All, and only, the data needed by the application are delivered by one OData-service.
  * The 1:1 relationship between SAP Fiori app and Odata service simplifies the life-cycle of an SAP Fiori app and its data access.

 |
### Why Use Declarative Design for SAP Fiori Apps?
Let's move on to the next rule.
| Every SAP Fiori App is defined by a Set of Metadata |
| --- |
|
  * SAP Fiori apps define their set of metadata in an app descriptor (manifest.json) file.
  * App descriptors make it easy to orchestrate and automate the development delivery.
  * App descriptors are mandatory for SAP Fiori apps.

 |
### Why Use UI Theme Designer to Apply Corporate Design?
Next, we will cover why UI Theme Designer is essential to SAP Fiori app development.
| No Custom CSS Is Allowed For SAP Fiori Apps |
| --- |
|
  * Note that HTML/CSS generated by UI5 is not part of the public API and may change in patch and minor releases.
  * Do not override UI5 with CSS in SAP apps as it bears the risk of breaking the application on updating UI5.
  * Use the standard CSS classes of SAPUI5, such as for margins, paddings, or visibility on various devices.
  * Make use of the UI theme designer.

 |
### How to Make SAP Fiori Apps Platform Independent?
It is time to talk about rules related to platform independence in SAP Fiori apps.
You need to consider following rules to make your SAP Fiori apps platform independent.
| Every SAP Fiori App Must Run as a Web App and Must Run in the SAP Fiori Launchpad |
| --- |
|
  * SAP Fiori apps must be implemented as self-contained UI5 Components.
  * Avoid:
    * Using absolute URLs generated in the front- or back-end.
    * Using private UI5 properties or functions.
    * Calling UI2 services directly instead of using the APIs.
    * Using platform-specific functionality without an availability check.
    * Using private UI5 properties or functions.
    * Using generated IDs for accessing UI-controls.
  * SAP Fiori apps must build in platform independence.
  * SAP Fiori apps must run from out of the box without platform specific adjustments. It is usually a bug in the app when an app does not run on a particular platform.
  * SAP Fiori apps must be implemented as self-contained UI5 Components.
    * noShellIndex.html: local, isolated test without shell services
    * FioriSandbox.html: local, integrated test with mock shell services
    * FioriLaunchpad.html: productive usage

 |
| Every SAP Fiori App Must Run on Mobile Devices in the Native App Paradigm |
| --- |
|
  * The SAP Fiori apps can run on a mobile device within the browser, SAP Mobile Start and as self-contained native-packaged apps.
  * An SAP Fiori app must run inside SAP Mobile Start or be deployed as a Packaged App if it wants to benefit from native features.
  * The most generic way apps can run on mobile devices and still have access to native features is by running the app inside the SAP mobile start.
  * The SAP Fiori apps can be pre-packaged as self-contained native apps. All static web resources are bundled into a Cordova container.

 |
[Continue to quiz](https://learning.sap.com/courses/ui-development-with-sap-fiori/applying-the-golden-rules-of-sapui5-development_98a83c7e-e65d-3219-abd3-7678b0a51ec1)
