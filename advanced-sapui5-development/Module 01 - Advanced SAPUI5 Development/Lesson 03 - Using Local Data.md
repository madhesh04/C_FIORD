# Using Local Data

*Source: https://learning.sap.com/courses/advanced-sapui5-development/using-local-data*

Objective
After completing this lesson, you will be able to use Local Data to design and test application.
## Remote vs. Local OData Services
### Scenario
As a Business Process owner, you are asked to continually improve the user experience in your area of responsibility.
Creating user interfaces is a critical aspect of the user experience. In this training, you will learn how to develop SAPUI5 user interfaces to facilitate a greater user experience.
But the major part of an application resides in its business logic, which is provided by the OData Service.
### Remote Data Use Case
#### The following are some basics about remote data use cases:
  * Most applications will be built using remote data:
In other words, the model will access data that resides on a server such as an SAP system and accessed through an SAP Gateway OData service.
  * Someone will create an OData service(s) consisting of the following:
    * Collections
    * Properties
    * Associations
  * The code that you write in the SAPUI5 application will make use of these entities.

### Local Data Use Case
#### There are a variety of reasons a developer may want to create and use local data during the development cycle:
  * Sometimes, a developer has to work offline.
  * A developer is impacted by poor development server performance.
  * Developers want to perform a quick test without creating the live entities needed on the backend server (Gateway).
  * Technically, what is being shown here could be used in a production application as well.
  * Production applications could fetch some of their data from local files instead of enduring the overhead of making remote requests:
For example, local data could be used for lookup tables/lists.

### Accessing the Metadata
If you are working offline, for example, you won't be able to directly reference the OData Service in your project. But you still need to get the structure(metadata) of the service that will be used by the UI.
In order to add this service metadata to your project, you first need to access it.
Watch the following video to learn how to access an OData Service metadata:
### Adding the Metadata to the Project
Once you have the metadata file, you can add it to your project.
Watch the following video to learn how to import this metadata into your project:
### Editing the Metadata
Sometimes, when you are implementing an OData-Service based application, the service implementation is not finished or even did not start yet. To create or to adapt an existing metadata file, SAP Business Application Studio provides a text editor with intellisense.
![Screenshot of the text editor, showing an OData Service metadata.xml file.](../images/ee3231ff8afd921a.png)
### Getting Local Data
Getting the metadata is one thing, but you might want to be able to test your application with real data.
You can then query the OData Service to get some data and import this data into your project. This data file then needs to be in JSON format.
Watch the following video to see how to query data in JSON format:
Then watch the following video to learn how to best add the data file into your project:
## Explore the data model of an existing application
### Business Example
In the following exercise, you will explore the data model of a Full-screen Application with SAPUI5.
### Prerequisites
You should have completed the first exercise of this unit to import the full screen application.
### Steps
  1. Explore the service metadata.
What are the entity sets provided by this OData Service ?
    1. Expand the localService sub folder.
    2. Open the metadata.xml file. Look for the EntityType tags and note their names.
Note
The four entity sets provided are the following :
UX_C_Booking_TP
UX_C_Carrier_TP
UX_C_Connection_TP
UX_C_Flight_TP
  2. Explore the data files.
For which entities are the sample data provided?
    1. Expand the data sub folder.
    2. Look at the three provided files.
Note
The sample data is provided for the following entity sets :
UX_C_Carrier_TP
UX_C_Connection_TP
UX_C_Flight_TP
