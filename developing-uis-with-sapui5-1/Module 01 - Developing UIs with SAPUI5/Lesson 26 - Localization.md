# Localization

*Source: https://learning.sap.com/courses/developing-uis-with-sapui5-1/working-with-a-resource-model_da9e4eef-3a80-4db7-b23f-e318ffd6a5e7*

Objective
After completing this lesson, you will be able to internationalize an application by using translatable texts
## Resource Bundles
Watch the video to understand how language-specific UIs are implemented through a resource model.
Settings
### Using Localized Texts
![Sample localized texts, highlighting the i18n properties.](../images/ff62e897eb548fb0.png)
Resource bundle files are stored in an SAPUI5 project in the i18n folder, which is located under the webapp folder.
The figure, _Using Localized Texts_ , shows a resource bundle with base name i18n, which consists of three files i18n.properties, i18n_en.properties, and i18n_de.properties. All three files are located in the i18n folder of the project. The i18n_en.properties file contains the English texts _City_ and _Country_ for the two keys cityLabelText and countryLabelText. The _i18n_de.properties_ file, on the other hand, contains the German texts _Stadt_ and _Land_ for these keys.
With the help of a resource model, the application can now bind the label texts seen on the UI to the texts from the resource bundle. For this purpose, the language-independent keys are used for the binding. Details on this are discussed in the next section.
If the application now runs with en as language code / locale, the texts to be displayed are taken from the i18n_en.properties file. If, on the other hand, de is used as the language code / locale, the German texts are displayed accordingly.
## Resource Model
### Model Instantiation
Via a resource model, localized texts can be used in data binding. The resource model is a wrapper for resource bundles that exposes the localized texts as a model for data binding. You use the resource model to bind texts for control properties to language-dependent resource bundle properties.
![Sample resource model, as described in the text.](../images/6d7922af1c7804d4.png)
The resource model is implemented via the sap.ui.model.resource.ResourceModel class. A corresponding model instance can be created either by calling the constructor of this class in JavaScript or declaratively via the application descriptor. The figure, _Instantiating a Resource Model_ , shows the declarative way via an entry in the models property of the sap.ui5 namespace.
The entry creates a resource model that is set under the model name i18n for the component. The bundle name references the .properties base file of the resource bundle to be used. It is specified as SAPUI5 module name in dot notation and is resolved to a path as with normal SAPUI5 modules, to which ".properties" is then appended. In the example, the file i18n.properties in the i18n folder of the SAPUI5 project is specified, since the resource root of the project was set to sap.training.exc.
The two properties supportedLocales and fallbackLocale can be used to control the loading of resource bundle files and avoid '404 Not Found' network responses as follows: Assuming SAPUI5 determines de_DE as the current language code / locale of the application. Without using the two properties, the following fallback chain would be used in the example: To load the language-dependent text for a used key, the file i18n_de_DE.properties would first be requested from the server. If this is not found or the used key is not present there, the file i18n_de.properties would be requested next (without region suffix). If this is not found or the key used is not present there, the i18n_en.properties file would be requested next. If no value for the key can be identified via this request either, the raw file, i18n.properties, is finally requested from the server.
Via supportedLocales a list of locales can be specified to restrict the fallback chain. The empty string ("") represents the raw file. The fallbackLocale property can be used to specify the locale to be used after all derived locales have been tried unsuccessfully and before the raw file is used. This property has en as default value. To prevent a generic fallback, the empty string is used ("").
So the values used here for supportedLocales ("") and fallbackLocale ("") ensure that only the raw file without fallback is requested by the browser.
### Data Binding
After the resource model has been instantiated, you have a model containing the resource bundle texts as data.
![Sample data binding code, as described in the following text.](../images/e43b563883ab166a.png)
In contrast to other models, binding paths for a resource model must not start with a slash; they are absolute by default, and there is no further structure. Each key in the underlying resource bundle is a valid binding path.
In the example shown in the figure _Data Binding_ , keys cityLabelText and countryLabelText from the resource bundle are used to define language-dependent labels for the two input fields. Since the model was given the name i18n when it was declared in the application descriptor, the binding paths must be prefixed with i18n> accordingly.
![Sample code using the sap/base/strings/formatMessage code, as described in the following text.](../images/7a295b50051daf68.png)
The texts used in a resource bundle may contain placeholders of the form {integer}. Such placeholders can be replaced in the data binding using the sap/base/strings/formatMessage function.
The sap/base/strings/formatMessage function expects the pattern string with the placeholders as the first parameter. The second parameter is an array containing the values to be used instead of the placeholders. Each occurrence of {0} is replaced by the value at index position 0 of the array, each occurrence of {1} is replaced by the value at index position 1 of the array, and so on. The function returns the appropriately formatted string as result.
The figure, _Replacing Placeholders_ , shows an example of how the sap/base/strings/formatMessage function can be used in data binding to replace placeholders. The shown i18n.properties resource bundle file contains a language-dependent text for the key dialogText, in which the placeholder {0} is used.
The text is to be displayed using a Text UI element, where the placeholder is to be replaced with the customer name.
To do this, the core:require attribute is used in the <Text> tag to ensure that the sap/base/strings/formatMessage module is loaded (core is the alias for the previously defined sap.ui.core namespace). The loaded module is assigned the alias formatMessage.
A binding object is passed to the text attribute of the Text UI element. There the loaded function is set as formatter function for the binding via its assigned alias. The parts array is used to pass the pattern string via the i18n>dialogText path and a value for the placeholder via the customer>/CustomerName path. The passed placeholder value is the content of the property CustomerName of the model named customer.
The formatMessage function ensures that the text from the resource bundle is displayed on the UI with the inserted customer name.
## Module sap/base/i18n/ResourceBundle
SAPUI5 provides two options to access localized texts in applications: In addition to data binding via a resource model, the sap/base/i18n/ResourceBundle module is available. This module provides an API to access localized texts that are contained in a resource bundle.
![Sample code using sap/base/i18n/ResourceBundle.](../images/e9199d534afc80ba.png)
Use the module's create method to create an instance of sap/base/i18n/ResourceBundle. The url parameter of this method can be used to pass the URL pointing to the base .properties file of the resource bundle.
The create method returns either an instance of sap/base/i18n/ResourceBundle or a promise on that resource bundle when requesting the resource bundle asynchronously. To load the resource bundle asynchronously, the async parameter of the create method must be passed with the value true.
Analogous to the constructor of the resource model, the create method also has the parameters supportedLocales and fallbackLocale. For details, see the API reference in the Demo Kit.
The resource bundle underlying a resource model can also be accessed directly from the resource model instead of using the create method of the sap/base/i18n/ResourceBundle module. For this purpose, the resource model provides the getResourceBundle method. This method returns the resource bundle underlying the model (instance of sap/base/i18n/ResourceBundle) or a promise resolving with it in asynchronous case. To load the resource bundle asynchronously via the resource model, the async parameter of the constructor must be passed with the value true when instantiating the resource model.
The getText method of the resource bundle returns a locale-specific string value for the given key. The method has an optional second parameter that can be used to pass an array. If such an array is passed, any placeholder in the found locale-specific string value of the form {n} (with n being an integer) is replaced by the corresponding value from the array with index n.
The figure, Using sap/base/i18n/ResourceBundle, shows an example of how to use the module. In the classText method depicted, an instance of the module is created via its create method, specifying i18n/i18n.properties as the base file of the resource bundle. Then the getText method is called to retrieve the locale-specific text for key flightClassC from the resource bundle.
## Use Translatable Texts
### Business Scenario
In the previous exercises, you hard-coded all the texts that are displayed on the UI in the corresponding files. In this exercise, you will now move these texts on the Overview view, in the formatter function, and in the XML fragment to a resource bundle file so that they can be accessed through a resource model. Through this process of internationalization, the texts can be translated into other languages.
| _Template:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/18_device_adaptation**  |
| --- | --- |
| _Model solution:_  | Git Repository: <https://github.com/SAP-samples/sapui5-development-learning-journey.git>, Branch: **sol/19_resource_model**  |
### Task 1: Add a Resource Model to the Component
#### Steps
  1. Open the manifest.json application descriptor from the webapp folder in the editor.
  2. In the application descriptor, look for the following entry contained in the models property in the sap.ui5 namespace:
JSON
Copy codeSwitch to dark mode

```

123456

"i18n": {
  "type": "sap.ui.model.resource.ResourceModel",
  "settings": {
    "bundleName": "<...>"
  }
}

```

Note
This declaration automatically instantiates a resource model named i18n for the component.
  3. Specify the resource bundle to use for the resource model by replacing "<...>" with **"sap.training.exc.i18n.i18n"** for the bundleName property.
Note
The bundle name now refers to the i18n.properties file from the i18n folder, which already exists in the project.
#### Result
The declaration of the resource model should now look like this:![The JSON file, highlighting the bundleName attribute.](../images/98918183330662b0.png)
  4. In addition to the bundleName property, add the following two properties to the settings property:
JSON
Copy codeSwitch to dark mode

```

12

"supportedLocales": [""],
"fallbackLocale": ""

```

Note
For simplicity, the exercise scenario works only with the i18n.properties file. No other language-specific i18n_*.properties files are created in addition to this raw file. The values set here for supportedLocales and fallbackLocale therefore ensure that only the raw file is requested by the browser without any fallback.

#### Result
The declaration of the resource model should now look like this:
![The JSON code, highlighting the supported Locales and fallbackLocale attributes.](../images/9faad597d6ec6bf5.png)
### Task 2: Replace the Hard-Coded Texts on the Overview View with Translatable Texts
#### Steps
  1. Open the i18n.properties resource bundle file from the i18n folder in the editor.
  2. For the hard-coded texts used on the Overview view, add the following key-value pairs to the resource bundle file:
