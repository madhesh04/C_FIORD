# Explaining Data Services

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/explaining-data-services_d3477b9d-aa60-43fd-90b3-9ef71ccf75f8*

Objectives
After completing this lesson, you will be able to:
  * Explain the OData protocol.
  * Operate an OData Service for handling data.
  * Operate SAP Gateway for handling data.

## OData Standard
![Comparison of a client with application connecting via a Web infrastructure to a server with business logic with a client with OData SDK connecting via OData services to SAP S/4HANA with SAP Gateway.](../images/3d736f2bae7461ff.png)
One important aspect of the architecture of the World Wide Web is the use of abstract interfaces for component communication. These abstract interfaces are presented as connectors. A client and a server each use a connector component. There is a contract between both connectors that defines the application protocol. It defines the documents, their format, and the behavior. Any protocol can be chosen. By using the connector concept, both client and server are largely independent and exchangeable. Each connector translates the documents exchanged on the communication channel to the internal representations both on the server and on the client side, and vice versa.
The OData protocol defines such a contract by specifying a uniform protocol that has the necessary qualities. For instance, a connector attached to an SAP back-end system translates between ABAP APIs and OData entities. SAP Gateway is such a connector.
On the other side, a client connector translates between OData entities and the APIs of the consumer platform. The connector is specified here. As a consequence, any client platform with libraries supporting the contracted OData format can communicate with any server supporting the same contract.
OData follows the Representational State Transfer (REST) architecture design paradigm in the sense that the protocol transfers representations of the state of resources. The term resource denotes data that is addressable and accessible. The standard address representation or resource is the Uniform Resource Identifier (URI). A client requests a resource from a server by sending a request to a URI. The server processes the request by translating the URI to internal address data to access or manipulate the data, and then assemble the response.
### Open Data Protocol
![Diagram explaining SAP Annotations, OData, JSON, XML, HTTP\(S\) with icons depicting their functionalities; right side lists components related to data transfer and formatting.](../images/2cc4a194bd7d6d95.png)
OData is an open standard originally developed by Microsoft but now managed by the Oasis Organization. It is based on the Atom Publishing and Atom Syndication standards, which, in turn, are based on XML (Extensible Markup Language) and HTTP(S) (HyperText Transfer Protocol (Secure)). JSON (JavaScript Object Notation) is an alternative to XML to structure data.
The objective of the OData protocol is to provide a vendor-neutral, web-based API that fully complies with the design principles of Representational State Transfer (REST). OData provides database-like access to server-side resources. In this context, OData is also called **ODBC for the Web**.
Note
Open Database Connectivity (ODBC) is a widespread database access method.
OData is also extensible. This enables SAP to supplement the data types used by OData with extra information from the ABAP Data Dictionary. Another example is metadata-driven development for Web and mobile like SAP Fiori elements.
OData is available in version 2 (V2), version 3 (V3), and version 4 (V4). The versions are built on each other extending the previous version by adding new features. Most OData services are based on V2. SAP Gateway supports OData V2 since AS ABAP 7.00 and OData V4 since AS ABAP 7.50. OData V3 was skipped in SAP Gateway and is therefore not supported.
## OData Model
![Screenshot of the comparison of XML \(Atom\) and JSON formats for product data, featuring attributes like ProductID, TypeCode, Category, Name, Description, Supplier, Price, and other specifications.](../images/9dacda27097b9d37.png)
In current real-life applications, JSON (JavaScript Object Notation) is used instead of Atom and XML for structuring data. It needs considerably less meta-information, which reduces the amount of data transferred greatly. Atom and XML, in contrast, are used precisely because of the extensive meta-information when it comes to development.
![Screenshot of the comparison of XML \(Atom\) and JSON structures highlighting BusinessPartnerSet. XML shows service tags and collections, while JSON displays a nested structure with entity sets.](../images/21b6ab2cb1ddc97e.png)
Each OData service is represented by a URI, called the service root URI. A URI is a uniform resource identifier, which is a string of characters used to identify a resource by name and address. This type of identification enables interaction with representations of the resource across a network using specific protocols like OData.
Note
The URL (Unified Resource Locator) is a subtype of a URI identifying a resource just by its address.
To consume an OData service for read, you just need a browser and the OData service base URI. The service document is the highest-level description of an SAP Gateway service. It shows the basic information about the available data. From here, it is possible to call further information on the service, and of course the data itself, by adding URI parameters.
To get data from the service, add the name of an entity set of the service to the base URI. You get a list of entities of that type, which could be the content of a database table.
![A diagram showing entity relationships among BusinessPartner, Contact, Product, SalesOrder, and SalesOrderItem, with BusinessPartner as a central node connecting to the others with cardinality notations.](../images/6b9bdd11259be1d9.png)
The entities of an OData service are defined in an Entity Data Model (EDM). Entity types define properties and navigations to other entity types. These associations define relation constraints based on key properties of the entity types. A navigation property is then used to actively navigate between entities during runtime. For every entity type, at least one entity set is defined. These are shown in the service document and used to request data from the OData service.
![Screenshot of XML code specifying the metadata for an entity type Product with various properties like ProductID, Name, Description, etc., used in an SAP OData service.](../images/7f8fd172e576059c.png)
By adding the OData option $metadata to the service root URI, the metadata document of the service is shown. The whole EDM is defined here and available at runtime. Application developers and all the wizards in development environments create their applications based on this information.
Note
The metadata document is only available as XML.
## How to Examine the Data Model of an OData Service
### Business Example
You want to examine the data model of an OData service in a web browser.
Watch the video to see how to examine the data model of an OData Service.
## OData Operations
![Table showing operations on resources with corresponding HTTP verbs: Create-POST, Read-GET, Update-PUT, Delete-DELETE.](../images/4d4cc88b2d7d98c7.png)
One of the main features of OData is that it uses the existing HTTP verbs GET, PUT, POST, and DELETE at addressable resources identified in the URI. Conceptually, OData is a way of performing database-style create, read, update, and delete operations on resources through HTTP verbs.
By building URIs based on the rules of OData, a wide variety of data requests can be performed. These requests can often be mapped directly to SQL requests accessing data in a database.
![The image illustrates an OData URL structure comprising elements like Server Address, Service URI, Entity Set, Entity Key, and Navigation Property, resulting in an XML data entry example.](../images/3d6c1a227b6e24b7.png)
Calling the service URI of an OData service in a GET request, results in the service document. Adding the name of an entity set to the base URI, results in a list or set of all entities. This is called a query request.
Adding the unique key of an entity in brackets to a query request results in a single entity having this key. Character-based keys must be put in apostrophes. This is called a read request.
Adding a navigation property of the entity type to a read request separated by a slash results in a single entity or a set of entities depending on the multiplicity of the association. This is called a navigation request.
## OData Query Language
![Comparison table showing OData version 2 and 4 query operations: Formatting: $format; Filtering: $filter; Projecting: $select; Sorting: $orderby; Paging: $top and $skip; Inlining: $expand; Counting: $inlinecount and $count; Searching: - and $search; Computing: - and $compute.](../images/16efd100d48a937b.png)
OData specifies a simple, yet powerful query language that allows a client to request arbitrary filtering, sorting, paging, and so on. A client is able to express, via query string parameters, the amount, and order of the data that an OData service returns for the resource identified by the URI. The names of all query string parameters defined by OData are prefixed with a "$" character.
First, the structure of the data transferred from the server to the client can be formatted, for example, in JSON or XML. The data volume can be reduced by filtering data sets and by selecting the relevant data properties only. Paging is another way to reduce data traffic. Sorting guarantees the right sequence of the entities within a requested entity set. A client can also instruct the server to include associated data entries in the response, which is called inlining. This technique avoids subsequent read operations.
The versions of OData are additive. New versions include features of previous versions in the same way as they were used back then. But they are enhanced with additional features. This also counts for query options. One exception here is "counting" because the two ways to count in OData V2 were combined in just one in OData V4.
In OData V4, data can also be searched and computed. Both require a specific implementation depending on the application scenario.
![The image illustrates an OData URL structure comprising elements like Server Address, Service URI, Entity Set, and Query Options, resulting in a JSON data entry example.](../images/ea831ec2ab75e99d.png)
An OData request consists of a server address, service URI, entity set, and additional query options. There are many combinations of query options possible. A full documentation is available at <http://www.odata.org>.
## How to Query Data of an OData Service
### Business Example
You want to query data of an OData service in a web browser using query options.
Watch the video to see how to query data of an OData Service.
Settings
## SAP Gateway Foundation
![Diagram showing social platforms, mobile devices, Web browsers, enterprise software, and enterprise cloud connecting via OData to SAP Gateway of an AS ABAP and SAP HANA XS of an SAP HANA.](../images/873f5c387782da04.png)
SAP offers various OData providers. SAP Gateway (up to the end of 2014 known as SAP NetWeaver Gateway) provides a single entry point to access business data of ABAP-based systems such as the SAP Business Suite or SAP S/4HANA. The SAP HANA Extended Applications Services (XS) has the same role in SAP HANA – just to name another important OData provider.
Caution
SAP Gateway must not be confused with the kernel’s **gateway** process used for communication via RFC.
By using OData, business data can be shared among multiple environments and platforms. SAP knowledge is not required for the consumption of the data. Usually client-based applications consume SAP Gateway services and interact directly with the user. Applications in a Web browser are a common example.
However, it is also possible for an SAP Gateway service to be used as an API (Application Programming Interface) by a server-based application. Additional servers can be added to the communication path to enhance the possibilities for client and server. For mobile devices, the SAP Mobile Services add additional value to the applications.
For AS ABAP 7.00 to 7.31, SAP Gateway consists of individual add-ons that provide the OData functionality. These can be divided into the following areas:

