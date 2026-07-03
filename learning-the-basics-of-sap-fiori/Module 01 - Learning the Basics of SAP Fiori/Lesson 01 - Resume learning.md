# Resume learning

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/personalizing-sap-fiori_decea017-0eda-41c1-bea9-c83627443035*

Objectives
After completing this lesson, you will be able to:
  * Explain the structure of the SAP Fiori launchpad
  * Personalize My Home.
  * Personalize SAP Fiori pages.

## Settings
End users can personalize their own variant of the _SAP Fiori launchpad (FLP)_. The settings can be accessed via the _User Actions Menu_. You can get information about the user account, appearance, language, and region.
![The screenshot shows the Language and Region settings popup in the SAP Fiori launchpad. Settings are accessed via the user actions menu.](../images/72474c5aa2bab96a.png)
Depending on the configuration of the FLP for the user, the following settings can be changed:
  * Selection of design theme
  * Switch between spaces and home page
  * Activation of user profiling
  * Settings around language and region
  * Maintenance of default values
  * Appearance and behavior of notifications
  * Configuration of personalized search

![Screenshot flow of SAP Fiori launchpad showing steps to set a default value for bank key and its effect in the app Manage Banks app.](../images/cb5daa046a5e3a7b.png)
The default values in the FLP settings can be used to set initial values for selection fields when starting applications. The only exception is ABAP transactions, which still rely on the SET-/GET-parameters in SU3/SU01 transaction.
When a user starts the FLP the first time, all SET-/GET-parameters from his back-end user account are copied to the default values. This should make it easier for new users previously working in SAP GUI to step into SAP Fiori. Unfortunately, this only happens once.
The default values can be single, several or even a range of values. The changes of single values are copied to the SET-/GET-parameters, but not the additional values or ranges. It is recommended to only use the default values in SAP Fiori. For more details, please read SAP Note [2519765](https://me.sap.com/notes/2519765) – _Synchronization of Fiori User Default Values with Backend SET-/GET-Parameters_.
## Change Settings in the SAP Fiori Launchpad
### Business Example
You want to change settings in the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Change Settings in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_8E2053404066FCBA:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system, change its theme to one of your choice.
    1. In the _SAP Fiori launchpad_ of your S4H, choose your user in the upper right-hand corner.
    2. Choose _Settings_.
    3. In the _Settings_ window, choose _Appearance_.
    4. Select a _Theme_ of your choice.
    5. Choose _Save_.
#### Result
The new theme is applied to the _SAP Fiori launchpad_.
  2. Change the language of the _SAP Fiori launchpad_ to one of your choice.
    1. Choose your user in the upper right corner.
    2. Choose _Settings_.
    3. In the _Settings_ window, choose _Language and Region_.
    4. Select a _Language and Region_ of your choice.
    5. Choose _Save_.
#### Result
The _SAP Fiori launchpad_ reloads in the selected language.

## Structure
Since SAP S/4HANA 2020, the spaces concept can be used to structure the _SAP Fiori launchpad_. A space is visualized as a ribbon or tab at the top of the FLP and defines a frame for one or more pages. A page consists of sections showing tiles in the same way as groups have done before.
![Diagram illustrating that tiles are distributed from catalogs via pages and spaces to the FLP.](../images/4171f3b10e13db28.png)
Tiles are organized in catalogs in the system. These catalogs hold all technical information to start an application. To show a tile in the FLP, it is embedded in a page. Pages are then assigned to spaces, which define the structure of the FLP for a user.
Spaces and pages are defined centrally in the system, but only spaces can be assigned to roles. Sections are an integral part of pages and can also be created by the user in their launchpad.
Hint
You can activate spaces in the _SAP Fiori launchpad_ settings under _Spaces and Pages_.
Note
Since SAP S/4HANA 2021 FPS01, the _SAP Fiori launchpad_ home page concept using groups is deprecated. For more information, please read SAP Note [3500249](https://me.sap.com/notes/3500249) – _SAP S/4HANA Cloud Private Edition and SAP S/4HANA: Replacement of Groups (deprecated) by Spaces and Pages_.
Let's see how the _SAP Fiori launchpad_ can be further personalized. Applications require an app descriptor if they are to be called from the _SAP Fiori launchpad_.
Watch the video to learn about the SAP Fiori app descriptor.
Settings
## Personalization of My Home
The first version of _My Home_ in SAP Fiori 1.0 was a business group part of the only existing page. With the introduction of SAP Fiori spaces, _My Home_ grew to an SAP Fiori page, where the user could create sections and add tiles in various sizes. With SAP Horizon, a completely reworked _My Home_ was introduced including many new personalization options.
![Screenshots showing navigation to My Home Settings from to-dos, pages, apps, insights, and the user actions menu, leading to the My Home Settings popup.](../images/12bc9457ff4f1bab.png)
_My Home_ consists of four sections:
  * _To-Dos_
  * _Pages_
  * _Apps_
  * _Insights_

Next to each section header, a small arrow opens a menu offering more functions for the section and access to the _My Home Settings_. The _My Home Settings_ button in the _User Actions Menu_ leads to the same popup.
In _Layout_ , the four sections can be rearranged or hidden. _Pages_ , _Insights Tiles_ , and _Insight Cards_ allow you to define the elements seen in _My Home_. In _Advanced_ , it is possible to export and import the personalized content.
![Step-by-step guide illustrating how to add apps to My Home either from the app finder or from another page using the Edit Current Page option in the SAP Fiori Launchpad.](../images/78dfd2197cd24d3c.png)
The only section missing in the _My Home Settings_ is _Apps_. Apps are managed directly in _My Home_. You can add apps as favorites in two ways:
  1. Choose _Add Apps_ in the _Apps_ section to open the app finder and select an app from a catalog.
  2. On an _SAP Fiori page_ assigned to your user in FLP, choose _Edit Current Page_ in the _User Actions Menu_ and choose _Add to My Home_ in the context menu of a tile.

The first way comes in handy if you browse all apps assigned to you without concerning, if the app is already part of any page. It is a search for functionality rather than process. The second way instead allows you to bring an app in the foreground, which may be the start of a bigger process the user regularly runs from a page. It is about getting faster access to this process.
![Flowchart showing steps to create a group in My Home. Create a group manually or by dragging and dropping items, select items from favorites, and manage group settings like renaming or changing color.](../images/fc5374d57f181d1f.png)
App favorites can be organized in app groups in the _Apps_ section. There are two ways to achieve this. The prerequisite for both ways is that the apps are already added as favorite:
  1. Choose _Create Group_ in the context menu of the _Apps_ section, enter a group name and color, and select the apps from the list of favorites.
  2. Drag and drop an app favorite onto another one and enter a group name and color.

After the app group was created, extra apps can be added or removed and the name and color can be changed via the context menu of the app group. The _Delete_ button deletes the app group and favorites. The _Remove All Apps_ button instead deletes the app group but keeps the apps as favorites.
## Personalize My Home
### Business Example
You want to adapt the sections, pages, and apps of your _My Home_ of the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Adapt My Home
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_DFBC19C74447BF8C:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system, in your _My Home_ , hide the _Insights Tiles and Cards_ section.
    1. In the _SAP Fiori launchpad_ of your S4H, in your _My Home_ , choose your user in the upper right-hand corner.
    2. Choose _My Home Settings_.
    3. In the _My Home Settings_ popup, for _Insights Tiles and Cards_ , choose _Hide_ on the right.
    4. Choose _Close_.
#### Result
The _Insights Tiles and Cards_ section disappeared.
  2. In your _My Home_ , hide all pages of the _Line of Business_ space.
    1. In your _My Home_ , choose _More_ (arrow pointing down) next to _Pages_.
    2. Choose _Manage Pages_.
    3. In the _My Home Settings_ popup, choose _Hide_ for all pages part of _Line of Business_.
    4. Choose _Close_.
#### Result
All pages from _Line of Business_ disappeared from the _Pages_ section.
  3. In your _My Home_ , create the group _Banking_ consisting of the tiles for the apps _Manage Bank Accounts_ and _Manage Banks_.
    1. In your _My Home_ , choose _Add Apps_ on the right.
    2. In the _Search in catalog_ field, enter **bank** and choose _Search_.
    3. Select the "+" icon of the _Manage Bank Accounts_ and _Manage Banks_ tile.
    4. Choose _Navigate to Home_ (SAP Logo).
    5. Drag and drop the _Manage Banks_ on the _Manage Bank Accounts_ tile.
    6. In the _Create Group_ popup, in the _Create Group_ field, enter **Banking**.
    7. Select a color of your choice.
    8. Choose _Create_.
    9. In the _Banking_ popup, choose _Close_.
#### Result
The _Banking_ group with two apps was created in the _Apps_ section.
  4. In your _My Home_ , add the tile for the app _Query Browser_ as favorite originating from the _General_ page of the _Cross Topic_ space.
    1. In your _My Home_ , choose the _General_ page.
    2. Choose your user in the upper right-hand corner.
    3. Choose _Edit Current Page_.
    4. For the _Query Browser_ tile, choose _Tile Actions_ (three dots).
    5. Choose _Add to My Home_.
    6. Choose _Close_ in the lower right.
    7. Choose _My Home_.
#### Result
The _Query Browser_ is now part of the favorite apps.

## Personalization of Pages
![Screenshot flow showing the process to add a tile in SAP Fiori Launchpad by navigating through the user actions menu to Edit Current Page or the App Finder.](../images/df33b777391056a5.png)
To enter the action mode for personalization of a page, choose _Edit Current Page_ in the _User Actions Menu_ of the FLP. In this mode, sections can be added, hidden, and deleted. Tiles can be removed and new ones can be created and rearranged. When adding a new tile to a section in the action mode or choosing _App Finder_ in the _User Actions Menu_ , the app finder is shown. Here, the user can choose tiles from all catalogs assigned to their user role.
![Screenshot flow showing different tile types labeled wide tile, \(basic\) tile, link, flat wide tile, and flat tile. Conversion options are displayed, such as Convert to Link, Convert to Flat Tile, and others.](../images/9b7737ee8a674443.png)
There are five different tile sizes possible on pages, showing less information the smaller the tile gets:
  * (Basic) Tile
  * Wide tile (since SAP S/4HANA 2021 FPS01)
  * Flat tile (since SAP S/4HANA 2021)
  * Flat wide tile (since SAP S/4HANA 2021)
  * Link (tile)

(Basic) Tiles and wide tiles have the same height, show all available information, and are arranged in the same line(s). Analytical and news tiles are special types of (wide) tiles showing even more information.
Flat (wide) tiles only show the title, icon, and preview data. They are arranged in their own line(s) separated from (wide) tiles.
Links are the smallest "tiles" showing only the title and subtitle. They are arranged in their own line(s) separated from all other tiles. They are quite useful to save space on the screen, especially if no preview data is available or needed.
Hint
You can transport FLP and application personalization data to another system. The /UIF/MIGRATE_FES_PERSO report allows you to collect the personalization data and writes these to transport requests. For more information, please read SAP Note [2789848](https://me.sap.com/notes/2789848) – _Migration report for homepage and application personalization_.
## Classic UI Integration
![The screenshots compare three SAP layouts: SAP Belize, SAP Morning Horizon, and SAP Quartz Light. The different layouts display various apps and pages related to analytics, data migration and other topics.](../images/700962812f38d7d1.png)
The SAP Fiori themes SAP Belize (Deep) (introduced with SAP Fiori 2.0), SAP Quartz Light/Dark (introduced with SAP Fiori 3), and SAP Fiori Morning/Evening Horizon are not only a design for HTML-apps like SAPUI5, but also for applications running in SAP GUI. Beside changing colors and font, using one of these themes in SAP GUI does also change the structure of the UI.
![Screenshots of the comparison between the SE16 screen in Blue Crystal theme and Horizon theme showing locations of generic actions, app specific actions, and finalizing actions.](../images/6e19b12143bdb04e.png)
Well-known functions such as SAVE or BACK change their position according to the rules of SAP Fiori. Finalizing actions are defined in the SAP Fiori design guidelines to be visible in the lower-right corner or the BACK button must be in the upper left corner. This all works out-of-the-box by using the SAP Belize or SAP Quartz theme with SAP GUI.
SAP Belize is available as of _SAP GUI for HTML_ with SAP Kernel 7.49 and _SAP GUI for Windows 7.50_ , but only if the user connects to an SAP S/4HANA 1610 or a newer SAP S/4HANA release. With _SAP GUI for Windows 7.60_ , SAP Belize is available for all SAP products.
SAP Quartz is available as of _SAP GUI for HTML_ with SAP S/4HANA 1909 and _SAP GUI for Windows 7.70_. A full documentation of all designs for SAP GUI and their prerequisites is available in SAP Note [710719](https://me.sap.com/notes/710719) – _SAP GUI family and visual designs ("themes")_.
Hint
In _SAP GUI for Windows 7.70_ , it is also possible to replace _Microsoft Internet Explorer_ with _Microsoft Edge_ as the default HTML-control. For more information about this topic, read SAP Note [2913405](https://me.sap.com/notes/2913405) – _SAP GUI for Windows: Dependencies to browsers / browser controls_.
SAP Horizon is available as of _SAP GUI for HTML_ with SAP S/4HANA 2023 and will be available with _SAP GUI for Windows 8.10_.
### SAP Easy Access Menu
Adding transactions to the FLP has been possible since the release of SAP Fiori 1.0. However, in SAP Fiori 2.0, with the automatic adaptation of the design and behavior of SAP GUI to SAP Fiori, it is even more attractive.
![Screenshot flow showing how a user navigates the SAP Easy Access Menu by clicking on User Menu, then Development, selecting ABAP Reporting, and adding it to the SAP Fiori launchpad.](../images/7ffbe8e488595876.png)
The easiest way to add transactions is by accessing the _User Menu_ or _SAP Menu_ of a mapped ABAP system. The mapping must be done by an administrator. However, once this is complete, creating a tile for an ABAP transaction is as easy as adding any other app to the FLP.
## Personalize SAP Fiori Pages
### Business Example
You want to add tiles and sections to pages of the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
### Task 1: Add Tiles and Sections in SAP Fiori Pages
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_F873721EF858A896:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your SAP S/4HANA (S4H) system, add the _Data Migration Status_ app as the first tile on the _Cross Topic_ → _General_ page.
    1. In the _SAP Fiori launchpad_ of your S4H, choose the _Cross Topic_ → _Data Migration_ anchor.
    2. Choose your user in the upper right-hand corner.
    3. Choose _Edit Current Page_.
    4. Choose _Add Tile_.
    5. In the _Search in catalog_ field, enter **Migration** and choose _Search_.
    6. Select the "+" icon of the _Data Migration Status_ tile.
    7. Choose _Back_ twice.
    8. Drag and drop the _Data Migration Status_ tile at the first position in the section.
    9. Choose _Close_ in the lower right.
  2. Edit the _Cross Topic_ → _General_ page and create the section **Basics** at the top. Add the _News_ tile of the _Education - Cross-Application_ catalog to it.
    1. Choose the _Cross Topic_ → _General_ anchor.
    2. Choose your user in the upper right-hand corner.
    3. Choose _Edit Current Page_.
    4. Choose any _Add Section_.
    5. In the _Section Title_ field, enter **Basics**.
    6. Drag and drop the _Basics_ section at the top of the page.
    7. Choose _Add Tile_ for the _Basics_ section.
    8. In the list of catalogs on the left-hand side, choose _Education - Cross-Application_.
    9. Select the "+" icon of the news tile.
    10. Choose _Back_ twice.
    11. Choose _Close_ in the lower right.
  3. Start the _Data Browser_ (SE16) in your S4H via a new link in your _Basics_ section.
    1. Choose your user in the upper right-hand corner.
    2. Choose _App Finder_.
    3. Choose _User Menu_ at the top.
    4. In the list of folders on the left, choose _Development_.
    5. Select the "+" icon of the _Data Browser_ tile.
    6. In the _Select the Pages for This Tile_ popup, select _Cross Topic_ → _General_ and choose _OK_.
    7. Choose _Back_.
    8. Drag and drop the _Data Browser_ tile in the _Basics_ section.
    9. Choose your user in the upper right corner.
    10. Choose _Edit Current Page_.
    11. Choose the three points in the lower right of the _Data Browser_ tile.
    12. Choose _Convert to Link_.
    13. Choose _Close_ in the lower-right corner.
    14. Choose the _Data Browser_ link.
    15. Operate the app as you wish.
