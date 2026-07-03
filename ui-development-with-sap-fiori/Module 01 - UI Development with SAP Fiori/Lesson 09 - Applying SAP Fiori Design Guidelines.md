# Applying SAP Fiori Design Guidelines

*Source: https://learning.sap.com/courses/ui-development-with-sap-fiori/working-with-sap-fiori-design-guidelines_ab11c169-54de-4f51-87b9-f61c8a5198be*

Objective
After completing this lesson, you will be able to apply SAP Fiori design guidelines to provide consistent user experience
## SAP Fiori Layouts
### Introduction to SAP Fiori Layouts
Do you recall the golden rule of SAPUI5 development that says "SAP Fiori apps must have an approved UX design."?
After understanding the user and business needs, it comes to the design of the application. The first decision that designers and developers have to make is what overall layout should be used.
This depends a lot on the way the information needs to be presented in the app and how the user will access this information.
Julie meets Carmen to gather more details about the app.
![A conversation about app requirements, including time recording status, available hours, billable hours, non-billable hours, approved hours, and unapproved hours, referencing SAP Fiori Design Guidelines.](../images/1f91d07a19ab13b6.png)
The SAP Fiori Design Guidelines knows two main layouts and three layout variants.
Main layouts are:
  * Dynamic Page
  * Flexible Column Layouts

Layout variants are:
  * Comparison Pattern
  * Multi Instance
  * Semantic Page

In this lesson we will focus on the two main layouts.
Settings
### When to use dynamic page layout
Use the dynamic page layout if you are building a freestyle application that uses the dynamic page header and footer toolbar features of SAP Fiori (versions 1.40 and higher)
Do not use the dynamic page layout if you are planning any of the following scenarios:
  * Use SAP Fiori elements, such as the list report, analytical list page, overview page, or object page. These elements already incorporate the dynamic page layout.
  * Implement an initial page or object page floorplan. These floorplans already incorporate snapping header and footer toolbar features. The behavior is similar to the dynamic page, but the technical foundation is different.
  * Display a small amount of information. In this case, use a dialog instead. If you cannot avoid using the dynamic page layout, use letterboxing to mitigate the issue.

### When to use flexible page layout
Use the flexible-column layout if you want to create a master-detail or master-detail-detail scenario in which the user can drill down or navigate.
Do not use the flexible-column layout if you are planning any of the following scenarios:
  * You want to build a workbench or tools layout. The flexible-column layout is not meant to provide a main column with additional side columns on the left and right or either. If you want to display additional content to enrich the main content and to help users better perform their tasks, use the dynamic side content instead.
  * You want to create a dashboard with context-independent pages.
  * You want to open multiple instances of the same object type. Use the multi-instance-handling floorplan instead.
  * You want to split a single object into multiple columns, or display only a small amount of information.
  * You want to embed the SAP Fiori launchpad or overview page into one of the columns.

### Things to Remember
The following table should help to decide what layout should be used and what type of question you asked yourself for making a decision.
| Question  | Template  |
| --- | --- |
| Is viewing, inspecting, or editing details on one or several elements from a list of elements an important user requirement?  | If so, use the flexible column layout pattern, for example a tracking app.  |
| Is inspecting the status of one or more objects important?  | If so, use the flexible column layout pattern, for example a tracking app.  |
| Are the objects you are inspecting so complex that you require charts to illustrate a point quickly?  | If so, you should use a dynamic page app with charts.  |
### Connect with Marco Rossi
Now that you've learned about the SAP Fiori layouts, put on your thinking cap and help Marco make the right decision in this use case activity.
## SAP Fiori Floorplans
### Introduction to SAP Fiori Floorplans
Floorplans are usually based on the dynamic page. Floorplans serve specific use cases and therefore come with a specific combination of UI elements in the header, content area, and footer toolbar.
Choosing the right floorplan is not always easy. Roughly speaking, SAP Fiori offers floorplans that:
  * Allow navigation to work on one object: **initial page**
  * List several objects: **list report** , **analytical list report** , **worklist**
  * Manage an object: **object page** , **wizard**
  * Provide an overview of information and tasks: **overview page**