Runtime
    Provides the OData and thus the SAP Gateway service externally via the URI.

Design Time

Contains the development environment and programs for processing the requests to the service.
First introduced in AS ABAP 7.40 and finalized in AS ABAP 7.51, all add-ons are merged in the software component SAP_GWFND (SAP Gateway Foundation). This offers everything needed for the OData runtime and design time.
Note
Some SAP Gateway add-ons may still exist in an AS ABAP 7.51 after an upgrade. These are deprecated and should be uninstalled. Either their functions are now part of software component SAP_GWFND or they are no longer supported.
### SAP Gateway Deployment Options
![Diagram showing the three deployment options for SAP Gateway: Hub Deployment 1, Hub Deployment 2, and Embedded Deployment, all featuring SAP Gateway runtime connected to OData and design time in hub or back-end.](../images/ed45112c7e6d7850.png)
There are three possible deployment options for SAP Gateway (hub is a synonym for front-end server (FES)):

Hub deployment with development in back-end server (BES)
    A hub deployment offers the possibility of routing and composition of multiple back-end systems. It is the single point of access to back-end systems when using OData. This increases security and flexibility in operation.     This is the recommended setup for SAP Business Suite.

Hub deployment with development in front-end server (FES)
    When developing in the FES, data is only read via RFC-enabled function modules from the BES, which enables access to data of a BES not able to provide an OData service on its own. This grants more freedom in selecting a system as data source.     This is the recommended setup for integrating multiple BES with different releases.

