# Shaping the Header Area of the Object Page

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/placing-key-figures-in-the-header-area_c9dca7b8-25e4-4b3d-b7f0-3b7e01b35c27*

Objective
After completing this lesson, you will be able to populate the object page header with the most important data.
## The Object Page Header
The object page displays the detailed information about an object. It can contain multiple sections such as tables, charts, and forms.
The top section of the object page is called the object page header. It can consist of a title, a description, an image, some actions, and contains a number of header sections known as facets. Header facets are containers. You can add different types of micro charts, progress indicator, rating indicator and key figures into the header facets. For more information about header facets, see [Header Facets](https://sapui5.hana.ondemand.com/sdk/#/topic/17dbd5b7a61e4cdcb079062e976cd63f).
The key figures are represented by the @UI.DataPoint annotation. Usually, the data point is a number but can also be a text, for example, a status value. For more information about data points, see [Data Points](https://sapui5.hana.ondemand.com/sdk/#/topic/c2a389a11a704b00886440031a3d43f9).
## Add Travel Status, Total Price, and the Deduct Discount Action to the Header Area
In this exercise, you will learn to configure the key figures and actions in the header area of the object page. You can use either the guided development aid named Add a Header Facet Using Data Points or the Page Editor for configuring the header facets by using data points.
### Usage Scenario
The user must be able to execute the action Deduct Discount on the object page similar to the list report. They must see the two key figures Total Price and Travel Status prominently on the object page header.
### Task Flow
You will first add the action Deduct Discount to the object page header. You may have already created and implemented this action in your CAP service, and used it in the list report table toolbar in one of the previous exercises. You can use the Page Editor to configure it.
Next, you can learn to add two key figures Total Price and Travel Status as the data point header sections. The Page Editor can also help you to achieve this.
### Prerequisites
You have completed the exercise Create Multiple Table Views Using Single Table Mode in the unit Using Multiple Views in the List Report (lesson: Configuring Multiple Views Using Single Table Mode). Alternatively, you can check out its solution branch: [solution/create-multiple-table-views-single-table-mode](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/create-multiple-table-views-single-table-mode).
### Watch the Simulation and Perform the Steps
This exercise contains a simulation that takes you through all the steps described below. You can follow the simulation and perform the steps using your own trial account.
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_EC175727B917FC9C:uebung)
### Steps
  1. Add the action Deduct Discount.
    1. Open your CAP project in SAP Business Application Studio.
    2. In the Explorer view, select Projects\fiori-elements-v4-cap-advanced\app\travel_processor\webapp.
    3. Right-click on _webapp_.
    4. Select _Show Page Map_. The _Page Map-travel_ appears.
    5. Select the _Edit_ icon of the object page. The page map of _TravelObjectPage_ appears.
    6. Under _Header_ , select _Actions_.
    7. Under _Actions_ , select the _Add_ icon. The _Add Actions_ dialog appears.
    8. From the _Actions_ drop-down, choose **TravelService.deductDiscount**.
    9. Select _Add_. The action _deductDiscount_ is added.
    10. In the right pane, under _Label_ , enter the label name **Deduct Discount**.
    11. Select the globe icon corresponding to the label name.
    12. Select _Apply_. The label text is added to the i18n.properties file.
  2. Add the data point header Travel Status.
    1. Switch back to the SAP Business Application Studio. The Page Editor is still open.
    2. Under _Header_ , select _Header Sections_.
    3. Select the _Add_ icon.
    4. Choose **Add Data Point Section**. The _Add Data Point Section_ dialog appears.
    5. From the _Value Source Property_ drop-down, choose **TravelStatus_code**.
    6. Select _Add_.
    7. In the right pane, under _Label_ , enter the label name **Travel Status**.
    8. Select the globe icon corresponding to the label name.
    9. Select _Apply_. The label text is added to the i18n.properties file.
    10. Under _Criticality_ , from the drop-down, chose **criticality**.
  3. Add the data point header Total Price.
    1. Switch back to the SAP Business Application Studio. The Page Editor is still open.
    2. Under _Header_ , select _Header Sections_.
    3. Select the _Add_ icon.
    4. Choose **Add Data Point Section**. The _Add Data Point Section_ dialog appears.
    5. From the _Value Source Property_ drop-down, choose **TotalPrice**.
    6. Select _Add_.
    7. In the right pane, under _Label_ , enter the label name **Total Price**.
    8. Select the globe icon corresponding to the label name.
    9. Select _Apply_.

### Result
You have learned to visualize the key figures as data point sections in the object page header. You have also added the application-specific action to the header.
Note
  * You can find the solution for this exercise on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced).
  * The solution branch is [solution/put-travel-status-total-price-deduct-discount-to-header-area-op](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/solution/put-travel-status-total-price-deduct-discount-to-header-area-op).
  * You can see the code changes compared to the previous branch on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/compare/solution/create-multiple-table-views-single-table-mode..solution/put-travel-status-total-price-deduct-discount-to-header-area-op).

### Next Steps
For more information, see
  * [Object Page Elements](https://sapui5.hana.ondemand.com/sdk/#/topic/645e27ae85d54c8cbc3f6722184a24a1)
  * [Displaying Actions on the Object Page](https://sapui5.hana.ondemand.com/sdk/#/topic/f65e8b196335457cbfc891418ec25cfd)
  * [Setting Up the Object Page Header](https://sapui5.hana.ondemand.com/sdk/#/topic/cce93e6f067a4133a8430c4f5d7b8fc7)
  * [Object Page Floorplan](https://experience.sap.com/fiori-design-web/object-page/)
