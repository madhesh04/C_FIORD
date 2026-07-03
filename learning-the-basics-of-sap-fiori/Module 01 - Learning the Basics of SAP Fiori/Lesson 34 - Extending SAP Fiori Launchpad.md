# Extending SAP Fiori Launchpad

*Source: https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/extending-sap-fiori-launchpad_f5f3c83e-fdb1-46fc-89c5-fe123bb2b9c8*

Objective
After completing this lesson, you will be able to extend SAP Fiori launchpad.
## SAP Fiori Launchpad Plug-Ins
Watch this video for an overview on possible extensions.
Developing a plug-in involves the following steps:
  1. Implementing the plug-in
  2. Activating and configuring the plug-in

![Screenshot of SAP Fiori basic generator in SAP Business Application Studio on the left. On the right, directory tree shows items to delete in pink and to keep in green.](../images/f2fb099f8f7d52a0.png)
To start developing an FLP plug-in, generate an SAPUI5 freestyle application in the _SAP Business Application Studio (BAS)_. Then delete all unsupported or unnecessary folders and files.
The next step is to define the SAPUI5 project as an FLP plug-in. This is done in the manifest.json file:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223242526272829303132

{
  "_version": "1.37.0",
  "sap.app": {
    "id": "project1",
    "type": "component",
    "i18n": "i18n/i18n.properties",
    "applicationVersion": {
      "version": "0.0.1"
    },
    "title": "{{appTitle}}",
    "description": "{{appDescription}}",
    "resources": "resources.json",
    "sourceTemplate": {
      "id": "@sap/generator-fiori:basic",
      "version": "1.6.7",
      "toolsId": "4ef10253-5957-4a76-863b-06d7fd654689"
    }
  },
  "sap.ui": {
    "technology": "UI5",
    "deviceTypes": {
      "desktop": true,
      "tablet": true,
      "phone": true
    }
  },
  "sap.flp": {
    "type": "plugin"
  }
}

```

Generally, there are no views in a plug-in. All changes to the FLP are defined by accessing the renderer of the FLP in the Component.js file. This enables the FLP to load and instantiate the plug-ins automatically during startup. A typical initial Component.js looks like this:
Code Snippet
Copy codeSwitch to dark mode

```

1234567891011121314151617181920212223242526272829303132333435363738394041424344454647484950