Embedded deployment
    When developing in the BES, the application source code has direct access to the definition of the data and other repository objects. This increases performance and efficiency in development.     This is the recommended setup for SAP S/4HANA.
## SAP Gateway Tools
![Screenshot of SAP Gateway Service Maintenance with options like register service, test service, add system, and service catalog entries displayed.](../images/ee573b57fe8f3c74.png)
The _SAP Gateway Service Maintenance_ (transaction /IWFND/MAINT_SERVICE) provides a list of all the OData V2 services registered in the system. Complete management of the SAP Gateway services is carried out here. The transaction is divided into three areas:
  * _Service Catalog_ (service name, description, and many other settings)
  * _ICF Nodes_ (maintenance of the ICF services and testing of the service)
Hint
Since SAP_GWFND 7.58, an ICF node is optional for calling an SAP Gateway service. The OData V2 services are then directly linked to the node /sap/opu/odata.
  * _System Aliases_ (maintenance of the connection to the back-end)
Hint
For services not connecting to other systems, the _Processing Mode_ is set to **Co-deployed only** and no system alias is assigned.

![Screenshots of SAP Gateway Service Administration and SAP Gateway Backend Service Administration showing steps for service registration and publishing: Create service group, register service, add service to group, publish, test service.](../images/910e761ad656b057.png)
OData V4 services are not registered as single instances. Instead, a service group consisting of multiple services is published. These service groups are created using the _SAP Backend Service Administration_ (transaction /IWBEP/V4_ADMIN) and shipped by SAP or created by developers.
The _SAP Gateway Service Administration_ (transaction /IWFND/V4_ADMIN) is used to publish service groups so that the services inside can be consumed in applications.
Hint
The default service group /IWBEP/ALL consists of all SAP Gateway services in the BES. This makes it easier for developers to test their services in a development system. It should never be published on a productive system.
![Screenshot of SAP Gateway Client showing HTTP request with URI input, request body, and controls. Response body displays XML with status code 200 and status reason OK.](../images/d787f9b10134a731.png)
Using the _SAP Gateway Client_ (transaction /IWFND/GW_CLIENT), all functions of an OData service can be tested. For a read request, it is enough to enter the request URI and execute. For a create, update, and delete request, more adjustments must be made, for example, a request body filled with data must be created. All adjustments can be saved as test cases for later usage.
The _SAP Gateway Client_ can handle data formats like XML (Atom) and JSON for both OData V2 and V4 services.
Apart from these transactions, there are several more for SAP Gateway. All transactions are connected to each other via buttons and menu entries. Therefore, you can jump from the service maintenance to the client and back.
## Test an SAP Gateway Service Based on OData V2
### Business Example
You want to examine and test an SAP Gateway service based on OData V2 using SAP Gateway Service Maintenance and the SAP Gateway Client.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Check the Registration of an OData V2 Service in SAP Gateway
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_609EACEBF09380BD:uebung)
#### Steps
  1. Log on to your SAP S/4HANA (S4H) system using _SAP GUI_.
    1. In the _SAP Business Client_ or _SAP Logon_ , select the SAP GUI SNC system entry of your S4H.
    2. Choose _Log On_.
  2. In the _SAP Gateway Service Maintenance_ of your S4H, examine the registration of the OData V2 service **ZEPM_REF_APPS_SHOP_SRV**.
    1. On the _SAP Easy Access_ screen, search for _Activate and Maintain Services_ or start transaction /IWFND/MAINT_SERVICE.
    2. Choose _Filter_.
    3. In the _Technical Service Name_ field, enter ***epm_ref*** and choose _Continue_.
    4. Choose the _Technical Service Name_**ZEPM_REF_APPS_SHOP_SRV**.
    5. Confirm that the status of the ICF Node _ODATA_ is initial.
    6. Confirm that the _Processing Mode_ is _Co-deployed only_ and no system alias is assigned.

