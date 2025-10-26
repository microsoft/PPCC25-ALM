## Connect to the Power Platform using the Power Platform Command-Line Interface (CLI)

1. In your codespace, click on the **Power Platform** icon in the left navigation

    ![Power Platform icon in the left navigation](assets/power-platform-icon.png)

    You'll more than likely see that there is "No auth profiles found on this computer". Let's create one.

    ![Screenshot of no auth profiles found](assets/no-auth-profiles-found.png)

1. If you don't see it open already, let's open the Terminal. Click on the Burger menu icon in the top left corner and then hover over **Terminal** and then click **New Terminal**

    ![Screenshot of new terminal menu](assets/new-terminal.png)

    A terminal window has now been opened for you. This is where you will write all of the following commands in this lab and in the upcoming labs as well.

1. Type the following command in the terminal and then press **Enter**:

    ```bash
    pac auth create --deviceCode
    ```

1. You will be prompted to use a web browser to authenticate. Copy (**ctrl + c**) the ```code``` that is provided in the terminal and then **Ctrl + click** on the link that is provided in the terminal.

    ![Screenshot of the terminal with the code and link](assets/terminal-with-code-and-link.png)

    Once you click on that link, it will open a new browser tab where you will have to paste that code into the browser and then click **Next**

    > **Note:** 
    > If you are using a Mac, you can **Ctrl + click** on the ```link``` that is provided in the terminal and then enter the ``code`` provided.

    ![Enter code and click next](assets/enter-code.png)

1. Pick the account that was provided to you. If you can't see it on screen then log in.

    ![Screenshot of the account selection page](assets/account-selection.png)

1. Then type in your password and click **Sign in**

    You will then see a page asking if you're trying to sign in to Power Platform CLI - pac.

    ![Screenshot of the Are you trying to sign in to Power Platform CLI - pac? page](assets/sign-into-pac-cli.png)

1. Click **Continue**

    You'll then see a prompt confirming that you have successfully signed in to Power Platform CLI - pac. Close the browser tab and return to your codespace.

1. Refresh the Auth Profiles section by clicking on the **Refresh** button next to "Auth Profiles"

    ![Screenshot of the Auth Profiles section with the Refresh button](assets/refresh-auth-profiles.png)

    You should now see at least one auth profile. If you have more than one, you can select the one you want to use by clicking on the **Select Auth Profile** button next to the auth profile.

    ![Select Auth Profile](assets/select-auth-profile.png)