JSON
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223242526

# Overview View
overviewPageTitle=Flight Customers
customerPanelHeader=New Customer
newCustomerButtonText=Create Customer
generalDataFormContainerTitle=General Data
addressDataFormContainerTitle=Address Data
contactDataFormContainerTitle=Contact Data
formLabelText=Form
nameLabelText=Customer Name
discountLabelText=Discount
streetLabelText=Street
postcodeLabelText=Post Code
cityLabelText=City
countryLabelText=Country
emailLabelText=Email
phoneLabelText=Telephone
customerTableHeader=Customers
bookingTableHeader=Bookings
airlineColumnHeader=Airline ID
connectionColumnHeader=Connection Number
fldateColumnHeader=Flight Date
classColumnHeader=Class
paymentColumnHeader=Foreign Currency Payment
cancellationColumnHeader=Cancellation Status
cancelledTooltip=cancelled
notCancelledTooltip=not cancelled

```

Note
In the next steps, you will replace the hard-coded texts on the Overview view using the keys defined here from the resource model.
#### Result
The i18n.properties resource bundle file should now look like this:![The Overview View code is highlighted.](../images/47dadd4ffcf6dd56.png)
  3. Open the Overview.view.xml file from the webapp/view folder in the editor.
  4. Now replace the value of the title attribute in the <Page> tag with **{i18n >overviewPageTitle}**.
Note
In the new value, i18n is the name assigned to the resource model in the application descriptor, while overviewPageTitle is the key from the resource bundle file.
#### Result
The <Page> tag should now look like this:![The XML file, highlighting the title attribute.](../images/bf945905762bf193.png)
  5. Replace the value of the headerText attribute in the <Panel> tag with **{i18n >customerPanelHeader}**.
#### Result
The <Panel> tag should now look like this:![The XML file, highlighting the headerText attribute.](../images/c77d3921bd610987.png)
  6. Replace the value of the text attribute in the <Button> tag with **{i18n >newCustomerButtonText}**.
#### Result
The <Button> tag should now look like this:![The XML file, highlighting the button tag.](../images/c1ea2d5d9d53aed4.png)
  7. Replace the texts hard-coded in the form for creating a new customer as shown in the following table:
| **Old**  | **New Attribute Value**  |
| --- | --- |
| <core:Title text="General Data"/>  | **i18n >generalDataFormContainerTitle**  |
| <Label text="Form"/>  | **i18n >formLabelText**  |
| <Label text="Customer Name"/>  | **i18n >nameLabelText**  |
| <Label text="Discount"/>  | **i18n >discountLabelText**  |
| <core:Title text="Address Data"/>  | **i18n >addressDataFormContainerTitle**  |
| <Label text="Street"/>  | **i18n >streetLabelText**  |
| <Label text="Post Code"/>  | **i18n >postcodeLabelText**  |
| <Label text="City"/>  | **i18n >cityLabelText**  |
| <Label text="Country"/>  | **i18n >countryLabelText**  |
| <core:Title text="Contact Data"/>  | **i18n >contactDataFormContainerTitle**  |
| <Label text="Email"/>  | **i18n >emailLabelText**  |
| <Label text="Telephone"/>  | **i18n >phoneLabelText**  |
#### Result
The form should now look like this:![The XML file, highlighting the text attributes.](../images/0b16806491656f39.png)
  8. Replace the texts hard-coded in the customer table as shown in the following table:
| **Old**  | **New Attribute Value**  |
| --- | --- |
| <Title text="Customers"/>  | **i18n >customerTableHeader**  |
| <Text text="Customer Name"/>  | **i18n >nameLabelText**  |
| <Text text="Street"/>  | **i18n >streetLabelText**  |
| <Text text="Post Code"/>  | **i18n >postcodeLabelText**  |
| <Text text="City"/>  | **i18n >cityLabelText**  |
| <Text text="Country"/>  | **i18n >countryLabelText**  |
| <Text text="Email"/>  | **i18n >emailLabelText**  |
#### Result
The customer table should now look like this:![The XML file, highlighting the text attributes.](../images/9914239b42e6eba4.png)
  9. Finally, replace the texts hard-coded in the booking table as shown in the following table:
| **Old**  | **New Attribute Value**  |
| --- | --- |
| <Table headerText="Bookings" ...>  | **i18n >bookingTableHeader**  |
| <Text text="Airline ID"/>  | **i18n >airlineColumnHeader**  |
| <Text text="Connection Number"/>  | **i18n >connectionColumnHeader**  |
| <Text text="Flight Date"/>  | **i18n >fldateColumnHeader**  |
| <Text text="Class"/>  | **i18n >classColumnHeader**  |
| <Text text="Foreign Currency Payment"/>  | **i18n >paymentColumnHeader**  |
| <Text text="Cancellation Status"/>  | **i18n >cancellationColumnHeader**  |
| <core:Icon tooltip="{= ${IsCancelled} === 'X' ? 'cancelled' : 'not cancelled' }" .../>  | **${IsCancelled} === 'X' ? ${i18n >cancelledTooltip} : ${i18n>notCancelledTooltip}**  |

#### Result
The booking table should now look like this:
![The XML file, highlighting the headerText, text, and tooltip attributes.](../images/e1d886d69596eebf.png)
### Task 3: Replace the Hard-Coded Texts in the Formatter Function with Translatable Texts
#### Steps
  1. The classText formatter function created in a previous exercise returns the texts _Business Class_ , _Economy Class_ , or _First Class_ , depending on the content of the Class model property.
Add the following key-value pairs to the i18n.properties file to make these texts translatable:
JSON
Copy codeSwitch to dark mode

```