sap.ui.define([
  "sap/ui/core/Component",
  "sap/m/Button",
  "sap/m/Bar",
  "sap/m/MessageToast"
], function (Component, Button, Bar, MessageToast) {

  return Component.extend("project1.Component", {

    metadata: {
      "manifest": "json"
    },

    _getRenderer: function () {
      var that = this,
          oDeferred = new jQuery.Deferred(),
          oRenderer;

      that._oShellContainer =
          jQuery.sap.getObject("sap.ushell.Container");
      if (!that._oShellContainer) {
        oDeferred.reject(
          "Illegal state: shell container not available;
           it must be executed in a unified shell runtime context.");
      } else {
        oRenderer = that._oShellContainer.getRenderer();
        if (oRenderer) {
          oDeferred.resolve(oRenderer);
        } else {
          // renderer not initialized yet
          // listen to rendererCreated event
          that._onRendererCreated = function (oEvent) {
            oRenderer = oEvent.getParameter("renderer");
            if (oRenderer) {
              oDeferred.resolve(oRenderer);
            } else {
              oDeferred.reject("Illegal state: shell renderer
                                not available after recieving
                                'rendererLoaded' event.");
            }
          };
          that._oShellContainer.attachRendererCreatedEvent(
            that._onRendererCreated);
        }
      }
      return oDeferred.promise();
    }
  });
});

```

In the FLP documentation on <https://help.sap.com>, many code snippets are available as template. A code changing the shell header looks like this:
Code Snippet
Copy codeSwitch to dark mode

```

123456789101112131415

...

init: function () {
  var rendererPromise = this._getRenderer();

  /**
   * Set header title
   */
  rendererPromise.then(function (oRenderer) {
      oRenderer.setHeaderTitle("SAP Education");
  });
},

...

```

The SAP Note [3085381](https://me.sap.com/notes/3085381) – _Developing SAP Fiori launchpad plug-ins with SAP Fiori Tools_ provides a full description of the process.
Note
Plug-ins are loaded and instantiated asynchronously. When multiple plug-ins are loaded, do not assume any specific instantiation order of the components.
Every plug-in must be defined in transaction /UI2/FLP_CONF_DEF before it can be activated via customizing.
Watch the video to see how plug-ins can be activated via customizing.
## Activate a Plug-In for the SAP Fiori Launchpad
### Business Example
You want to extend the _SAP Fiori launchpad_ by adding a plugin to the configuration.

Solution
    SAP_UX100_BC_S_FLP_PLUGIN (Business Catalog)     SAP_UX100_TC_S_FLP_PLUGINS (Standard Catalog)
Note
This exercise requires an SAP Learning system. Login information is provided by your system setup guide.
Note
Whenever the values or object names in this exercise include ##, replace ## with the number of your user.
### Prerequisites
The role was created in the exercise **Create SAP Fiori Spaces and Pages**.
### Task 1: Examine a Plug-In in the Definition of FLP Settings
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_84378CEA111F149B:uebung)
#### Steps
  1. In the _Definition of FLP Settings_ (/UI2/FLP_CONF_DEF) of your SAP S/4HANA (S4H) system, check the technical information of the _UX100_FLP_PLUG_ FLP plug-in and note down the _UI5 Component ID_ and _URL_.
UI5 Component ID:____________________________________________________________
URL:________________________________________________________________________
    1. In the _SAP Easy Access_ menu of your S4H, search for _Definition of FLP Settings_ or start transaction /UI2/FLP_CONF_DEF.
    2. Double-click _Define Launchpad Plug-Ins_ on the left.
    3. Double-click _UX100_FLP_PLUG_ in the _Launchpad Plug-in ID_ column.
    4. Note down the _UI5 Component ID_**sap.ux100.flp.plugin** and _URL_**/sap/bc/ui5_ui5/sap/ux100_flp_plug**.

### Task 2: Create an App Descriptor for an SAP Fiori Launchpad Plug-In
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_EDF799B0ED7CB7B7:uebung)
#### Steps
  1. In the _SAP Fiori launchpad application manager_ of your S4H, create the empty standard catalog **Z_##_TC_FLP_PLUGINS** with title **Z## - SAP Fiori Launchpad Plugins** as local object.
    1. In the _SAP Fiori launchpad_ of your S4H, choose the _Launchpad App Manager_ tile or start transaction /UI2/FLPAM.
    2. In the _SAP Fiori launchpad application manager_ , choose _New Technical Catalog_.
    3. In the _Technical Catalog ID_ field, enter **Z_##_TC_FLP_PLUGINS**.
    4. In the _Technical Catalog Title_ field, enter **Z## - SAP Fiori Launchpad Plugins**.
    5. From the _Technical Catalog Type_ dropdown, select **Standard Catalog**.
    6. Select _Create empty technical catalog only_.
    7. Choose _Local Object_.
  2. Add an SAPUI5 Fiori app descriptor for the _UX100_FLP_PLUG_ plug-in in your _Z_##_TC_FLP_PLUGINS_ catalog using the following values:
| Field  | Value  |
| --- | --- |
| _Semantic Object_  | **Shell**  |
| _Action_  | **plugin**  |
| _SAPUI5 Component ID_  | **sap.ux100.flp.plugin**  |
| _ICF Path_  | **/sap/bc/ui5_ui5/sap/ux100_flp_plug**  |
| _Suppress Tile_  | **checked**  |
    1. In the _Search Term_ field, enter **z_##** and choose _Go_.
    2. In the _Technical Catalogs_ table, choose _Z_##_TC_FLP_PLUGINS_.
    3. Choose _Edit_ in the upper left.
    4. In the _Select Transport Request_ popup, choose _Local Object_.
    5. Choose _Add App_ → _SAPUI5 Fiori App_.
    6. In the _Target Application Fields_ tab, enter the following values:
| Field  | Value  |
| --- | --- |
| _Semantic Object_  | **Shell**  |
| _Action_  | **plugin**  |
| _SAPUI5 Component ID_  | **sap.ux100.flp.plugin**  |
| _ICF Path_  | **/sap/bc/ui5_ui5/sap/ux100_flp_plug**  |
| _Suppress Tile_  | **checked**  |
    7. Choose _Save_.
#### Result
The warning _Transaction code is not entered_ is displayed. This is solved in the next step.
    8. Close the warning message.
  3. For the app descriptor, create the transaction code **Z##_FLPPLUG** with **FLP Plugin ##** as text.
    1. Choose _Edit_ in the upper left.
    2. In the _SAP Fiori ID_ field, enter **Z##_FLPPLUG**.
    3. For the _Transaction Code_ , choose _Click for creation_.
    4. In the _Warning_ popup, choose _OK_.
    5. In the _Create / Display Transaction_ window, in the _Transaction Text_ field, enter **FLP Plugin ##**.
    6. Choose _Create Transaction_.
    7. Close the _Create / Display Transaction_ window.
    8. Choose _Save_.

### Task 3: Copy the Catalog, Assign It to a Role, and Test the Plug-In in the SAP Fiori Launchpad
Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_C20B753EA72C9DA6:uebung)
#### Steps
  1. In the _SAP Fiori launchpad content manager_ for customizing of your S4H, copy the _Z_##_TC_FLP_PLUGINS_ catalog using ID **Z_##_BC_FLP_PLUGIN** and title **Z## - SAP Fiori Launchpad Plugin**.
    1. In the _SAP Easy Access_ menu of your S4H, search for _SAP Fiori launchpad content manager_ or start transaction /UI2/FLPCM_CUST.
    2. In the _SAP Fiori launchpad content manager_ for customizing, select the _Z_##_TC_FLP_PLUGINS_ catalog.
    3. Choose _Copy_.
    4. In the _New ID_ field, enter **Z_##_BC_FLP_PLUGIN**.
    5. In the _New Title_ field, enter **Z## - SAP Fiori Launchpad Plugin**.
    6. Choose _Continue_.
    7. Choose the transport request provided to you.
  2. In the _SAP Fiori launchpad content manager_ of your S4H, assign the _Z_##_BC_MIG_DATA_STATUS_ catalog to the _Z_##_BC_FLP_PLUGIN_ role.
    1. In the _SAP Fiori launchpad content manager_ for customizing, select the _Z_##_BC_FLP_PLUGIN_ catalog.
    2. Choose _Show Usage in Roles_.
    3. In the _Roles containing Catalog Z_##_BC_FLP_PLUGIN_ table, choose _Assign Role_.
    4. In the _Assign Role to Catalog_ popup, for the _Role ID_ field, open the value help.
    5. In the popup, in the _Single Role_ field, enter **z_##***.
    6. Double-click _Z_##_BR_TRAINING_.
    7. In the _Assign Role to Catalog_ popup, choose _Continue_.
  3. Search for changes in the _SAP Fiori launchpad_ of your S4H.
    1. Start or reload the _SAP Fiori launchpad_ of your S4H in the client of your choice.
    2. Choose _Important Information_ in the footer.
    3. Choose _Add bookmark_ in the header on the left.
    4. Choose your user in the upper right corner.
    5. In the _User Actions Menu_ , choose _Help for FLP page_.
    6. Choose any tile starting an SAPUI5 application.
    7. Choose your user in the upper right corner.
    8. In the _User Actions Menu_ , choose _Help for App page_.

[Continue to quiz](https://learning.sap.com/courses/learning-the-basics-of-sap-fiori/adaptation_9f8fd9cb-6b9c-30fa-b63b-d21d4d68faec)
