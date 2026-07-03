# Version Control - Working in Teams

*Source: https://learning.sap.com/courses/advanced-sapui5-development/working-with-git_de59cb29-ed41-43a4-b17e-cc48e7e6a6d4*

Objective
After completing this lesson, you will be able to use GIT as a version control system for tracking changes in files.
## GIT Version Control System
In software projects, it Is important to track changes on files. A version control system helps you to track these changes. A version control is a system that records changes to a file or set of files over time so that you can recall specific versions. GIT is such a version control system. The SAP Business Application Studio comes with a built in GIT-Client to interact with the GIT-system. The GIT-system may be installed on premise or a cloud service like <http://github.com>. Lets take a look at the features, the states and the workflow:
### Features
  * GIT works like a set of snapshots, with every commit GIT takes a snapshot of the current state of the underlying files. For unchanged files, only a reference to the file is stored.
  * GIT is a free and open source distributed version control system.
  * GIT is designed to handle small to very large projects, It is designed for speed and efficiency.
  * GIT supports local branching and staging.
  * With GIT, most operations require local files and resources only, almost every operation can be done offline.
  * GIT uses checksums based on SHA-1 hashes.

### GIT States
  * **Committed:** The data is safely stored in the local database.
  * **Modified:** Files were changed but not yet committed to the local database.
  * **Changed:** Files were marked as modified in the current version and go into the next commit snapshot.

### GIT Workflow
  * **Working Tree:** Modify files in the working tree.
  * **Staging Area:** Staging Area: Stage the files/add snapshots of files to the staging areas.
  * **GIT Repository:** Perform a Commit. Takes the files from the staging area and stores the snapshot permanently in the local GIT repository.

For more information, visit <https://git-scm.com>
### GIT Procedure
The procedures for getting started with GIT repositories are provided in the following figure.
![Illustration of the GIT processes: Access project , initialize, stage files and commit changes. Or access project and clone repository.](../images/4bb7a1a38012a2a0.png)
The figure shows you the two options regarding how to start with GIT repositories:
  1. Import an existing directory into GIT.
  2. Clone an existing GIT repository from a server.

Watch this video to learn about GIT Working Directories.
Settings
## Work with a Local GIT Repository
### Business Example
In this exercise, you will learn how to work with a local Git Repository.
Note
SAP BTP Platform and SAP Business Application Studio are cloud services. Due to the nature of cloud software, the naming of fields and buttons, as well as the content of the steps, may differ from the exercise solution provided here.
### Steps
  1. Open your training SAP Business Application Studio.
  2. Create a new SAP Fiori Freestyle project using the following information.
#### SAP Fiori Freestyle Project Information
| Field  | Value  |
| --- | --- |
| Template  | _SAP Fiori application_  |
| Template Type  | **SAP Fiori**  |
| Template  | _Basic_  |
| Data source  | **None**  |
| View name  | **Main**  |
| Module name  | **repository**  |
| Application title  | **Repository-integration**  |
| Application namespace  | **student.com.sap.training.advancedsapui5**  |
| Description  |  **A Fiori Application**.  |
| Project folder path  | **/home/user/projects**  |
Leave other fields and radio buttons as default values.
    1. Perform this step as shown in a previous exercise.
  3. Open the terminal for the _repository_ folder. Initialize the local GIT repository by executing the following command: git init.
    1. Open the terminal for the _repository_ folder by choosing _Open in Integrated Terminal_ in the contextual menu.
    2. Initialize the local GIT repository by executing the given command.
  4. Stage all changes over the Git view for the first commit. The Git view is located on the left side menu in the form of a _branch_ symbol. If you open it, you will see all changes. You can stage all changes by choosing the three dots symbol and in the dropdown menu, _Changes_ → _Stage All Changes_.
    1. From the left side menu of the SAP Business Application Studio, choose the _branch_ symbol _(Source Control_) to open the Git view.
    2. Check the commit section of the Git view (located under the _Message_ input field). The files are marked as untracked (U) and located under _Changes_.