### Task 2: Test an OData V2 Service in the SAP Gateway Client
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_A640FB6B9667DD90:uebung)
#### Steps
  1. In the _SAP Gateway Client_ of your S4H, call the service document of the OData V2 service **ZEPM_REF_APPS_SHOP_SRV**.
    1. In the _ICF Nodes_ panel, choose _SAP Gateway Client_.
    2. In the _SAP Gateway Client_ , select _HTTPS_ as _Protocol_.
    3. Choose _Execute_.
#### Result
In the _HTTP Response_ , the service document is shown as XML.
  2. Call the service metadata document of the OData V2 service **ZEPM_REF_APPS_SHOP_SRV**.
    1. In the _SAP Gateway Client_ , choose _Add URI Option_.
    2. In the _Add URI Option_ popup, double-click _$metadata_.
    3. Choose _Execute_.
#### Result
In the _HTTP Response_ , the service metadata document is shown as XML.
  3. Display all products of the OData V2 service **ZEPM_REF_APPS_SHOP_SRV**.
    1. In the _SAP Gateway Client_ , choose _Entity Set_.
    2. In the _Entity Sets_ popup, double-click _Products_.
    3. Choose _Execute_.
#### Result
In the _HTTP Response_ , a list of products is shown as XML.
  4. Display the first two products in the format JSON of the OData V2 service **ZEPM_REF_APPS_SHOP_SRV**.
    1. In the _SAP Gateway Client_ , choose _Add URI Option_.
    2. In the _Add URI Option_ popup, double-click _$format=json_.
    3. Choose _Add URI Option_.
    4. In the _Add URI Option_ popup, double-click _$top=2_.
    5. Choose _Execute_.
