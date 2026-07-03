# Understanding SAP Fiori Elements Templates

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/getting-an-overview-of-the-available-templates_b22c0190-714a-47e6-8609-e7fd6fe9bc49*

Objective
After completing this lesson, you will be able to distinguish the available SAP Fiori elements templates.
## SAP Fiori Elements Templates (or Floorplans)
SAP Fiori elements provides templates for common business use cases. Most business scenarios include providing an overview of business data, listing business objects, and managing or processing these business objects.
You can use these templates for your SAPUI5 applications without having to write a line of code. SAP Fiori elements apps are based on app metadata, OData annotations, and settings in the manifest.json file. The application determines what data is displayed on the UI, but it is the templates that determines how the data is displayed on the UI.
You can easily create apps using the SAP Fiori elements templates. Let's take a look at the templates available in SAP Fiori elements.
### Overview Pages
The overview page template provides a data overview for a certain business area or role. Information is visualized in card format. The user can view, filter, and act on data efficiently. There are different types of cards to represent different types of content. A card serves as a typical entry point for a business process.
![User interface of an overview page](../images/a74b37538b743aa9.png)
### List Report Page
The list report page is the most commonly used template. It creates an SAP Fiori elements application containing a list report and an object page.
The list report allows the user to filter and sort a large set of items in a list format. It combines powerful functions for filtering large lists with different ways of displaying the resulting list of items. It is often an entry point for navigating to the item details. The item details are shown on the object page. The list report is usually used in conjunction with an object page.
![User interface of a list report](../images/7ddcec155cb62321.png)
There are other variations of the list report: the worklist page and the analytical list page. You can either create a worklist page or an analytical list page from a template, or you can modify the list report accordingly.
The analytical list page adds analytical capabilities like charts and visual filters to your apps. They help you to visualize and analyze your data from different perspectives, drill down into the data, and act on transactional content.
![User interface of an analytical list page](../images/2e7e1fedc49f0c8a.png)
The worklist page allows you to process a list of tasks. You can work through a list of items, review the details, and take necessary actions. The filter bar is hidden as there is no need for sophisticated filtering.
![User interface of a worklist](../images/fdefee8553fef24d.png)
### Object Page
The object page is used to display and categorize the relevant information about a business object. This information can consist of text, charts, graphs, images, or any other form of data. The categorized content can be accessed quickly using anchor navigation or tab navigation, and users can switch from display to edit mode to change the content. The object page comes with a flexible, responsive layout, and a dynamic page header that can adapt to displaying simple and complex business objects.
![User interface of an object page](../images/b5f4d086315748b2.png)
### SAP Fiori Elements Boosts Your Productivity
SAP Fiori elements provides enterprise-ready app templates. SAP Fiori elements ensures that the apps created using the templates comply with the latest SAP Fiori design guidelines and includes uniform layout, navigation, search, and filtering. Thus, you achieve UX consistency in your apps when using SAP Fiori elements.
By using the templates, SAP Fiori elements lets developers focus on the business logic and back-end services without having to worry about writing UI code. Thus, the development and maintenance effort can be reduced.
### Summary
You have learned about the various SAP Fiori elements templates or floorplans.