![Screenshot of the Git Pane showing all files with the flag U \(Untracked\).](../images/8ce123a3a4154090.png)
    3. Now stage all changes for the first commit. For the staging, select the three dots symbol (_Views and More actions…_) and choose _Changes_ → _Stage All Changes_.
![Screenshot of the Git Pane menu options.](../images/47c58494f72461f0.png)
    4. Check the commit section of the Git view. As you can see, the files are now marked as added (A) and located under _Staged Changes_.
![Screenshot of the Git Pane showing all files with the flag A \(Added\).](../images/644870c9186cca96.png)
  5. Commit the files that you have staged in your local Git repository. Use the Git view for the commit and _Initial Commit_ as commit message. You can then go back to the _Explorer_ pane.
    1. Commit the files that you have staged in your local Git repository. For the commit, just type in **Initial Commit** into the _Message_ input field of the Git view and select the _Commit_ button or choose the checkmark symbol.
![Screenshot of the Git Pane. A comment has been entered and files are ready for commit.](../images/73328b921c8c96e1.png)
    2. There will be zero changes within the Git view:
![Screenshot of the Git Pane. Changes have been committed. No files are displayed any more.](../images/aade8194ae9532d3.png)
    3. Go back to the _Explorer_ pane.
  6. Add the listed view of type XML in the view folder and the corresponding controller of type JavaScript in the controller folder of your project. To create the files, use _Copy_ and _Paste_ in the context menu of the _Main.view.xml_ and _Main.controller.js_ files. Rename them to the listed view and controller file names. In the created _Detail.view.xml_ file, you need to change part of the controllerName attribute from Main to Detail and remove the displayBlock attribute. Then change the value of the title attribute of the Page element to the string Title. A string is sufficient for this exercise, you do not need to use i18n. In the created _Detail.controller.js_ file, you need to change part of the controller name in the extend function from Main to Detail.
#### View and Controller File Names
| View file name  | Controller file name  |
| --- | --- |
| **Detail.view.xml**  | **Detail.controller.js**  |
    1. Add the _Detail.view.xml_ file in the view folder and the corresponding _Detail.controller.js_ file in the controller folder of your project. Use _Copy_ then _Paste_ in the context menu of the _Main.view.xml_ and _Main.controller.js_ files to create the files. Now, rename them.
    2. In the created _Detail.view.xml_ file, you need to change part of the controllerName attribute from Main to Detail and remove the displayBlock attribute. Then change the value of the title attribute of the Page element to the string Title. A string is sufficient for this exercise, you do not need to use i18n.
Code Snippet
Copy codeSwitch to dark mode

```

12345678910

<mvc:View controllerName="student.com.sap.training.advancedsapui5.repository.controller.Detail"
     xmlns:mvc="sap.ui.core.mvc"
     xmlns="sap.m">
  <Page id="page" title="Title">
    <content />
  </Page>
</mvc:View>

```

    3. In the created _Detail.controller.js_ file, you need to change part of the controller name in the extend function from Main to Detail. The last part of the string should look like the following:
Code Snippet
Copy codeSwitch to dark mode

```

12

repository.controller.Detail", {

```

  7. Stage your changes and commit them with the commit message, _Detail view and controller added_ , and come back to the _Explorer_ pane.
    1. Open the Git view and check the commit section. As you can see, the _Detail.controller.js_ and _Detail.view.xml_ files are marked now as _untracked_ (U) and located under _Changes_.
![Screenshot of the Git Pane showing the two new files with the flag U \(Untracked\).](../images/46a9c0a2ae6a433d.png)
    2. Now, stage all changes. For the staging, select the three dots symbol (_Views and More actions_ …) and then on _Changes_ → _Stage All Changes_. Alternatively, you can stage the files individually by selecting the _+_ symbol (_Stage Changes_) for every file. Now, the files should be marked as added (A) and located under _Staged Changes_.