The majority of floorplans are covered in the course: SAP Fiori Elements Development. There are 2 floorplans that cannot be developed using SAP Fiori elements, these are the Initial Page and the Wizard. The following two sections will cover these floorplans,
In the section that follows, there is a summary table that will direct you to any additional information you may need.
### The Initial Page Floorplan
The initial page floorplan is used when the user needs to navigate to a single object.
An interaction or starting point, is a single input field that directs the user to the object they are looking for in a few steps.
An input field might be value help, or a search as you type field.
![Screenshot of the initial page with one input field.](../images/7ec7dcd990b8fdaa.png)
The screen uses initial page floorplan to show single input field for entering a purchase order ID.
![Sample search results are shown.](../images/f06716b6a7a5c1a7.png)
The screen uses initial page floorplan to show the result of searching for the respective purchase order ID.
Do not use this floorplan when you want to show more than one object. In this case, the list report floorplan is a more appropriate solution.
In the following code, the handleValueHelp method is used to display the standard value help dialog for selecting a purchase order in the initial screen.
![Screenshot of the handleValueHelp code and the resulting dialog box.](../images/475c2c57713aa51f.png)
You can also define a specific table structure for the suggestion pane as in the following code.
![Screenshot of the sample code.](../images/36d1c9124866231c.png)
You could also define your own search dialog with a specific fragment and methods to handle Search, Confirm and Cancel user actions.
![Sample code with search and close values.](../images/2c8dc707a07343b5.png)
### The Wizard floorplan
![Sample step by step wizard.](../images/7a897763f0f8a195.png)
When to use the wizard floorplans
  * The wizard aims to help users by dividing large or complex tasks into segments. Use the wizard if the user has to accomplish a long task (such as filling out a long questionnaire) or a task that is unfamiliar to the user.
  * The flow should consist of a minimum of 3 and a maximum of 8 steps.
  * The wizard can be used for both create and edit scenarios. If your application contains both, consider using the same method for both scenarios – either the wizard, or another create or edit screen, (edit flow or object page).

When not to use the wizard floorplans
  * If you have a task with only 2 steps or a format that the user is familiar with, for example, it is part of their daily routine, do not use the wizard as it only adds unnecessary clicks to the process.
  * If your process needs more than 8 steps, the wizard will not support those steps as the process is too long and can be confusing for the user. In this case, you should consider restructuring the task.
  * Consider if the classic edit screens (edit flow or object page), are more suitable for your use case.

Structure of the wizard floorplan walk-through screen.
  1. After calling the wizard, the first step of the floorplan appears.
  2. When all necessary fields are completed, a button labelled Step # appears.
  3. When completing the last step, a button labelled _Review_ appears.
  4. The footer of the wizard holds the cancel button with standard SAP Fiori cancel behaviour.
  5. It is possible to have a save or draft button when the form is very long

Displayed is the structure of the wizard floorplan summary page. The review button takes the user to the screen displaying the data.
![Sample summary page, showing five steps.](../images/1ad1a875fcc2b24e.png)
### Summary Table
In this table, you can see each Floorplan summarized. Please refer to the following learning journey for more details: Develop SAPUI5 Applications > SAP Fiori Elements Development.
#### Floorplan Summary Table
| Floorplan  | Description  | SAP Documentation  |
| --- | --- | --- |
| Initial  | Allow navigation to work on one object.  | <https://experience.sap.com/fiori-design-web/initial-page-floorplan/>  |
| List Report  | List several objects.  | <https://experience.sap.com/fiori-design-web/list-report-floorplan-sap-fiori-element/>  |
| Worklist  | Display a collection of items and process them or delegate them to someone else.  | <https://experience.sap.com/fiori-design-web/work-list/>  |
| Object Page  | Display all the information of a simple or complex object with different facets in a responsive way.  | <https://experience.sap.com/fiori-design-web/object-page/>  |
| Wizard  | Guide the user step by step through the data editing.  | <https://experience.sap.com/fiori-design-web/wizard/>  |
| Overview Page  | Provide an overview of information and tasks  | <https://experience.sap.com/fiori-design-web/overview-page/>  |
### Connect with Marco Rossi
Now that you've learned about the SAP Fiori floorplans, put on your thinking cap and help Marco make the right decision in this use case activity.
[Continue to quiz](https://learning.sap.com/courses/ui-development-with-sap-fiori/applying-sap-fiori-design-guidelines_aad4ebc8-85b6-392b-89d4-974bdebde8ab)
