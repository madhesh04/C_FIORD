# Using SAP Fiori Launchpad

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/using-sap-fiori-launchpad_a9103226-f903-4afb-b471-c07be29c59e3*

# Using SAP Fiori Launchpad
Objectives
After completing this lesson, you will be able to:
  * Identify the features of the SAP Fiori launchpad
  * Identify the clients and integration options for SAP Fiori

## Evolution
![Tablet showing SAP Fiori launchpad with tasks and activities for finance, human resources, sales, and procurement. Four circles with colored blocks represent different departments, each connected to the tablet.](../images/290a1d63a1c278d5.png)
The SAP Fiori launchpad (FLP) offers a coherent user experience across different enterprise solutions by utilizing the capabilities of the user role to combine the decomposed apps in one surface. Each app represents one individual step for one specific role. Therefore, several apps combined represent a complete process covering different enterprise solutions and systems. This is a shift from monolithic solutions to activity-based apps and a role-based simplification of business processes.
### From SAP Fiori 1.0 to SAP Fiori 2.0 to SAP Fiori 3
SAP Fiori is continuously evolving and the evolution continues.
Watch the video to learn how SAP Fiori shifted the approach from monolithic solutions to activity-based apps and a role-based simplification of business processes.
Loading
Play
00:00
Play
Seek 10 seconds backwards
Seek 10 seconds forward
00:00 / 00:00
Mute
Click to volume controlUse the arrows to control the volume
Turn on Picture in picture
Show Full screen
### SAP Fiori Horizon
![Screenshot of My Home in the SAP Fiori Launchpad with Horizon showing four sections: To dos, pages, apps, and insights.](../images/e047caed43b0f073.png)
With SAP S/4HANA Cloud 2208, SAP Fiori Horizon is available to customers. SAP decided to no longer count the version of SAP Fiori. Instead, the name of the design theme is used. But it is not just a new theme, it includes new features and functions for the FLP, too. The theme itself is called Horizon and introduces signature design elements to provide a better focus on important parts on the screen.
A new feature is the completely reworked _My Home_ page. It provides several sections with new options of what the user can see and start in the FLP.
  * Tasks and situations are shown as _To Dos_.
  * _Pages_ can be accessed directly without opening the space first.
  * Recently or frequently used _Apps_ and favorites can be started directly.
  * Users can define _Insights_ into analytical data as tiles or cards.

All sections of the _My Home_ page can be personalized by the user.
Note
For more information about this topic, see:
  * SAP Fiori (Community)
<https://pages.community.sap.com/topics/fiori>
  * Introducing SAP Fiori Launchpad for SAP S/4HANA Cloud (Learning Video)
<https://learning.sap.com/videos/introducing-sap-fiori-launchpad-for-sap-s-4hana-cloud>

## Features
![Screenshot of the user actions menu with options recent activities, frequently used, app finder, settings, my home settings, adapt UI, about, and sign out. Highlights: User name for activation, app finder for catalogs, settings for settings, and my home settings for personalization.](../images/c523198b306f3eb1.png)
The features in the _User Actions Menu_ can be configured per user role. The options for personalization can be reduced to disallowing everything or extended to adapting apps at runtime. The recent activities and frequently used apps can also be deactivated.
![Screenshot of notifications area showing alerts grouped by date with options for approval, rejection, or closing. Includes short descriptions and quick actions for each alert. Accessible via ALT+N and the bell icon.](../images/b297f4e85c3d18ac.png)
The notifications area can be enabled per user role in the _SAP Fiori launchpad_. Notifications are created by notification providers and can be based on SAP Workflow or the ABAP notification framework. They can offer quick actions and are able to start a suitable app showing details for the notification topic.
## Accessibility
_SAP Fiori launchpad_ provides more features such as context-sensitive User Assistance, Quick Tour, and keyboard shortcut.
We will explore each feature in detail. To begin with, let's look at how SAP Fiori provides context-sensitive assistance to users.
![Screenshot of the context-sensitive User Assistance on the SAP Manage Banks app, showing options to manage bank hierarchies and displaying bank keys, account numbers, and categories. Help topics and detailed explanations are visible.](../images/75abb05f75bc5924.png)
_SAP Fiori launchpad (FLP)_ offers help functionality that includes a guided tour for an app. This context-sensitive User Assistance can be started via the question mark in the upper right corner or by pressing F1. A help panel consisting of help topics shows up to the right of the app as well as bubbles pointing out the key elements inside the app. By selecting a topic or a bubble, an information pop-up appears, offering more information about the functionality.
The help content for this User Assistance is provided by the SAP Content Server hosted by SAP, an SAP Enable Now Manager hosted by the customer, or a mixture of both. This also includes access to learning material available in the Learning Center.
Watch the video to get an overview of the Quick Tour pop-up.
Loading
Play
00:00
Play
Seek 10 seconds backwards
Seek 10 seconds forward
00:00 / 00:00
Mute
Click to volume controlUse the arrows to control the volume
Turn on Picture in picture
Show Full screen
Watch the video to explore the keyboard navigation of SAP Fiori Launchpad.
Loading
Play
00:00
Play
Seek 10 seconds backwards
Seek 10 seconds forward
00:00 / 00:00
Mute
Click to volume controlUse the arrows to control the volume
Turn on Picture in picture
Show Full screen
## Client Integration
![Chart of SAP Fiori clients and SAP Fiori integration. Clients include Web browser, SAP Business Client, and SAP Mobile Start. Integration includes SAP Build Work Zone, SAP Enterprise Portal, and SAP Mobile Services.](../images/07ab742d4c3e3e73.png)
There are three clients available to access SAP Fiori:

