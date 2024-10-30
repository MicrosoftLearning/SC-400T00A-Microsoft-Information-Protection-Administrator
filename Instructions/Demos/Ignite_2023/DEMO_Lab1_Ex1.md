---
lab:
    title: 'Exercise 1 - Manage Compliance Roles'
    module: 'Module 1 - Implement Information Protection'
---
# Exercise 1 - Manage Compliance Roles

As the recently hired Compliance Administrator for Contoso Ltd. in the role of Joni Sherman, your responsibility is to configure your organization's new Microsoft 365 tenant to meet its compliance requirements. Contoso Ltd. is a company headquartered in the United States with new subsidiaries in the European Union, and it is essential for your organization to ensure that the new Microsoft 365 tenant complies with legal requirements in different countries and regulatory standards in your industry sector.

## Task 1 – Assign Compliance Roles

In this exercise, you will follow the principal of least privilege and use the default Global Administrator to assign the Compliance Admin role to Joni Sherman, which is required to perform the operations described in this lab.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account. The password should be provided by your lab hosting provider.

1. Open **Microsoft Edge**, select the address bar, navigate to **https://admin.microsoft.com** and log into the Microsoft 365 admin center as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com. Admin's password should be provided by your lab hosting provider.

1. On the **Things have moved** dialogue, select **Next** until the dialogue box closes.

1. In the left navigation pane, expand **Users** then select **Active users**.

1. In the **Active users** list select **Joni Sherman**. This will open a flyout page to the right with Joni's user settings.

1. On Joni's user settings page, below the **Account** tab, scroll to **Roles** then select **Manage roles**.

      ![Screenshot of Manage roles option](../Media/ManageRoles.png)

1. On the **Manage admin roles** flyout page, select **Admin center access** then scroll down to select **Show all by category**. Under the category view in the **Security & Compliance** category select **Compliance Administrator**.

1. Select **Save changes** to apply the role. When the **Admin roles updated** message is displayed on the upper part of the page, select the arrow pointing to the left to return to Joni's user settings.

1. Close the flyout page displaying Joni Sherman’s account with the **X** in the upper right to go back to the **Active users** list.

1. Before switching to Joni Sherman, use the Global Admin privileges of MOD Administrator for activating the audit logging by navigating to https://compliance.microsoft.com/auditlogsearch.

1. On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.

1. Select the circle with **MA** in the upper right and select **Sign out**.

1. Close the **Microsoft Edge** browser window.

You have successfully assigned Joni Sherman the Compliance Administrator role, which is required to perform the different exercises of this lab. Continue with the next task.

## Task 2 – Explore the Microsoft Purview portal

In this task, you will sign out of the global admin account and sign-in again as Joni Sherman. Now that Joni Sherman was just assigned the Compliance admin role, her account will be sufficient for most of this lab's exercises.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com**.

1. When the **Pick an account** window is displayed, select **Use another account**.

1. When the **Sign in** window is displayed, sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com. Joni's password should be provided by your lab hosting provider.

1. The page **Welcome to the Microsoft Purview compliance portal** is displayed. Explore the dashboard tiles and the left-side navigation pane.

1. Get yourself familiar with the different settings. When you are done, leave the browser window open.

You have successfully switched to Joni Sherman's account and you are now ready to start with the lab.
