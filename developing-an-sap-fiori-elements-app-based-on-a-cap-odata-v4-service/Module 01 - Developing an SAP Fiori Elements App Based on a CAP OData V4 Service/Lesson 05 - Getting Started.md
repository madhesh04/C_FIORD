# Getting Started

*Source: https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/getting-started_e9e6df20-b8a7-4af8-bd47-6d50c7c4a6ee*

Objective
After completing this lesson, you will be able to get a free account on SAP BTP, create a dev space for business applications. and clone the initial CAP project to your workspace.
## Create a Free Trial Account on SAP BTP
SAP Business Technology Platform (SAP BTP) is a technology platform that brings together data and analytics, artificial intelligence, application development, automation and integration. In this lesson, you will create a free trial account on SAP BTP and set up SAP Business Application Studio for development of SAP Fiori elements projects with CAP. You will not use any other tools from SAP BTP in this course.
### Prerequisites
You must complete the steps below before continuing with the rest of the course.
### Steps
  1. Create your free trial account on SAP BTP by following the steps described in this tutorial: [Get a Free Account on SAP BTP Trial](https://developers.sap.com/tutorials/hcp-create-trial-account.html).
The SAP BTP Trial offering contains many of the most important services and tools for development on the platform.
![SAP BTP Trial home page](../images/7b6ca7dbee7e9ea4.png)

## Application Development Environment
In this training you will use SAP Business Application Studio as a development environment. SAP Business Application Studio is the integrated development environment (IDE) included with SAP Build Code. As an alternative you can use Visual Studio Code (VS Code).
![The user interface of VS Code](../images/b0bfe197f7c15903.png)
You can download it from <https://code.visualstudio.com/>.
![Comparison between the main features of SAP Business Application Studio and VS Code](../images/af087668fcf4af61.png)
## Set Up SAP Business Application Studio for Development and Create a Development Space
You need to set up SAP Business Application Studio before continuing with the other lessons.
### Prerequisites
You have completed the exercise Create a Free Trial Account on SAP BTP in the unit Getting an Overview of SAP Fiori Elements for OData V4 (lesson: Getting Started).
### Steps
  1. Set up SAP Business Application Studio for development by following the steps in this tutorial: [Set Up SAP Business Application Studio for Development](https://developers.sap.com/tutorials/appstudio-onboarding.html).
  2. Create a development space in SAP Business Application Studio for developing business applications. Follow the steps in this tutorial: [Create a Dev Space for Business Applications](https://developers.sap.com/tutorials/appstudio-devspace-create.html).
Note
Make sure you choose Full Stack Cloud Application as the application type.

## Clone the Initial Application Project, Set Up and Run the Application in SAP Business Application Studio
GitHub is a popular cloud-based Git repository for software projects. The exercise files for this course, along with their solutions, are stored on GitHub. For more information, see [GitHub](https://github.com/). To work on the exercises in SAP Business Application Studio, you need to clone the project first.
### Task Flow
You will first clone the initial project from the GitHub repository to your SAP Business Application Studio instance. Then, you will perform the initial set up so you can run the app in SAP Business Application Studio.
### Prerequisites
You have completed the exercises Set Up SAP Business Application Studio for Development and Create a Development Space in the unit Getting an Overview of SAP Fiori Elements for OData V4 (lesson: Getting Started).
### Steps
  1. After your dev space is up and running, navigate to it by clicking on its name. SAP Business Application Studio opens.
  2. Clone the initial application project from [fiori-elements-v4-cap-advanced](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced.git).
    1. In SAP Business Application Studio, open the command palette using **Ctrl** + **Shift** + **P** (Windows/Linux) or **Command** + **Shift** + **P** (Mac). In the popover, choose **SAP Business Application Studio: Git Clone**.
    2. Enter the GitHub URL: <https://github.com/SAP-samples/fiori-elements-v4-cap-advanced.git>.
  3. Select _/home/user/projects/_ as the folder to clone the project into.
  4. Open the cloned project from _File > Open folder_ and select _projects_.
  5. Switch to the initial-app-state branch.
    1. Open the terminal by selecting _Open in Terminal_ from the context menu of the cloned project name.
    2. Execute the command git checkout initial-app-state in the terminal.
![Switching to the initial-app-state branch in the terminal](../images/612f1e5d5eb85a18.png)
Note
Alternatively, you can follow these steps to switch to the initial-app-state branch:
      1. Select _main_ from the bottom bar.
      2. In the middle of the screen, a dialog will appear titled _Select a branch or tag to checkout_.
      3. Start typing the branch name until it is displayed.
      4. Select the branch.
      5. A popup will then appear with the message _Your local changes will be overwritten by checkout_.
      6. Select the _Stash and Checkout_ option.
  6. Execute npm install in the terminal.
![Executing npm install in the terminal](../images/3f1e94552d64cc58.png)
#### Result
This will install all the dependencies of your project that are listed in the package.json and package-lock.json file, into a new folder called node_modules within the root of your project. Ignore any messages about deprecated dependencies, as long as there are no errors in the log.
  7. In the terminal, start a CAP server by typing cds watch.
The CAP server serves all the CAP sources from your project. It also keeps track of all the files in your projects and restarts the server whenever you make a change in your project. Your changes will immediately be served; you don't have to do anything else.
  8. Open the app in the browser by clicking _Open in a New Tab_ in the popup window in the bottom right corner.
  9. In the page that opens, select /travel_processor/webapp/index.html under _Web Applications_.
![Welcome page of @sap/cds Server](../images/80b72ff3ba9e32fe.png)
#### Result
The app starts in the browser.![The user interface of the app in the browser](../images/4b023545561cd6be.png)

### Result
You have set up the development environment you will need to complete other lessons in this course.
You have created a BTP trial account, set up SAP Business Application Studio for development and created a dev space. You have also cloned the initial project from the GitHub repository. The app is now running in the browser.
You are now ready to start with the training exercises.
### Next Steps
For more information, see [Preview an SAP Fiori Elements CAP Project.](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/1dc179a7f74d48c7816e90b867058887.html)
## Overview of All Simulations
We have provided a list of all simulations used in this training for your reference. The simulations allow you to experience the look and feel of the solution and explore the supported SAP Fiori elements features. The simulations serve as an entry point for the exercises that you can do by yourself in SAP Business Application Studio, where you can explore the features and functions in depth. All the solutions for the exercises are available on [GitHub](https://github.com/SAP-samples/fiori-elements-v4-cap-advanced/tree/initial-app-state).
The overview provided below is for your reference only. You don’t need to navigate through all simulations at this point in the training. The individual simulations are referenced again in those parts of the training where they fit best. The overview is intended as a central point of entry in case you ever want to access any simulation directly.
Please note the following: When you click on a simulation, it opens in the same browser window. Therefore, we recommend not to close the browser window but to always leave the simulation using the exit button available on the UI.
Below you will find a list of all simulations.
Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=slide!SL_39DCA07275C5AAA9)
[Continue to quiz](https://learning.sap.com/courses/developing-an-sap-fiori-elements-app-based-on-a-cap-odata-v4-service/getting-an-overview-of-sap-fiori-elements-for-odata-v4_34213e40-71b3-33c8-a315-7cf7d28e9ee8)
