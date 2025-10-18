# Lab 4: ALM with Power Pages

## Table of Contents

- [Pre-requisites](#pre-requisites)
- [Overview](#overview)
- [Steps](#steps)
  1. [Configure Azure DevOps](#configure-azure-devops)
  1. [Create solution and connect to Git](#create-solution-and-connect-to-git)
  1. [Create Power Pages site](#create-power-pages-site)
  1. [Add site to solution](#add-site-to-solution)
  1. [Configure Power Pipelines](#configure-power-pipelines)
  1. [Deploy to Prod Environment](#deploy-to-prod-environment)
  1. [Activate Site in ProdEnvironment](#activate-site-in-prodenvironment)
  1. [Committing changes to Source Control](#committing-changes-to-source-control)
  1. [Cloning the repository locally](#cloning-the-repository-locally)
  1. [Editing the site in VS Code](#editing-the-site-in-vs-code)
  1. [Pulling changes in Solution Explorer](#pulling-changes-in-solution-explorer)
  1. [Updating Environment Variables](#updating-environment-variables)
  1. [Deploy the updated solution to ProdEnvironment](#deploy-the-updated-solution-to-prodenvironment)
  1. [Verify changes](#verify-changes)
- [Steps to enable Managed Environment](#steps-to-enable-managed-environment)

## Pre-requisites

1. Install VS Code Desktop from this [download link](https://code.visualstudio.com/download).
1. Following steps will work on EDM environments. (This should be enabled by default).

## Overview

In this scenario, we will be doing the following:

![Flow](images/flow.jpg)

## Steps

1. Setup two managed environments, **DevEnvironment** and **ProdEnvironment**. Follow [these](#steps-to-enable-managed-environment) steps to enable managed environment.

### Configure Azure DevOps

1. Navigate to [Azure DevOps Portal](https://aex.dev.azure.com/) and create a new organization.

    ![Create Azure DevOps Organization](images/create-ado-org.png)

1. Create a new project. This will automatically create a git repository with the same name as the project.

    ![Create Azure DevOps Project](images/create-ado-project.png)

1. In the new project, navigate to **Repos** and initialize it with main branch.

    ![Initialize Repo](images/initialize-repo.png)

### Create solution and connect to Git

1. In a new tab, open [Power Pages Maker Studio](https://make.powerpages.microsoft.com/) and select **DevEnvironment** from top right corner.

    ![Select Environment](images/select-environment.png)

1. Click on **Solutions** option from left burger icon to open Solutions Explorer.

    ![Solutions Explorer](images/solution-explorer.png)

1. Click on **Connect to Git** button to setup your git repository for this environment.

    ![Connect to Git](images/connect-to-git.png)

1. Use above created Azure DevOps project to connect to git. You can name the folder as applicable.

    ![Connect to Git Repo](images/connect-to-git-repo.png)

### Create Power Pages site

1. After successful connection, navigate to home and proceed to create your first power pages site **PPCC ALM Dev** using blank template.

    ![Create Power Pages Site](images/create-power-pages-site.png)

    ![Create Power Pages Site 2](images/create-power-pages-site-2.png)

1. Once the **PPCC ALM Dev** site is ready, navigate back to Solutions Explorer and click on **New Solution** to create a new solution.

    ![New Solution](images/new-solution.png)

1. Name the solution **PPCCALMDev**, select **CDS Default Publisher** from Publisher dropdown and click **Create**.

    ![Create New Solution](images/create-new-solution.png)

### Add site to solution

1. Click on **Objects** from the left menu.

    ![Objects Menu](images/objects-menu.png)

1. Click on **Add Existing** button and select **Site** from the dropdown.

    ![Add Existing Site](images/add-existing-site.png)

1. Select the site and click on **Next**.

1. Select **Include All Objects** and click on **Add**.

    ![Include All Objects](images/include-all-objects.png)

    _Note: You can also include specific objects by clicking **Edit Objects** and selecting them individually._

1. Once the site and its related objects are added to the solution, you will see something like below:

    ![Solution with Site](images/solution-with-site.png)

### Configure Power Pipelines

1. Select the newly created solution and click on **Pipelines** from the left menu.

    ![Pipelines Menu](images/pipelines-menu.png)

1. Click on **Create Pipeline** button to create a new pipeline.

    ![Create Pipeline](images/create-pipeline.png)

1. Name the pipeline **PPCC ALM Workshop pipeline** and select **ProdEnvironment** as the target environment and click on **Save**.

    ![Create Pipeline](images/create-pipeline-2.png)

1. Once the pipeline is created, you will see something like below:

    ![Pipeline Created](images/pipeline-created.png)

### Deploy to Prod Environment

1. Click on **Deploy Here** button to deploy the solution to ProdEnvironment.

    ![Deploy Here](images/deploy-here.png)

1. On the fly out panel, click on **Deploy** button to start the deployment.

1. After the initial verification of deployment is complete, you will get an option to click **“Deploy** on the Summary Panel for Power Pipelines **Deploying Solution** panel.

    ![Deploy Solution](images/deploy-solution.png)

1. The deployment will start. Wait for the deployment to complete.

    ![Deployment in Progress](images/deployment-in-progress.png)

1. Once the deployment is complete, switch to **ProdEnvironment** from top right corner in Power Pages Maker Studio.

    ![Switch Environment](images/switch-environment.png)

### Activate Site in ProdEnvironment

1. Click on **Inactive Sites** tab to view the list of inactive sites.

    ![Inactive Sites](images/inactive-sites.png)

1. Click on **Reactive** button to activate the site and then click on **Done**.

    ![Reactivate Site](images/reactivate-site.png)

1. _Optional:_ Preview the site by clicking on **Preview** button.

    ![Preview Site](images/preview-site.png)

## Committing changes to Source Control

1. Go back to **DevEnvironment** and navigate to **Solutions Explorer** and select the **PPCCALMDev** solution.

1. Select **Source Control** from the left menu.

    ![Source Control Menu](images/source-control-menu.png)

1. Verify that the **Changes** tab has the some changes listed and click on **Commit** button.

    ![Commit Changes](images/commit-changes.png)

1. Enter a commit message and click on **Commit** button.

    ![Enter Commit Message](images/enter-commit-message.png)

1. After the commit is successful, click on the commit id to navigate to Azure DevOps and see the changes reflected in the repository.

    ![View Commit in Azure DevOps](images/view-commit-in-ado.png)

1. Notice that there are 3 folders created in the repository:
    1. **powerpagesites** - Contains the Power Pages site related files
    1. **solutions** - Contains the solution related files
    1. **publishers** - Contains the publisher information

    ![Repository Structure](images/repo-structure.png)

### Cloning the repository locally

1. Click on **Files** from the left menu in Azure DevOps to go to the repository view.

    ![Repository View](images/repo-view.png)

1. Click on **Clone** button and then click on **Clone in VSCode**.

    ![Clone Button](images/clone-button.png)

    ![Clone in VSCode](images/clone-in-vscode.png)

1. This will open VS Code Desktop and prompt for the local path to clone the repository.

1. It will ask for authentication, provide your Azure DevOps credentials.

1. If asked to automatically sign-in, select **No, this app only**.

   ![VS Code Sign-in](images/vscode-signin.png)

1. Click on **Open** to open the cloned repository in VS Code.

    ![Cloned Repository in VS Code](images/cloned-repo-vscode.png)

### Editing the site in VS Code

1. Open **Home.webpage.copy.html** file and use GitHub Copilot to add a welcome message to the home page.

    ![Edit Home Page](images/edit-home-page.png)

1. Once the edits are done, save the file and commit and push the changes.

    ![Commit Changes in VS Code](images/commit-changes-vscode.png)

### Pulling changes in Solution Explorer

1. Go back to **Power Pages Maker Studio** in **DevEnvironment** and navigate to **Solutions Explorer**.

1. Select **Source Control** from the left menu and click on **Check for updates** button. _This might take a while._

    ![Check for Updates](images/check-for-updates.png)

1. Click on **Pull** button to pull the latest changes in the solution. _This might take a while._

    ![Pull Changes](images/pull-changes.png)

### Updating Environment Variables

1. From the **Active Sites** tab, click on **Power Pages Management** for your site.

    ![Power Pages Management](images/power-pages-management.png)

1. Click on Site Settings.

    ![Site Settings](images/site-settings.png)

1. Search for the setting **Authentication/Registration/LocalLoginEnabled** and click on it to open.

1. Change the value of **Source** to **Environment Variable**.

    ![Change Source to Environment Variable](images/change-source-to-env-var.png)

1. Create a new environment variable by selecting the text box and clicking on **New**.

    ![Create New Environment Variable](images/create-new-env-var.png)

1. Click on **Discard Changes** to open the environment variable creation panel.

1. Create new environment variable with **Schema Name** and **Display Name** as **LocalLoginEnabled** and set the default value to **True**. Click on **Save & Close**.

    ![Create Environment Variable](images/create-env-var.png)

1. Now, again change the value of **Source** to **Environment Variable** and search for **Local** and select the newly created environment variable from the dropdown. Click on **Save & Close**.

    ![Select Environment Variable](images/select-env-var.png)

1. Navigate back to **Power Pages Maker Studio** and open **Solutions Explorer** and select the **PPCCALMDev** solution.

1. Add the newly created environment variable to the solution by clicking on **Add Existing** > **Environment Variable**.

    ![Add Existing Environment Variable](images/add-existing-env-var.png)

1. Select **LocalLoginEnabled** from the list and click on **Next** and then click on **Add**.

    ![Select Environment Variable](images/select-env-var-to-add.png)

1. The environment variable will be added to the solution.

    ![Environment Variable Added](images/env-var-added.png)

### Deploy the updated solution to ProdEnvironment

1. Go to **Pipelines** tab and click on **Deploy Here** button to deploy the updated solution to **ProdEnvironment**.

1. Click on **Next** and you'll be asked to select a value for the environment variable. Select **No** and click on **Next**.

    ![Set Environment Variable Value](images/set-env-var-value.png)

1. Click on **Deploy** to start the deployment process and wait for the deployment to complete.

### Verify changes

1. Open the website preview in **DevEnvironment** by clicking on **Preview** -> **Desktop**.

    ![Preview Site in DevEnvironment](images/preview-site-devenv.png)

1. Click on **Sign In** button to verify that the local login is enabled.

    ![Local Login Enabled](images/local-login-enabled.png)

1. Now, go back to **Power Pages Maker Studio** and switch to **ProdEnvironment** from top right corner and preview the site.

1. Click on **Sign In** button to verify that the local login is disabled.

    ![Local Login Disabled](images/local-login-disabled.png)

## Steps to enable Managed Environment

1. Navigate to Power Platform Admin Center (PPAC) at <https://admin.powerplatform.microsoft.com/manage/environments>
1. In the Manage tab on the left-hand side, click on **Environments**
1. Select the environment where you want to enable Managed Environments
1. In the ribbon, click **Enable Managed Environments**
1. Click **Enable** in the fly out wizard

    ![Enable Managed Environment](images/enable-managed-environment.png)
