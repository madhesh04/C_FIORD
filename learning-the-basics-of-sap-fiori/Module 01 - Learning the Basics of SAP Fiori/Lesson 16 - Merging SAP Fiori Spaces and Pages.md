# Merging SAP Fiori Spaces and Pages

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/merging-sap-fiori-spaces-and-pages*

Objective
After completing this lesson, you will be able to merge SAP Fiori spaces and pages.
## Merge Launchpad Spaces
![Screenshots of merging two spaces with one page each into one space with two pages in FLP.](../images/18ea09cda1d81d4c.png)
Sometimes users have several spaces with similar title and similar content, because they have similar roles assigned. For example, the sales manager and the sales accountant have overlapping tasks and therefore apps in their spaces. Such spaces can be merged to combine their pages in one transient space at runtime. This means that the merged space is not visible in the _Manage Launchpad Spaces_ app, but just for the user in the FLP having all spaces assigned.
![Screenshot of merge options for SAP Fiori Spaces in Manage Spaces.](../images/a4186f9444ca7b2d.png)
Customer spaces can be merged with other customer spaces or with an SAP space. For the second one, you enter the name of the SAP space in the _Merge ID_ field in the _General Data_ tab of the customer space. When merging customer spaces, you can define an own name for the merged space and enter it as _Merge ID_ in all spaces you want to merge.
Hint
The space title is defined by the space with the lowest sort priority.
## Merge Launchpad Pages
Let's watch a video to learn about Merging Launchpad Pages.
![Screenshot of merge options for SAP Fiori Pages in Manage Pages.](../images/be0aafafbe789a7a.png)
Customer pages can be merged with other customer pages or with an SAP page. For the second one, you enter the name of the SAP page in the _Merge ID_ field in the _General Data_ tab of the customer page. When merging customer pages, you can define an own name for the merged page and enter it as _Merge ID_ in all pages you want to merge.
You can only merge pages, which are in the same space. Transient spaces merged at runtime count, too. This allows you to add additional apps to an SAP space without modifying it:
  1. Define a customer page and add apps to it.
  2. Define a customer space. and add the customer page to the it.
  3. Merge the customer space with an SAP space.
  4. Merge the customer page with an SAP page of the SAP space.

Users having the customer and SAP space assigned only see one space with one page with all apps of both pages.
Note
The page title is defined by the first page in the space. If more than one space is involved, the first page in the space with the lowest sort priority defines the page title.
## Merge SAP Fiori Spaces and Pages
### Business Example
You want to merge an SAP Fiori space and page with an SAP-delivered space and page.

Solution:
    SAP_UX100_SP_S_MERGE (Space)     SAP_UX100_PG_S_MERGE (Page)
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names in this exercise include ##, replace ## with the number of your user.
### Prerequisites
Role, space, and page were created in the exercise **Create SAP Fiori Spaces and Pages**.
### Task 1: Assign an SAP-Delivered Space to the Business Role
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_93319C907D9BA68A:uebung)
#### Steps
  1. In the _Role Maintenance_ (PFCG) of your S4H, add the _SAP_PLM_SP_RECIPE_DEVELOPER_ space to the menu of the _Z_##_BR_TRAINING_ role.
    1. In the _Role Maintenance_ (PFCG) of your S4H, edit your **Z_##_BR_TRAINING** role.
    2. Choose the _Menu_ tab.
    3. Expand the _Insert Node_ button.
Hint
The initial value written on the _Insert Node_ button is _Launchpad Catalog_.
    4. Choose _SAP Fiori Launchpad_ → _Launchpad Space_.
    5. In the _Space ID_ field, enter ***recipe*** and use the value help.
    6. In the pop-up, double-click _SAP_PLM_SP_RECIPE_DEVELOPER_.
    7. Choose _Continue_.
    8. Choose _Save_.
  2. Check the tiles of the _Recipe Development_ space in the _SAP Fiori launchpad_ spaces of your S4H.
    1. Reload the _SAP Fiori launchpad_ spaces of your S4H.
    2. Choose the _Recipe Development_ space at the top.
#### Result
The section _Recipes_ with _My Recipe Overview_ and _Manage Recipes_ and the section _Substances_ with _Manage Real Substances_ and _Manage Raw Substances_ are displayed.

### Task 2: Merge a Customer Space with an SAP-Delivered Space
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_FA877FA31BFFC9AA:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your S4H, start the _Manage Launchpad Spaces_ app. Edit the _Z_##_SP_RESEARCH_ space.
    1. In the _SAP Fiori launchpad_ of your S4H, choose the _Manage Launchpad Spaces_ tile.
    2. In the _Search_ field, enter **z_##** and choose **Enter**.
    3. Choose _Edit_ for the _Z_##_SP_RESEARCH_ page.
Hint
The _Edit_ button is the pencil at the end of the line.
  2. Merge the _Z_##_SP_RESEARCH_ space with the **SAP_PLM_SP_RECIPE_DEVELOPER** space.
    1. Choose the _General Data_ tab.
    2. In the _Merge ID_ field, enter **SAP_PLM_SP_RECIPE_DEVELOPER**.
    3. Choose _Save_.
    4. Choose _Navigate to Home_.
  3. Search the _Recipe Development_ space and its _Recipe Development Cockpit_ page in the _SAP Fiori launchpad_ spaces of your S4H.
    1. Reload the _SAP Fiori launchpad_ spaces of your S4H.
    2. Search the _Recipe Development_ space.
#### Result
The _Recipe Development_ space is gone.
    3. Expand the _Research ##_ space.
    4. Choose _Recipe Development Cockpit_.
#### Result
The _Recipe Development Cockpit_ page of the _Recipe Development_ space is now merged in the _Research ##_ space.

### Task 3: Merge a Customer Page with an SAP-Delivered Page
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_D2A00DBB899C45B3:uebung)
#### Steps
  1. In the _SAP Fiori launchpad_ of your S4H, start the _Manage Launchpad Pages_ app. Edit the _Z_##_PG_ENGINEERING_ page.
    1. In the _SAP Fiori launchpad_ of your S4H, choose the _Manage Launchpad Pages_ tile.
    2. In the _Search_ field, enter **z_##** and choose **Enter**.
    3. Choose _Edit_ for the _Z_##_PG_ENGINEERING_ page.
Hint
The _Edit_ button is the pencil at the end of the line.
  2. Merge the _Z_##_PG_ENGINEERING_ page with the **SAP_PLM_PG_RECIPE_DEVELOPER** page.
    1. Choose the _General Data_ tab.
    2. In the _Merge ID_ field, enter **SAP_PLM_PG_RECIPE_DEVELOPER**.
    3. Choose _Save_.
    4. Choose _Navigate to Home_.
  3. Search the _Recipe Development_ space and its _Recipe Development Cockpit_ page in the _SAP Fiori launchpad_ spaces of your S4H.
    1. Reload the _SAP Fiori launchpad_ spaces of your S4H.
    2. Choose _Research ##_.
#### Result
_Manage Recipes_ is displayed as link as defined in _Research ##_ and _Manage Real Substances_ was added in _Substances_ as defined in _SAP_PLM_PG_RECIPE_DEVELOPER_.
