# Working with Branches

*Source: https://learning.sap.com/courses/advanced-sapui5-development/working-with-branches_f65b97a1-6936-44f2-a56b-9aa5ba5076ca*

Objective
After completing this lesson, you will be able to use Git branches for starting an independent line of development.
## Branches in GIT
Git provides a concept called branch. The default branch is called main branch. The main branch contains usually the code of the current productive running code line.
  * serves as an abstraction for the staging and commit process.
  * works with an independent working directory and staging area.
  * is a reference to a commit.

### GIT Usage
  * git branch List all branches in the repository.
  * git branch <branch name> Create a new branch.
  * git branch –d <branch name> Delete a branch.

### Different Branch Types
Different branch types are used to represent different development activities as indicated by the example branches in this image:
![Illustration showing different branch types : Master Branch, Feature Branch and BugFix branch.](../images/f0bf5e8b91cb7010.png)
### git Checkout
![Illustration of the checkout for creating a feature branch](../images/3e22a576458d71a8.png)
git checkout allows switching between different branches. The following are examples of usage:
  * git checkout <yourbranch> Switch to a branch.
  * git checkout –b <yourbranch> Create and checkout a new branch.
  * git checkout –b <newbranch> <existingbranch> Create and checkout a branch from an existing branch.

### git Merge
![Illustration of the merge scenario.](../images/bfc7fd53828d41fe.png)
git merge <yourbranch>Merge a branch into the current branch.
## Work with Git Branches
### Business Example
In this exercise, you will learn how to work with branches.
Note
SAP BTP Platform and SAP Business Application Studio are cloud services. Due to the nature of cloud software, the naming of fields and buttons, as well as the content of the steps, may differ from the exercise solution provided here.
### Task 1: Create and Work with a Feature Branch
#### Steps
  1. Open the SAP Business Application Studio.
  2. Create a new branch with the name **featureA**. You can create and check out branches directly through the _Git: Checkout_ command over the command palette of the SAP Business Application Studio.
    1. Open the command palette, by choosing _View_ → _Find Command…_ or by pressing F1 (on your keyboard) and type into the opened input field **Git**. (A dynamic list with the Git commands will appear).
    2. Execute the command _Git: Checkout to..._
    3. Choose _Create new branch…_
![Screenshot of the command line. Choose Create new branch](../images/7b4f219f2c000cbd.png)
    4. Enter **featureA** into the input field and press the Enter key (on your keyboard).
![Screenshot of the command line. Enter branch name.](../images/d8af4d9ba8014721.png)
    5. Open the Git view and observe that the new branch is selected now.
![Screenshot of the Git Pane. Future changes will now be commited to the new branch](../images/b907c7de199fdbf2.png)
  3. Add a new folder with the name **util** to your _epository_ project _webapp_ folder.
    1. From the context menu of your _repository_ project _webapp_ folder, choose _New Folder_.
    2. Enter **util** and press the Enter key (on your keyboard).
  4. Add a new file with the name **Formatter.js** to the newly created folder _util_. Then save your changes and close the file.
    1. From the context menu of your _util_ folder, choose _New File_.
    2. Enter **Formatter.js** and press the Enter key (on your keyboard).
    3. Save your changes and close the file.
    4. Check to ensure that the artefacts are created correctly. Your folder and file structure should now look like what we see in the following figure.
![Screenshot of the project structure.](../images/e60c0f6aed48bd23.png)
  5. Stage and commit your changes to the local Git repository. Use **Formatter added** as the commit message.
    1. Open the Git view and look at the commit section. As you can see, the _Formatter.js_ file is now marked as _unstaged (U)_ and located under _Changes_.
![Screenshot of the Git Pane showing the formatter.js file with the flag U \(Untracked\).](../images/96495cd8b77edecd.png)
    2. Now, stage all changes. You can stage the Formatter.js file directly by choosing its _+_ symbol (Stage Changes). Now the _Formatter.js_ file should be marked as _staged (A)_ and located under _Staged Changes_.
![Screenshot of the Git Pane showing the file with the flag A \(added\).](../images/9589d74b6310d920.png)
    3. Commit the files that you have staged in your local Git repository. For the commit, enter **Formatter** added in the _Message_ input field of the Git view and select the _Commit_ button or click on the checkmark symbol. Now, there should be zero changes.
![Screenshot of the Git Pane. All changes have been committed.](../images/6049270ff7222004.png)
  6. Switch to the _main_ branch by using the _Git: Checkout to_ command. Then merge the _featureA_ branch and the _main_ branch. For the merge, use the _Merge…_ action from the Git view.
    1. Open the command palette, by choosing _View_ → _Find Command…_ or pressing F1 (on your keyboard).
    2. Execute the command, _Git: Checkout to..._
    3. Choose _main_.
![Screenshot of the command line. Choose the main branch.](../images/efc38c4a803c15d9.png)
    4. Check the folder structure and the artefacts of your project. As you can see in the main branch, the new _util_ folder and the _Formatter.js_ file are not displayed.
![Screenshot of the project structure. The formatter.js file is no longer there.](../images/b979578432e4846a.png)
    5. Open the Git view. For the merge, select the three dots symbol (_Views and More actions…_) and choose _Branch_ → _Merge Branch…_
![Screenshot of the Git Pane menu options. Choose Branch → Merge Branch.](../images/57cd8904a490794d.png)
    6. Choose the _featureA_ branch.
![Screenshot of the command line. Choose featureA branch.](../images/fef2718c5ab35f6c.png)
    7. Check the artefacts of your project, which should appear as it is shown in the following figure.
![Screenshot of the project structure. The formatter.js file is now there.](../images/4f48570217e6f291.png)
  7. Perform a Push request to add the changes to the master branch of your remote Git repository. Use the _Push to…_ action from the Git view.
Caution
If multiple people are working on a remote Git repository, you should Pull before you Push, but in this case it is not necessary.
    1. Open the Git view.
    2. Choose the three dots symbol (_Views and More Actions…_) and then choose _Pull, Push_ → _Push to…_
![Screenshot of the Git Pane menu options. Choose Pull,Push → Push to...](../images/4df1ff06730187d8.png)
    3. In the input field, choose _origin_.
![Screenshot of the command line. Choose origin.](../images/0ff09b4a8f259fc9.png)
  8. Check the content of your remote Git repository on GitHub.
    1. Visit <https://github.com/> and log into your account.
    2. Open your remote Git repository _trainingrepository_.
    3. Observe the content of your repository.
![Screenshot of the github web page showing the last stage of the app.](../images/dc880439f08d59d0.png)
    4. To see the four commits, click on the _clock_ symbol.
![Screenshot of the github web page showing the 4 stages.](../images/6168a952ef6aed19.png)

[Continue to quiz](https://learning.sap.com/courses/advanced-sapui5-development/version-control-working-in-teams)