#### Result
In the _HTTP Response_ , the first two products are shown as JSON.

## Test an SAP Gateway Service Based on OData V4
### Business Example
You want to examine and test an SAP Gateway service based on OData V4 using SAP Gateway Service Administration and the SAP Gateway Client.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Check the Publication of an OData V4 Service Group in SAP Gateway
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_465259A8AE724D93:uebung)
#### Steps
  1. Log on to your SAP S/4HANA (S4H) system using _SAP GUI_.
    1. In the _SAP Business Client_ or _SAP Logon_ , select the SAP GUI SNC system entry of your S4H.
    2. Choose _Log On_.
  2. In the _SAP Gateway Service Administration_ of your S4H, examine the publication of the OData V4 service group **/IWNGW/NOTIFICATION**.
    1. On the _SAP Easy Access_ screen, search for _SAP Gateway Service Administration_ or start transaction /IWFND/V4_ADMIN.
    2. Expand _Service Groups_ on the left.
    3. Double-click the service group _/IWNGW/NOTIFICATION_.
    4. Confirm that the only system alias is _LOCAL_.
    5. Confirm that the only service in the group is _/IWNGW/NOTIFICATION_SRV_.

### Task 2: Test an OData V4 Service in the SAP Gateway Client
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_FD50D071C36CBA8E:uebung)
#### Steps
  1. In the _SAP Gateway Client_ of your S4H, call the service metadata document of the OData V4 service **/IWNGW/NOTIFICATION_SRV** in the _SAP Gateway Client_ on your S4H.
    1. In the services table, select _/IWNGW/NOTIFICATION_SRV_.
    2. Choose _Service Test_.
    3. In the _SAP Gateway Client_ , select _HTTPS_ as _Protocol_.
#### Result
In the _HTTP Response_ , the service metadata document is shown as XML.
  2. Call the service document of the OData V4 service **/IWNGW/NOTIFICATION_SRV**.
    1. In the _SAP Gateway Client_ , in the _Request URI_ field, delete $metadata?sap-statistics=true.
    2. Choose _Execute_.
#### Result
In the _HTTP Response_ , the service document is shown as JSON.
  3. Display all notifications of the OData V4 service **/IWNGW/NOTIFICATION_SRV**.
Hint
You can create notifications by ordering or rating a product in the _Shop_ reference app in the _SAP Fiori launchpad_.
    1. In the _SAP Gateway Client_ , choose _Entity Set_.
    2. In the _Entity Sets_ popup, double-click _Notifications_.
    3. Choose _Execute_.
#### Result
In the _HTTP Response_ , a list of notifications is shown as JSON.
  4. Display the _CreatedAt_ , _SensitiveText_ , and _Actor_ of the first two notifications of the OData V4 service **/IWNGW/NOTIFICATION_SRV**.
    1. In the _SAP Gateway Client_ , choose _Add URI Option_.
    2. In the _Add URI Option_ popup, double-click _$top=2_.
    3. In the _Request URI_ field, add &$select=CreatedAt,SensitiveText,Actor to the URI.
#### Example
/sap/opu/odata4/iwngw/notification/default/iwngw/notification_srv/0001/Notifications?$top=2&$select=CreatedAt,SensitiveText,Actor
    4. Choose _Execute_.
#### Result
In the _HTTP Response_ , the first two notifications with _Id_ , _CreatedAt_ , _SensitiveText_ , and _Actor_ are shown as JSON.
