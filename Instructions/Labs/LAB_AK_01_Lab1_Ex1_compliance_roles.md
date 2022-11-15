---
lab:
    title: 'Exercise 1 - Manage Compliance Roles'
    module: 'Module 1 - Implement Information Protection'
---


# Lab 1 - Exercise 1 - Manage Compliance Roles

In your role as Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. you are tasked to configure the new Microsoft 365 tenant of your organization, to meet the organizations compliance requirements. Contoso Ltd. is a company with a headquarters in the United States and several new subsidiaries in the European Union and your organization needs to make sure the new Microsoft 365 tenant fulfills the legal requirements of different countries and regulatory requirements of your industry sector.

### Task 1 – Assign Compliance Roles

In this exercise, you will follow the principal of least privilege and use the default Global Administrator to assign the Compliance Admin role to Joni Sherman, which is required to perform the operations described in this lab.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account. The password should be provided by your lab hosting provider.

1. Make sure all available Windows Updates are installed and the client does not require a restart to finish update installation.

    [//]: <> (Installing the latest OS updates will also update the Edge browser to the new chromium version required to do this labs.)

1. Open **Microsoft Edge** from the taskbar and when a **Welcome to Microsoft Edge** windows is displayed, select **Start without your data**, select **Continue without this data** again and select **Confirm and start browsing**.

1. If the welcome message is missing, navigate to https://microsoft.com/edge, select **DOWNLOAD for Windows** and **Windows 10**. Select **Accept and download** and **Run** to install the latest version of the Edge browser. Once this is complete perform the previous step.

1. In **Microsoft Edge**, select the address bar, navigate to **https://admin.microsoft.com** and log into the Microsoft 365 admin center as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **No**.

1. Close the password save dialog from the bottom by selecting **Never**, to not save the default global admins credentials in your browser.

1. If a welcome screen is displayed, close it. If the Office 365 apps notification appears, also close it.

1. If a welcome window is displayed, select Get started and close it.

1. In the left navigation pane, expand **Users** and then select **Active users**.

1. In the **Active users** list, search and select **Joni Sherman**, to open the right-side settings pane.

1.	In the settings below the **Account** tab, scroll to **Roles** and select **Manage roles** below.

1. When the **Manage admin roles** pane opens, select **Admin center access**, select **Show all by category** and scroll down to the **Security & Compliance** category and select **Compliance Administrator** .

1.	Select **Save changes** to apply the role. When the **Admin roles updated** message is displayed on the upper part of the pane, select the arrow pointing to the left to return to Joni's user record.

1. Close the pane displaying Joni Sherman’s account with the **X** in the upper right to go back to the **Active users** list.

1. Before switching to Joni Sherman, use the Global Admin privileges of MOD Administrator for activating the audit logging by navigating to https://compliance.microsoft.com/auditlogsearch.

1. On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.

1. In the **compliance** window, select **Yes** to update the organization settings.

1. Select the circle with **MA** in the upper right and select **Sign out**.

1. Close the **Microsoft Edge** browser window.

You have successfully assigned Joni Sherman the Compliance Administrator role, which is required to perform the different exercises of this lab. Continue with the next task.

### Task 2 – Explore the Microsoft Purview portal

In this task, you will sign out of the global admin account and sign-in again as Joni Sherman. Now that Joni Sherman was just assigned the Compliance admin role, her account will be sufficient for most of this lab's exercises.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account. 

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com**.

1. When the **Pick an account** window is displayed, select **Use another account**.

1. When the **Sign in** window is displayed, sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.  Hint: The password is probably the same as the MOD Administrator used earlier.

1. If the **Improve your compliance posture** message window opens, read the text and select **Next** twice and then select **Done**. 

    [//]: <> ("Improve your compliance posture" did not show uo in any test scenario. Remove the last step?)

1. The page **Welcome to the Microsoft Purview compliance portal** is displayed. Investigate the dashboard tiles and the left-side navigation pane.

1. Get yourself familiar with the different settings. When you are done, leave the browser window open.

You have successfully switched to Joni Sherman's account and you are now ready to start with the lab.

---

| [Lab Exercise List](../../../../) | [Proceed to Lab 1 - Exercise 2](LAB_AK_01_Lab1_Ex2_message_encryption.md) |
| :-----------: | :-----------: |
