# SAP Fiori Launchpad

*Source: https://learning.sap.com/courses/ui-development-with-sap-fiori/understanding-the-sap-fiori-launchpad_d5c9eec8-ad89-4d9f-b754-0ae2f273ca7a*

Objective
After completing this lesson, you will be able to understand the SAP Fiori launchpad
## SAP Fiori Launchpad
Julie has built the SAP Fiori app that complies with all SAP Fiori guidelines and is based on user requirements.
So what comes next?
![Introduction to the need for the SAP Fiori Launchpad.](../images/2942614d9a6b80f1.png)
Marco and Julie both agree that SAP Fiori apps need to be launched from SAP Fiori Launchpad. Let's see why and how?
### General Concepts of the SAP Fiori launchpad
The SAP Fiori launchpad home page is the first page that users see after they have logged in. It is the main entry point to SAP Fiori apps on both, mobile or desktop devices.
The launchpad home page presents tiles that allow the launch of apps, and may show additional information. The page can be personalized. Tiles can be added or removed and bundled in groups.
The home page is provided by the SAP Fiori launchpad. Apps use this home page and do not design their own.
Apps can use the following services offered by the SAP Fiori launchpad:
  * Settings (apps only): Each app can provide app-specific settings to the launchpad.
  * User Preferences: This service provides details about the user currently logged in to the app. In addition, it offers theme selection.
  * Contact Support: You can offer a Contact Support option as a channel for user incidents. Note, that this option is only available if the customer configures the support setup.
  * Give Feedback: This service allows users to give feedback on the app. Note, that this option is only available if the customer configures the feedback setup.
  * About (apps only): This option is automatically available for all apps. It provides technical details about the app.

Apps can use the following services offered by the SAP Fiori launchpad:
  * Log In / SSO / Log Out: All aspects of logging in and out are handled by the launchpad. If single-sign-on (SSO) is used, no user password is required. If SSO is not used, the launchpad provides a login screen.
  * Save as Tile: This service allows users to save a snapshot of the app as a tile on the launchpad. The tile bookmarks the current state of the app.
  * Navigation: SAP Fiori Launchpad handles all navigation between apps.

SAP Fiori 3.0 is the next significant step in our evolution of user experience for business applications: an award-winning new design concept along with a delightful new visual theme and fully new SAP Fiori Launchpad user experience.
Key capabilities include:
  * New delightful visual theme: SAP Quartz
  * SAP Fiori 3 SAP Fiori launchpad does not use viewports anymore
  * Notifications – with connection to SAP Business Workflow and My Inbox
  * Merged header: only one header bar, giving more space for each app
  * New SAP Fiori elements: overview page, list report, object page, analytical list page

![The figure shows possibilities of SAP Fiori 3.0.](../images/748e056ecd3c4dcb.png)
The figure shows possibilities of SAP Fiori 3.0.
![The figure shows the access points in SAP Fiori 3.0 about news in SAP Fiori 3.0. See the URLS below.](../images/386274ed87dded75.png)
You can find details on how to configure the notification center at:
<https://blogs.sap.com/2017/02/13/leading-s4hana-ux-notification-center-part-1-activation/>
<https://blogs.sap.com/2017/02/14/leading-s4hana-ux-notification-center-part-2-providing-notifications/>
![The figure shows different business notifications in the SAP Fiori Launchpad.](../images/77375613ba5479d6.png)
Business notifications can be opened by choosing the respective icon.
The launchpad groups related apps on tab bars to display one group at a time on the homepage.
The launchpad now offers contextual help.
Lets users get started quickly and stay up-to-date easily.
User assistance is part of the attractive, simple, and enjoyable user experience.
  * Instant: exactly when the user needs it
  * Context-sensitive: exactly what is needed
  * Seamless: within the target application
  * Productivity: interactive user guidance

A tile is a container that represents an app on the SAP Fiori launchpad home page. All apps have at least one tile, except for fact sheets, (though users can also save fact sheets as tiles if they want). Tiles are only used for launching apps and presenting them on the launchpad.
Tiles can contain an icon, a title, an informative text, numbers, and charts.
The number of visible tiles on the launchpad home page depends on the screen resolution.
Tiles can be grouped
There is a variety of types of tiles:
  * KPI Tile
  * Comparison Chart Tile
  * Mini-Charts like Bullet Chart, Trend Chart, Column Chart
  * Basic Launch Tile
  * Monitoring Tile
  * SAP Jam Tile
  * Feed Tile

![The figure shows the details of a tile.](../images/d968d9e205213bd1.png)
A tile consists of:
  * Header Area (Mandatory)
  * Subtitle
  * Content Area (Mandatory)
  * Status Area

An app finder is available to search for a specific app.
![Screenshot of the App Finder.](../images/09e319f27c8a678f.png)
