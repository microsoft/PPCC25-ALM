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

1. Once the **PPCC ALM Dev** site is ready, navigate back to Solutions Explorer and create a new solution named **PPCCALMDev**.

    ![New Solution](images/new-solution.png)

1.

## Steps to enable Managed Environment

1. Navigate to Power Platform Admin Center (PPAC) at <https://admin.powerplatform.microsoft.com/manage/environments>
1. In the Manage tab on the left-hand side, click on **Environments**
1. Select the environment where you want to enable Managed Environments
1. In the ribbon, click **Enable Managed Environments**
1. Click **Enable** in the fly out wizard

    ![Enable Managed Environment](images/enable-managed-environment.png)