![Screenshot of the Git Pane showing the two files with the flag A \(Added\).](../images/aef214e9505b39cd.png)
    3. Commit the files that you have staged in your local Git repository. For the commit, just enter **Detail view and controller added** into the _Message_ input field of the Git view and select the _Commit_ button or choose the checkmark symbol. Now, there should be zero changes.
![Screenshot of the Git Pane. Changes have been commited. No files are displayed any more.](../images/94f64f0df0815a7d.png)
    4. Come back to the _Explorer_ pane.
  8. Open the _Detail.view.xml_ file and assign the value Detail to the title attribute of the Page element. For this exercise, there is no need to use i18n, just assign the value Detail as a string. Then save your changes.
    1. Open the _Detail.view.xml_ file.
    2. Change the value of the title attribute of the Page element to Detail:
Code Snippet
Copy codeSwitch to dark mode

```

123456

<Page id="page" title="Detail">
  <content />
</Page>

```

    3. Save your changes.
  9. Stage your changes and commit them with the Commit message, **Detail view title changed**.
    1. Open the Git view. As you can see, the _Detail.view.xml_ file is now marked as modified (M) and located under _Changes_.
![Screenshot of the Git Pane showing the view file with the flag M \(Modified\).](../images/528a1e5fa50d5cad.png)
    2. Now, stage the changes. For the staging, you can select the _+_ symbol (_Stage Changes_) for the _Detail.view.xml_ file. When this action is complete, the _Detail.view.xml_ file should still be marked as modified (M) but is now located under _Staged Changes_.
![Screenshot of the Git Pane showing the file with the flag M \(Modified\) as staged.](../images/2fa2056738a7064e.png)
    3. Commit the files that you have staged in your local Git repository. For the commit, enter **Detail view title changed** in the _Message_ input field of the Git view and select the _Commit_ button or select the checkmark symbol. Now, there should be zero changes.
  10. Select the _Git: View history (Git log)_ icon to see the history of commits. You should see all three commits done in this exercise:
![Screenshot of the Git History Pane showing all three commits.](../images/ea54eddd81e30b6f.png)

## Work with a Remote Git Repository
### Business Example
In this exercise, you will learn how to create and work with a remote Git repository.
As we have seen in previous exercise, SAP Business Application Studio has a local repository for GIT. However, the recommendation is always to have the work saved in remote repositories. Remote repository can be public or private (also knows as Corporate GIT).
For this exercise, we will focus on using the Public GIT in particular GitHub <https://github.com/>. You can use any other if you already have an account or are familiar with the tool.
Note
SAP BTP Platform and SAP Business Application Studio are cloud services. Due to the nature of cloud software, the naming of fields and buttons, as well as the content of the steps, may differ from the exercise solution provided here.
### Steps
  1. If you do not have a GitHub account, visit <https://github.com/> and create one. Make sure that you are using a valid email address. Furthermore, make sure that you are able to access the email account.
    1. Go to <https://github.com/> and choose _Sign up_.
    2. Follow the account creation process step by step.
  2. Go to <https://github.com/> and log into your account. Then create a new repository with the following information:
#### Repository Information
| Field  | Value  |
| --- | --- |
| Repository name  | trainingrepository  |
| Description  | Repository for training  |
| Repository visibility  | Private  |
    1. In the upper-right corner of any page, use the _plus(+)_ dropdown menu, and select _New repository_.
    2. Enter **trainingrepository** as the _Repository name_.
    3. Enter **Repository for training** as the _Description_.
    4. Choose _Private_ as repository visibility.
    5. Choose _Create repository_.
  3. Create a personal access token with the listed information. After the creation of the personal access token, ensure you copy and save it because you will not be able to see it again and you will need to insert it into a file of the SAP Business Application Studio. You can create the personal access token in the _Developer settings_ of your GitHub account.
