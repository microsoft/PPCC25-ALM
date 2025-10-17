# Lab 4: Scenario 1 - Power Pages Site (Enhanced Data Model)

## Pre-requisites

1. Install VS Code Desktop from this [download link](https://code.visualstudio.com/download).
1. Following steps will work on EDM environments. (This should be enabled by default).

## Overview

In this scenario, we will be doing the following:

![Flow](images/flow.png)

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

## Steps to enable Managed Environment

1. Navigate to Power Platform Admin Center (PPAC) at <https://admin.powerplatform.microsoft.com/manage/environments>
1. In the Manage tab on the left-hand side, click on **Environments**
1. Select the environment where you want to enable Managed Environments
1. In the ribbon, click **Enable Managed Environments**
1. Click **Enable** in the fly out wizard

    ![Enable Managed Environment](images/enable-managed-environment.png)
