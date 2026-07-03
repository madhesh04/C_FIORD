# Enforcing Responsiveness in a Full-screen application

*Source: https://learning.sap.com/courses/advanced-sapui5-development/developing-a-full-screen-application_c046dc57-0c33-4c42-8d97-c2d25065a920*

Objective
After completing this lesson, you will be able to enforce responsiveness in a full-screen application.
## Responsive UI Controls
One of the main advantages of SAPUI5 is that it offers UI controls already designed for responsiveness.
Controls available in the sap.**m** library are indeed designed for **mobility**.
For example, the sap.m.Table control provides a set of sophisticated and easy-to-use functions for responsive table design. The sap.m.Column used as aggregation in the Table control allows to define column specific properties that will manage responsiveness. Here are some of those properties :
  * **minScreenWidth**
Defines the minimum screen width to show or hide this column. By default column is always shown. The responsive behavior of the sap.m.Table is determined by this property. As an example by setting minScreenWidth property to "40em" (or "640px" or "Tablet") shows this column on tablet (and desktop) but hides on mobile.
  * **demandPopin**
According to your minScreenWidth settings, the column can be hidden in different screen sizes. Setting this property to true, shows this column as pop-in instead of hiding it. Meaning the columns to hide will be displayed below the actual table row, one below the other.

An alternative would be to set the **autoPopinMode** of the table to true and manage each column **importance** property.
Combined with alignment properties and the **width** property to fix a specific size for a column, no matter what the screen size is, it ensures that the data will be displayed correctly whatever device is used.
## Add responsiveness to a Full-screen application
In the following exercise, you will check and enforce responsiveness in a Full-screen Application with SAPUI5.
Note
SAP Business Technology Platform and its tools are cloud services. Due to the nature of cloud software, step procedures and naming of fields and buttons may differ from the exercise solution.
### Prerequisites
You should have completed the previous exercise to implement navigation in the full screen application.
If not, you can find the intermediate state of the fullscreen application in your solutions files. It is called fullscreen_stage1.
### Task 1: Test your Application for Responsiveness
#### Steps
  1. Run the application, _fullscreen_.
    1. Perform this step as shown in a previous exercise.
  2. With the help of Chrome DevTools, choose the large screen size of 1142 x 764 to preview how the application might look in a desktop browser. Select a carrier from the list of carriers and notice that the table for the flights has plenty of room for each field.
    1. Press F12 (on your keyboard) to access Chrome DevTools.
    2. Choose _Toggle device toolbar_.
![Toggle Device toolbar](../images/3c495d270c369def.png)
    3. Set the screen size to 1142 x 764 and press Enter (on your keyboard).
![Screen Resolution Settings](../images/4329bb00aae86d57.png)
    4. Select a carrier from the list of carriers. Take note that the table for the flights has plenty of room for each field.
![Resulting application screenshot with large columns for the list of flights.](../images/d090257745347ef5.png)
  3. With the help of Chrome DevTools, choose a smaller screen size of 324 x 480 to preview how the application might look on a mobile browser. Take note that the table for the flights has adjusted poorly to the new size.
    1. Set the screen size to 324 x 480 and press Enter (on your keyboard).
![Screen resolution settings](../images/040428d5095642af.png)
    2. Notice that the table for the flights has adjusted poorly to the new size. Text fields are wrapped and difficult to read.
![Application displayed in small screen resolution. Text fields are wrapped.](../images/cae919abaa46cc7f.png)

### Task 2: Adjust the Carrier View for a Mobile Device
#### Steps
  1. Open the Carrier.view.xml file and add to each of the Column elements the following attributes. Then save your changes.
#### Attribute-value Pairs for the Column Elements
| Attribute  | Value  |
| --- | --- |
| minScreenWidth  | **Tablet**  |
| demandPopin  | **true**  |
    1. Open the Carrier.view.xml file.
    2. Add the following code to each Column definition:
Code Snippet
Copy codeSwitch to dark mode

```

1

minScreenWidth="Tablet" demandPopin="true"

```

    3. For additional information about demandPopin visit the following URL: <https://sapui5.netweaver.ondemand.com/sdk/#/api/sap.m.Column%23controlProperties>
    4. Save your changes. You now should have the following code:
![Screenshot of the resulting columns code.](../images/c6c67bd3b0e5fb7f.png)

### Task 3: Adjust the Flights View for a Mobile Device
#### Steps
  1. Open the Flights.view.xml file.
    1. Perform this step as shown in a previous exercise.
  2. Add the following attribute to the first element of type, Column:
#### Attribute-value Pair for the first Column Element
| Attribute  | Value  |
| --- | --- |
| width  | **12em**  |
    1. Add the following code to the first Column definition:
Code Snippet
Copy codeSwitch to dark mode

```

1

width="12em"

```

  3. Add the following attribute to the last element of typeColumn:
#### Attribute-value pair for the last Column element
| Attribute  | Value  |
| --- | --- |
| hAlign  | **Right**  |
    1. Add the following code to the last Column definition:
Code Snippet
Copy codeSwitch to dark mode

```

1

hAlign="Right"

```

  4. Add the following attributes to the other elements of type Column. Then save your changes.
#### Attribute-value Pairs for the second, third and fourth Column Elements
| Attribute  | Value  |
| --- | --- |
| minScreenWidth  | **Tablet**  |
| demandPopin  | **true**  |
    1. Add the following code to the other two Column definition:
Code Snippet
Copy codeSwitch to dark mode

```

1

minScreenWidth="Tablet" demandPopin="true"

```

    2. Save your changes. You now should have the following code:
![Screenshot of the resulting columns code.](../images/f96979d88797db7a.png)

### Task 4: Test your Application Again
#### Steps
  1. Start your application for the test.
    1. Perform this step as shown in a previous exercise.
  2. With the help of Chrome DevTools, choose the large screen size of 1142 x 764 to preview how the application would look in a desktop browser. Then select a carrier from the list of carriers. Take note that the table for the flights has plenty of room for each field.
![Application screen in desktop resolution.](../images/1fa91c17c3567369.png)
    1. Press F12 (on your keyboard) to access Chrome DevTools.
    2. Set the screen size to 1142 x 764.
![Screen Resolution Settings](../images/635ce91111f95757.png)
    3. Select a carrier from the list of carriers.
    4. Notice that the table for the flights has plenty of room for each field.
  3. With the help of Chrome DevTools, choose a smaller screen size of 324 x 700 to preview how the application will look on a mobile browser. Notice that the table for the flights has adjusted well to the new size.
![Application screen in small resolution. Some fields are displayed vertically. Only seatocc is on a second column.](../images/3c68da18f384eed5.png)
    1. Set the screen size to 324 x 700.
![Screen resolution settings.](../images/e485ede473849dd1.png)
    2. Notice the table for the flights has adjusted well to the new size.
    3. Close and stop the application.
  4. Since we will further develop your fullscreen project in a following exercise, you can save the current state of the project by downloading it. Select the _fullscreen_ project and from the context menu, choose _Download_.

[Continue to quiz](https://learning.sap.com/courses/advanced-sapui5-development/implementing-full-screen-application)