1234

# Formatter
flightClassC=Business Class
flightClassY=Economy Class
flightClassF=First Class

```

#### Result
The i18n.properties resource bundle file should now look like this:![The il18n file, highlighting the formatter function.](../images/470ab56a6f4b9692.png)
  2. Open the formatter.js file from the webapp/model folder in the editor.
  3. Add the sap/base/i18n/ResourceBundle module to the dependency array of the formatter module and a corresponding parameter named ResourceBundle to the factory function.
Note
The ResourceBundle module is used in the next step to load the resource bundle and access the texts created above.
#### Result
The formatter module should now look like this:![The formatter.js file, highlighting the sap/base/i18n/ResourceBundle attribute.](../images/f3c892819cd6f048.png)
  4. Modify the implementation of the classText formatter function as follows to load the resource bundle and access the texts created above from it via their respective keys:
JavaScript
Copy codeSwitch to dark mode

```

1234567891011121314

classText: function (sClass) {
  var oResourceBundle = ResourceBundle.create({ url: "i18n/i18n.properties" });

  switch (sClass) {
    case "C":
      return oResourceBundle.getText("flightClassC");
    case "Y":
      return oResourceBundle.getText("flightClassY");
    case "F":
      return oResourceBundle.getText("flightClassF");
    default:
      return sClass;
  }
}

```

#### Result
The classText formatter function should now look like this:
![Formatter.js file highlighting the classText function.](../images/8469c3ccdf90db42.png)
### Task 4: Replace the Hard-Coded Info Text on the Popup with a Translatable Text
#### Steps
  1. Finally, the following text on the popup, implemented in a previous exercise via the Dialog.fragment.xml file, should be made translatable:
XML
Copy codeSwitch to dark mode

```

12

<Text
  text="Customer {customer>/CustomerName} is later saved via an OData service."/>

```

To do this, add the following key-value pair to the i18n.properties file:
JSON
Copy codeSwitch to dark mode

```

12

# Fragment
dialogText=Customer {0} is later saved via an OData service.

```

Note
In the next steps, you will display this text on the popup via the resource model, replacing the {0} placeholder with the current customer name.
#### Result
The i18n.properties resource bundle file should now look like this:![The i18n.properties file highlighting the #Fragment line.](../images/54b8e66262096c2e.png)
  2. Open the Dialog.fragment.xml file from the webapp/view folder in the editor.
  3. Modify the Text UI element on the popup as follows to use the text you just created from the resource model for the display, replacing the {0} placeholder with the current customer name:
XML
Copy codeSwitch to dark mode

```

1234567

<Text
  core:require="{formatMessage: 'sap/base/strings/formatMessage'}"
  text="{
          parts: [
                    {path: 'i18n>dialogText'},
                    {path: 'customer>/CustomerName'} ],
          formatter: 'formatMessage' }"/>

```

#### Result
The implementation of the popup should now look like this:![The XML file, highlighting the Text tag.](../images/6bcda362d537c309.png)
  4. Test run your application by starting it from the SAP Business Application Studio.
Make sure that the UI has not changed from the previous exercise from the user's point of view: All texts on the Overview view including the flight class in the booking table as well as the text on the popup should be displayed unchanged. However, the texts now come from the resource bundle and are translatable.
    1. Right-click on any subfolder in your _sapui5-development-learning-journey_ project and select _Preview Application_ from the context menu that appears.
    2. Select the npm script named _start-noflp_ in the dialog that appears.
    3. In the opened application, check if the component works as expected.

[Continue to quiz](https://learning.sap.com/courses/developing-uis-with-sapui5-1/localization)