#### Personal Access Token Information
| Field  | Value  |
| --- | --- |
| Note  | training  |
| Select scope  | repo, delete_repo and write:discussion  |
    1. Open the personal settings of your account by clicking on your account in the upper right corner, and choose _Settings_ from the dropdown menu.
    2. Choose _Developer settings_.
    3. Choose _Personal access tokens_.
    4. Choose _Tokens (classic)_.
    5. Choose _Generate new token_ → _Generate new token (classic)_.
    6. Enter **training** at _Note_ and select _repo_ , _delete_repo_ and _write:discussion_ at _Select scopes_. Choose _Generate token_.
    7. Make sure to copy and save your new personal access token now because you will not be able to see it again; you will need to insert it into a file of the SAP Business Application Studio.
  4. Open the SAP Business Application Studio.
  5. Open the terminal for the _repository_ folder. Set your email address and username for your Git account by executing the following commands:
     * git config --global user.email "<your github email address >"
     * git config --global user.name "<your github username>"
    1. Open the terminal for the _repository_ folder. Set your email address and username by executing the listed commands.
  6. In order to save the personal access token within the SAP Business Application Studio, create a **.netrc** file within the _/home/user_ folder with the listed information. Only one space is required between the key and the value.
#### Content of the .netrc File
| Key  | Value  |
| --- | --- |
| machine  | github.com  |
| login  | <Your GitHub email address>  |
| password  | <Your personal access token from step 2>  |
    1. Choose _File_ → _Open Folder…_.
    2. Enter **/home/user/** and choose _OK_.
    3. Choose the _New File_ icon.
    4. Enter **.netrc** and press the Enter key (on your keyboard).
    5. Enter the listed key-value pairs. There is no need to use **:** or **=** for the key-value pairs. Only one space is required between the key and the value.
    6. It will look like what we see in the following figure:
![Screenshot of the .netrc file.](../images/f6e83a00faa3dfd7.png)
    7. Save your changes.
  7. Open the _repository_ workspace. Open the terminal for the _repository_ folder and assign the new remote Git repository to your project. To assign the new remote Git repository to your project, you can use the following command with the URL of your _trainingrepository_ remote Git repository, which can be found on GitHub: git remote add origin https://<Git-Host-URL>/<full-path-to-repository>
    1. Choose _File_ → _Open Recent …_ to go back to your projects.
    2. From the context menu of the _repository_ folder, choose _Open in Integrated Terminal_.
    3. Within the terminal, execute the following command with the URL of your _trainingrepository_ remote Git repository, which can be found on GitHub: git remote add origin https://<Git-Host-URL>/<full-path-to-repository>
  8. Push the changes from your local Git repository to the remote Git repository. You can use the _Push to…_ action from the Git view.
Note
If a window appears on the bottom right of your screen asking for periodical git Fetch, answer _No_.
    1. Open the Git view.
    2. Choose the three dots symbol (_Views and More Actions…_) and choose _Pull, Push_ → _Push to…_
![Screenshot of the Git Pane menu options. Choose Pull,Push → Push to...](../images/bce2d0006f3477b2.png)
    3. In the input field, choose _origin_.
![Screenshot of the command line. Choose origin.](../images/c19bbf2fb654010b.png)
    4. If the following window appears, answer/select _No_.
![Screenshot of the message box. Choose No.](../images/c4400d34153493ac.png)
  9. Check the content of your remote Git repository on GitHub.
    1. Go to <https://github.com/> and log into your account.
    2. Open your remote Git repository, _trainingrepository_.
    3. Observe the content of your repository.
![Screenshot of the github web page showing the actual state of the app.](../images/dfa7497218bec512.png)
    4. To see the three commits, choose the clock symbol.
![Screenshot of the Github web page showing the history of changes.](../images/04fee829ab31bf2b.png)