Web Browser

Any HTML5-ready browser can be used.

SAP Business Client

As of _SAP Business Client 6.0_ , you can create _SAP Fiori launchpad_ system connections.

SAP Mobile Start
    You can access SAP Build Work Zone, standard edition web sites providing apps based on cloud and on-premise SAP solutions.
You can also integrate SAP Fiori in other system areas to add more values like logon features or increased distribution range. Details and benefits of these integration options are discussed later or considered in more depth in other trainings:
  * SAP Build Work Zone
  * SAP Enterprise Portal
  * SAP Mobile Services

Now, let's explore each client in detail.
![A diagram showing the original and the cache buster URL of the SAP Fiori launchpad with ABAP transaction /UI2/FLP in the middle pointing to both URLs.](../images/22990db5bcffb00d.png)
The original way to start an FLP is to enter the URL https://<host>:<port>/sap/bc/ui5_ui5/ui2/ushell/shells/abap/FioriLaunchpad.html in an HTML5-ready browser. This URL has been available since the beginning of SAP Fiori. Over time, SAP added more options to start the launchpad.
Many customers access SAP software via a logon to an Application Server ABAP (AS ABAP). Therefore, the transaction /UI2/FLP is added. With this transaction, you can log on automatically with the credentials you used to log on to the AS ABAP. This approach is for users working in both worlds, ABAP transactions and SAP Fiori web apps, if no business client is available.
Note
By default, transaction /UI2/FLP starts the FLP via the Internet Communication Manager (ICM) process of your application server instance. An entry in the database table HTTPURLLOC can be used to call a reverse proxy, such as SAP Web Dispatcher.
The current URL to start the FLP is https://<host>:<port>/sap/bc/ui2/flp. This URL is much shorter than the original one so it is easier to memorize. Even more important is the cache buster feature. This technique causes web browsers to load content from the server rather than from the browser cache if activated. The cache buster for SAP Fiori uses versioned URLs containing tokens to signal the browser that new resources are available on the server. Instead of forbidding caching or setting a lifetime for the resources, the system invalidates the cache only when resources are actually updated on the server.
![Screenshot of a system entry in SAP Business Client, showing fields like name, description, type, system, message server, web dispatcher, URL, client, language, SAP GUI type, and SAP GUI logon description, with the SAP Fiori launchpad URL highlighted.](../images/1fcd8a5d3ad70a71.png)
_SAP Business Client_ makes it possible to access SAP GUI and web applications in one client software. Therefore, in _SAP Business Client 6.0_ , the ability to add system connections for FLP was introduced. The benefit is the end user only needs one tool to access all the functions of an AS ABAP. It is even possible to start ABAP transactions in the FLP, which opens a new SAP GUI tab in the _SAP Business Client_. SAP Logon is completely integrated in _SAP Business Client_.
Hint
For _SAP Business Client 6.0_ , the term NetWeaver was dropped from the name. Previous releases are still called _SAP NetWeaver Business Client (NWBC)_.
![Screenshots of the SAP Mobile Start on five devices display various SAP app features including a task list, important applications, and notifications. The image highlights key sections: Start, search, applications, widgets, and notifications on different devices.](../images/eed82c84725297ee.png)
_SAP Mobile Start_ was introduced in August 2021. It is a mobile application for Apple iOS and Google Android integrated with SAP S/4HANA and further SAP solutions, leveraging the SAP Business Technology Platform (BTP). The SAP Build Work Zone, standard edition, Notification service, and Mobile Services of BTP work together to provide web sites and apps for mobile usage. SAP Mobile Start integrates with mobile operating system features like notifications, spotlight search, and widgets running on smartphones, watches, and tablets.
## Prepare the SAP Learning System
### Business Example
In your SAP Learning system, you want to log in to the _SAP Secure Login Client_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Prepare the SAP Learning System
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_4AA0D78C4DC713B1:uebung)
#### Steps
  1. Log in to your SAP Learning system.
    1. Follow your system setup guide.
  2. In your SAP Learning system, log in to the _SAP Secure Login Client_.
    1. In the Windows taskbar, choose _SAP Secure Login Client_.
    2. In the _SAP Secure Login Client_ window, right-click _SAP AS Java Authentication_ and choose _Log In…_.
    3. In the _User name_ field, enter your user name.
    4. In the _Password_ field, enter your password.
    5. Choose _OK_.
