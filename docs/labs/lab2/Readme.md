---
layout: lab
---

# 🧪 Lab 2: Building Power Platform Solutions

The inner loop is where developers spend most of their time - writing code, testing changes, and iterating quickly. In Power Platform, your **solution is your source code**. This lab focuses on working in the inner loop with your Power Platform solution, exploring how solutions exist at different levels of abstraction (binary packages, unpacked metadata files, and traditional source code projects), and how Power Platform Git Integration enables version control collaboration. You'll learn how to handle conflicts when changes occur in multiple places, work across development environments, and integrate AI agents into your ALM workflow. This hands-on lab demonstrates the complete inner-loop lifecycle of managing Power Platform solutions.

✅ Lab tasks

In this lab, you will go through the following tasks:

1. [Import and commit a solution in your dev environment](#-task-1-import-and-commit-a-solution-in-your-dev-environment)
1. [Edit your solution](#️-task-2-edit-your-solution)
1. [Work as a team in multiple environments](#-task-3-work-as-a-team-in-multiple-environments)
1. [Create a new agent](#-task-4-create-a-new-agent)

## 💻 Solution is your Source Code

For low-code makers, your **Power Platform Solution** is your source code - it's the complete description of what you're building that you can open and edit in the Solution Explorer within the maker portal.

## 📦 Understanding Solution Abstractions

The term "solution" can be confusing because it represents different levels of abstraction depending on the context:

### Three Levels of Solution Abstraction

1. **Solution Package (.zip)** - Binary Package
   - Compressed binary version of the metadata and runtime artifacts
   - Used for import/export operations between environments
   - What you see when you export a solution from the Maker Portal.

1. **Unpacked Solution** - Metadata and Runtime Artifacts
   - Collection of individual files: `.msapp`, `.xml`, `.js`, `.dll` files
   - Human-readable metadata that describes your Power Platform components
   - Metadata can be version controlled and merged like traditional source code

1. **Solution Project (.cdsproj)** - Traditional Source Code
   - This is the traditional developer source code format
   - Contains project files, references, and build configurations
   - Used by professional developers with Visual Studio and MS Build

![Solution Abstraction Flow](assets/SolutionsSourceCodeAbstractions.png)

> **Note:** It's not possible to generate traditional source code from runtime artifacts in a solution. Traditional source code must be maintained in a repository by the developer as part of their development workflow.

**Key Insight:** All three formats represent the same logical solution, just at different levels of abstraction. **Power Platform Git Integration covers only the unpacked solution** - it enables version control, collaboration, and deployment of low-code components. **Traditional source code** (like C# plugins, TypeScript PCF components, and project files) should be managed by traditional source code tools and development workflows alongside Power Platform components in your repository.

---

## 📋 Prerequisites

To complete this lab, you need to have the following environments and resources configured:

### Environments

| Environment Name | Environment Type | Purpose |
|---|---|---|
| Dev | Development | Primary development environment for creating and testing solutions |
| HotFix | Development | Secondary environment for hotfix development and multi-environment testing |

### Repository

- **Azure DevOps Repository**: You need an Azure DevOps repository configured with Git integration enabled. This repository will store your solution's unpacked metadata files and enable version control collaboration.

---

## 📥 Task 1: Import and commit a solution in your dev environment

In this task, we will work with the **Solution binary package** (.zip format) as defined earlier in our abstractions. This is the packaged format used for importing and exporting solutions between Power Platform environments.

### Step 1: Import the solution into Power Apps

1. **Navigate to the Power Apps maker portal**
   - Go to [make.powerapps.com](https://make.powerapps.com)
   - Select the environment "Dev"

![Select the environment Dev](assets/EnvironmentList.png)

1. **Access the solution import feature**
   - In the left navigation, click on **Solutions**

   ![Solution menu](assets/SolutionLeftMenu.png)

   - Click **Import solution** at the top of the page

1. **Upload the solution file**
   - Download the solution [ContosoRealEstate](assets/ContosoRealEstate_1_0_0_2.zip) available in the assets folder of this repo.
   - Click **Choose File** or **Browse**
   - Navigate to the `assets` folder in this repository
   - Select the solution `.zip` file provided for this lab
   - Click **Next**

1. **Configure import settings**
   - Review the solution information
   - Click **Import**

![Import solution dialog](assets/IimportSolutionDialog.png)

1. **Wait for import completion**
   - Monitor the import progress

   ![Importing Solution](assets/ImportingSolution.png)

   - Verify the solution appears in your Solutions list

   ![Imported successfully](assets/ImportedSuccessfully.png)

Now repeat the steps above to import the solution in your environment "Hotfix".

### Step 2: Commit the solution using Power Platform Git integration

1. **Enable Git integration** (if not already configured)
   - In the Solutions area, click Connect to Git

   ![Connect to GIT](assets/ConnectToGit.png)

   - Connect to your Azure DevOps Organization. In the dialog, select:
     - Connection type: *Solution*
     - Organization: Select the available
     - Project: Select an available project
     - Repository: select an available Repository
     - Root Git folder: PP

     ![Connect to GIT dialog](assets/ConnectToGitDialog.png)

     Note: if you don't have an organization to select you must create an Azure DevOps Organization.

   - Connect to your repository and branch. In the dialog, select:
     - Solution: ContosoRealEstate
     - Branch: Main
     - Git folder: PP/ContosoRealEstate
     ![Connect to repo dialog](assets/ConnectToGitRepoDialog.png)
   - Click Connect

You are now connect to your GIT repository!

![Connected to GIT](assets/ConnectedToGit.png)

1. **Commit the solution to source control**
   - In **Solution explorer**, open the solution **Contoso Real Estate**
   - Go to **Source control** tab in your solution
   ![Source Control](assets/SourceControl.png)
   - Add a commit message: "Initial import of [solution name]"
   - Click **Commit** to save the solution to your Git repository
   ![Commit Success](assets/CommitSuccessful.png)

1. **Verify the commit**
   - Check your Git repository to confirm the solution files were committed
   - Review the folder structure created by the Power Platform Git integration

> **Expected outcome:** Your solution is now imported into your development environment and committed to source control as an unpacked solution format. You also have imported the solution in a Hotfix environment, not yet connected to your repository.

---

## ✏️ Task 2: Edit your solution

In this task, we will work with the **Solution Explorer** in the Power Apps maker portal as our reference for source code. You'll learn how changes flow between the maker portal and your Git repository, including how to handle conflicts.

### Step 1: Edit the Canvas App with YAML code

1. **Open the solution in maker portal**
   - Navigate to your imported solution
   - Find and open the Canvas app component
   - Switch to **Tree view** in the app designer

2. **Import YAML code snippet**
   - In the app designer, select a screen or control
   - Use **Copy** and **Paste YAML** functionality
   - Paste the provided YAML snippet from the `assets` folder
   - Review the changes in the app designer

### Step 2: Save, publish and commit changes

1. **Save the app**
   - Click **Save** in the app designer
   - Add a meaningful save comment

2. **Publish the app**
   - Click **Publish** to make changes available
   - Confirm the publication

3. **Commit to repository**
   - Go to **Source control** tab in your solution
   - Add commit message: "Updated canvas app with new YAML snippet"
   - Click **Commit**

### Step 3: Make changes from the repository using vscode.dev

1. **Open repository in vscode.dev**
   - Navigate to your GitHub repository
   - Press `.` (period key) to open vscode.dev
   - Or change URL from `github.com` to `vscode.dev`

2. **Find and edit YAML files**
   - Navigate to your solution's unpacked files
   - Find the canvas app `.msapp` folder structure
   - Locate a YAML file (e.g., screen configuration)
   - Make a minor change (update a property value or text)

### Step 4: Commit changes using VS Code

1. **Stage and commit changes**
   - Use the Source Control panel in vscode.dev
   - Stage your changes
   - Add commit message: "Minor YAML update from repository"
   - Commit and push changes

### Step 5: Reverse sync - Get changes from repository

**Important concepts:**

- **Reverse Sync**: Getting code changes from the repository back into your maker portal environment
- **Source of Truth**: In conflict situations, you must decide whether the repository or maker portal version is correct
- **No merging**: Unlike traditional code, you don't merge Power Platform conflicts - you choose one source as authoritative

1. **Perform reverse sync in maker portal**
   - Return to your solution in Power Apps maker portal
   - Go to **Source control** tab
   - Click **Get changes** or **Sync** to pull repository changes
   - Review the incoming changes

2. **Verify changes applied**
   - Open the canvas app to confirm your repository changes are reflected
   - Check that the YAML modifications are visible

### Step 6: Create a conflict scenario

1. **Make simultaneous changes**
   - **In maker portal**: Edit the same canvas app element you modified in the repo
   - **In repository**: Using vscode.dev, make a different change to the same YAML property
   - Commit both changes

2. **Handle the conflict**
   - Attempt to sync in the maker portal
   - **Important**: You'll need to choose your source of truth
   - **Repository wins**: Accept repository version (recommended for team scenarios)
   - **Maker portal wins**: Keep maker portal version and commit over repository

3. **Resolution strategy**
   - Decide on your source of truth based on context
   - Communicate with team about the chosen resolution
   - Document the decision for future reference

> **Expected outcome:** You understand how to work with both maker portal and repository, handle reverse sync, and resolve conflicts by choosing a source of truth.
> **Key learning**: More complex merge scenarios and team collaboration patterns will be covered in the next lab.

---

## 👥 Task 3: Work as a team in multiple environments

In this task, we will simulate team development using multiple Power Platform environments. This demonstrates how different developers can work on the same solution using separate development environments while maintaining code synchronization through Git.

**Prerequisites:** You'll need access to a second development environment for this exercise.

### Step 1: Export solution from your current environment

1. **Navigate to your current development environment**
   - Go to [make.powerapps.com](https://make.powerapps.com)
   - Ensure you're in the environment where you completed Tasks 1 and 2

2. **Export the solution**
   - Go to **Solutions**
   - Select your working solution
   - Click **Export**
   - Choose **Managed** or **Unmanaged** (typically choose **Unmanaged** for development)
   - Click **Next** and then **Export**
   - Download the solution .zip file

### Step 2: Set up the second development environment

1. **Switch to your second development environment**
   - In the Power Apps maker portal, use the environment selector
   - Choose your second development environment
   - If you don't have one, create a new developer environment

2. **Import the solution**
   - Click **Solutions** > **Import solution**
   - Upload the .zip file you exported in Step 1
   - Configure import settings (keep defaults)
   - Click **Import** and wait for completion

### Step 3: Connect to Git repository with a new branch

1. **Create a new branch for the second environment**
   - The new branch will represent the second developer's workspace
   - Branch name suggestion: `dev-environment-2` or `developer-2-workspace`

2. **Configure Git integration**
   - In your imported solution, go to **Settings** > **Git integration**
   - Connect to the same repository you used in previous tasks
   - **Important:** Create and select a new branch (not the main branch)
   - Complete the Git integration setup

3. **Verify branch connection**
   - Confirm you're connected to your new branch
   - Check that the solution can commit to this separate branch
   - This simulates a second developer working independently

**Important concept:** In Power Platform, we recommend maintaining a **1:1 relationship between environment and branch**. Each development environment should be connected to its own dedicated Git branch for clean separation of work.

### Step 4: Make changes in Development Environment 1

1. **Switch back to your first development environment**
   - Return to the environment used in Tasks 1 and 2
   - Open your solution and navigate to the Canvas app

2. **Modify a control label**
   - Open the Canvas app in edit mode
   - Select any control with a label (button, text label, etc.)
   - Change the text property to something new (e.g., "Updated in Dev 1")
   - Save and publish the app

3. **Commit the changes**
   - Go to **Source control** tab
   - Add commit message: "Updated control label in dev environment 1"
   - Click **Commit** to save to your first branch

### Step 5: Make changes in Development Environment 2

1. **Switch to your second development environment**
   - Navigate to your second development environment
   - Open the same solution and Canvas app

2. **Add a new screen**
   - In the Canvas app designer, click **New screen**
   - Choose a screen template or create a blank screen
   - Add some basic controls to the new screen (optional)
   - Save and publish the app

3. **Commit the changes**
   - Go to **Source control** tab
   - Add commit message: "Added new screen in dev environment 2"
   - Click **Commit** to save to your second branch

### Step 6: Merge branches using VS Code

1. **Open repository in VS Code**
   - Navigate to your GitHub repository
   - Press `.` to open vscode.dev (or use GitHub Codespaces)
   - Or clone locally and use desktop VS Code

2. **Create Pull Request or merge directly**
   - **Option A: Pull Request (Recommended)**
     - Create a Pull Request from `dev-environment-2` to `dev-environment-1`
     - Review the changes in both branches
     - Merge the PR after review

   - **Option B: Direct merge using Git commands**
     - Switch to your first branch: `git checkout dev-environment-1`
     - Merge the second branch: `git merge dev-environment-2`
     - Resolve any conflicts if they arise
     - Push the merged changes: `git push origin dev-environment-1`

3. **Handle any merge conflicts**
   - If conflicts occur in Canvas app files, review carefully
   - Choose the appropriate resolution strategy
   - Remember: Power Platform files can be complex to merge

> **Expected outcome:** You've successfully demonstrated team development with separate environments and branches, then merged changes using standard Git workflows.

> **Key learning:** The 1:1 environment-to-branch relationship keeps development organized and makes it easier to track which changes come from which developer or environment.

---

## 🤖 Task 4: Create a new agent

In this final task, we will create a Microsoft Copilot Studio (MCS) agent and configure it to use Dataverse tables as a knowledge source. This demonstrates how AI agents integrate into the Power Platform ALM lifecycle alongside apps and flows.

### Step 1: Create a new Copilot Studio agent

1. **Navigate to Copilot Studio**
   - Go to [copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
   - Ensure you're in the same environment as your solution
   - Click **Create** > **New agent**

2. **Configure the agent**
   - **Name**: Give your agent a descriptive name (e.g., "Lab Solution Assistant")
   - **Description**: Add a brief description of the agent's purpose
   - **Language**: Select your preferred language
   - Click **Create** to initialize the agent

3. **Basic agent setup**
   - Review the default greeting and system message
   - Customize the agent's personality and tone if desired
   - Test the basic conversation flow

### Step 2: Add Dataverse tables as knowledge source

1. **Access Knowledge sources**
   - In your agent, navigate to **Knowledge** section
   - Click **Add knowledge** or **+ Add source**

2. **Connect to Dataverse**
   - Select **Dataverse** as the knowledge source type
   - Choose **Tables** from your current environment
   - Select the tables that were imported with your solution
   - Configure access permissions as needed

3. **Configure knowledge source settings**
   - Set up how the agent should use the table data
   - Configure any filters or specific columns to include/exclude
   - Test the knowledge source connection

### Step 3: Test the agent with Dataverse knowledge

1. **Test knowledge integration**
   - Use the **Test** panel in Copilot Studio
   - Ask questions that should trigger responses from your Dataverse tables
   - Verify the agent can access and use the table data appropriately

2. **Refine the agent behavior**
   - Adjust the agent's instructions based on test results
   - Fine-tune how it presents information from Dataverse
   - Test edge cases and error scenarios

### Step 4: Add agent to your solution and commit

1. **Add agent to solution**
   - Navigate back to **Solutions** in the Power Apps maker portal
   - Open your working solution
   - Click **Add existing** > **Chatbot**
   - Select your newly created agent
   - Add it to the solution

2. **Commit the agent to source control**
   - Go to **Source control** tab in your solution
   - You should see the agent files in the pending changes
   - Add commit message: "Added Copilot Studio agent with Dataverse knowledge source"
   - Click **Commit**

3. **Verify agent in repository**
   - Check your Git repository to see the agent files
   - Review the agent's metadata and configuration files
   - Note how the agent integrates with your overall solution structure

> **Expected outcome:** You have successfully created a Copilot Studio agent that uses Dataverse tables as a knowledge source, integrated it into your Power Platform solution, and committed it to source control as part of your ALM workflow.
> **Key insight:** AI agents are now first-class citizens in Power Platform ALM, following the same source control patterns as apps, flows, and other solution components.