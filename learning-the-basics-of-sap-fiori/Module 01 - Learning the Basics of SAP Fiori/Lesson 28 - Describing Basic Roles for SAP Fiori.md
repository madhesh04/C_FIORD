# Describing Basic Roles for SAP Fiori

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/describing-basic-roles-for-sap-fiori_e86f4df9-b918-4566-a5da-c29406b06c5a*

Objective
After completing this lesson, you will be able to describe Basic Roles for SAP Fiori.
## Predefined Roles
SAP ships foundation role templates for users and administrators of the SAP Fiori launchpad (FLP).
Watch the video to understand predefined roles.
### Additional Role Templates
![Diagram lists SAP roles. Enterprise Search: one composite role, six single roles. Catalog Management: three single roles. Trusted Remote Function Call: one single role.](../images/79f3c028fe9bc925.png)
Being authorized to use the FLP does not mean that any app can be started or data can be searched. To do that, additional roles and authorizations are in place. The topic authorizations must be taken seriously. SAP recommends approaching authorization specialists or to educate oneself specifically in the SAP S/4HANA authorization concept.
Note
For more information about this topic, see:
  * Authorization Concept for SAP Fiori on SAP S/4HANA (Classroom Training)
<https://training.sap.com/course/adm945>
  * Exploring the Authorization Concept for SAP Fiori on SAP S/4HANA (Online Course)
<https://learning.sap.com/courses/exploring-the-authorization-concept-for-sap-fiori-on-sap-s-4hana>

## Enroll a User to SAP Fiori Launchpad
### Business Example
You want to enable a user to work with the _SAP Fiori launchpad_.
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names in this exercise include ##, replace ## with the number of your user.
### Prerequisites
The services were activated in the demonstration **How to Activate SAP Fiori Content**.
### Task 1: Create a User and Assign a Business Catalog
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_E79D0403A9076182:uebung)
#### Steps
  1. In the _User Maintenance_ (SU01) of your SAP S/4HANA (S4H) system, create the user **FLP_USER_##**. Assign the _SAP_BR_UX100_RAPID_ACTIVATION_ role to the user.
    1. In the _SAP Easy Access_ menu of your S4H, search for _User Maintenance_ or start transaction SU01.
    2. In the _User_ field, enter **FLP_USER_##**.
    3. Choose _User_.
    4. In the _Last name_ field, enter your name.
    5. Choose the _Logon Data_ tab.
    6. In the _New Password_ and _Repeat Password_ fields, enter a password.
    7. Choose the _Roles_ tab.
    8. Open the value help of a _Role_ cell in the table.
    9. In the _Single Role_ field, enter ***rapid***.
    10. Choose _Start Search_.
    11. Select the _Single Role_**SAP_BR_UX100_RAPID_ACTIVATION** and choose _Copy_.
    12. Choose _Save_.
  2. Open the _SAP Fiori launchpad_ spaces of your S4H in _Microsoft Edge_ or _Google Chrome_ and examine the error in the _App Finder_.
    1. Start the _SAP Fiori launchpad_ spaces of your S4H in _Microsoft Edge_ or _Google Chrome_.
Caution
No other session must be active of the chosen Web browser.
    2. In the _Select a Certificate_ popup, choose _Cancel_.
    3. Log on with **FLP_USER_##** and the password you created in the step before.
    4. Change the password to a new password.
    5. Choose your user in the upper right corner.
    6. In the _User Actions Menu_ , choose _App Finder_.
#### Result
The error _Failed to load catalogs_ appears.

### Task 2: Assign the Z_FIORI_FOUNDATION_USER Role to the New User
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_C8A89EB418746793:uebung)
#### Steps
  1. In the _User Maintenance_ (SU01) of your S4H, assign the _Z_FIORI_FOUNDATION_USER_ composite role to the _FLP_USER_##_ user.
    1. In the _User Maintenance_ (SU01) of your S4H, choose _Change_ for the **FLP_USER_##** user.
    2. Choose the _Roles_ tab.
    3. Open the value help of a _Role_ cell in the table.
    4. Choose _Composite Roles_.
    5. In the _Composite Role_ field, enter ***fiori***.
    6. Choose _Start Search_.
    7. Select the _Composite Role_**Z_FIORI_FOUNDATION_USER** and choose _Copy_ (Check mark).
    8. Choose _Save_.
  2. In the _SAP Fiori launchpad_ of your S4H running in _Microsoft Edge_ or _Google Chrome_ , add the _Display Sales Order Items_ tile to your _My Home_ and start the app.
    1. Reload the _App Finder_ in the _SAP Fiori launchpad_ spaces of your S4H in _Microsoft Edge_ or _Google Chrome_.
Note
If you closed the Web browser, log on again to the _SAP Fiori launchpad_ with user **FLP_USER_##** and open the _App Finder_.
    2. Choose the plus of the _Display Sales Order Items_ tile.
#### Result
The message _"Display Sales Order Items" added to "My Home"_.
    3. Choose _Navigate to Home_.
    4. Choose the _Display Sales Order Items_ tile.