#### Result
You can now log into your SAP S/4HANA system using SAP Logon, SAP Business Client, or a Web browser via Single Sign-On (SSO).

## Operate SAP Fiori Launchpad
### Business Example
You want to start the _SAP Fiori launchpad_ of your SAP S/4HANA system in a Web browser and in the _SAP Business Client_.
You want to operate the _User Actions Menu_ and the _Notification Area_ of the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Start the SAP Fiori Launchpad in Different Clients
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_FE403F9A4087A085:uebung)
#### Steps
  1. Start the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system in a Web browser and check the _Quick Tour_.
    1. In the Windows start menu, choose a Web browser.
    2. In the Web browser favorites, choose the _SAP Fiori launchpad_ of your S4H.
    3. Check the content of the _Quick Tour_.
    4. Close the _Quick Tour_ popup.
  2. Start the _SAP Fiori launchpad_ of your S4H in the _SAP Business Client_ and examine the system entry.
    1. In the Windows start menu, choose _SAP Business Client_.
    2. In _SAP Business Client_ , select the _SAP Fiori launchpad_ of your S4H.
    3. Choose _Edit_.
    4. Examine the system entry.
    5. Choose _Cancel_.
    6. Choose _Log On_.

### Task 2: Check and Operate SAP Fiori Reference Apps
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_192E761E3776D1A9:uebung)
#### Steps
  1. Examine the _SAP Fiori launchpad_ information dialog box for the SAP Fiori reference app _Shop_.
    1. In the _SAP Fiori launchpad_ , choose the _Reference Apps_ anchor.
    2. Choose the _Shop_ tile.
    3. Choose your user in the upper right corner.
    4. Choose _About_.
    5. Examine the app information.
    6. Choose _OK_.
  2. Buy a product in the SAP Fiori reference app _Shop_ and access your purchase order via the notification in the _SAP Fiori launchpad_.
Note
Your user is also allowed to handle purchase orders of other users so be careful to only work with your purchase orders.
    1. In the SAP Fiori reference app _Shop_ , select a product of your choice and choose _Add to Cart_.
    2. In the upper right corner of the screen, choose _Shopping Cart_.
    3. Choose _Go to Checkout_.
    4. Choose _Buy Now_.
    5. In the upper right corner of the screen, choose _Notifications_.
    6. Select the most recent _Purchase order_.
Hint
If the purchase order does not show your product, select the purchase order of your user on the left. Remember that your user is allowed to handle all users.

Was this lesson helpful?
YesNo
[Next lesson](https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/personalizing-sap-fiori_decea017-0eda-41c1-bea9-c83627443035)
Copy debug info
Copy debug info
Copy debug info
