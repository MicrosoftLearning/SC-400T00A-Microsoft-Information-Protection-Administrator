---
lab:
    title: 'Exercise 1 - Manage Compliance Roles'
    module: 'Module 1 - Implement Information Protection'
---
## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab 1 - Exercise 1 - Manage compliance roles

As the recently hired Compliance Administrator for Contoso Ltd., you (Joni Sherman) need to ensure the new Microsoft 365 tenant complies with various legal and regulatory standards. Contoso Ltd. is expanding, and your role is crucial in maintaining compliance across different regions.

**Tasks**:

1. Assign compliance roles
1. Explore the Microsoft Purview portal

## Task 1 – Assign compliance roles

In this task, you'll assign the Compliance Admin role to Joni Sherman.

1. Log into the Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account. The password should be provided by your lab hosting provider.

1. Open **Microsoft Edge** and navigate to the Microsoft 365 admin center, `https://admin.microsoft.com`, and log in as **MOD Administrator**, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. On the left sidebar, expand **Users** then select **Active users**.

1. On the **Active users** page, search for `Joni`, then select **Joni Sherman**.

1. The properties for Joni's account is displayed in a right, flyout panel. Select **Manage roles** on the flyout panel.

1. On the **Manage admin roles** panel, select the option for **Admin center access**, then scroll down to expand **Show all by category**.

1. Under the **Security & Compliance** category, select the checkbox for **Compliance Administrator**, then select **Save changes** at the bottom of the flyout panel.

1. You should receive a message stating **Admin roles updated**.

1. On the **Manage admin roles** page, select the **X** on the top right corner of the flyout panel to close the panel.

1. Sign out of the MOD Administrator account by selecting the **MA** icon in the top right, then select **Sign out**.

   ![Screenshot showing the navigation path to sign out of the MOD Administrator account.](../Media/sign-out.png)

You have successfully assigned Joni Sherman the Compliance Administrator role, which is required to perform the different exercises of this lab.

## Task 2 – Explore the Microsoft Purview portal

In this task, you'll sign in as Joni Sherman to explore the Microsoft Purview portal.

1. You should still be logged into your Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`**.

1. When the **Pick an account** window is displayed, select **Use another account**.

1. When the **Sign in** window is displayed, sign in as `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in a previous exercise.

1. Get yourself familiar with the new Microsoft Purview Portal. When you are done, leave the browser window open.

You have successfully switched to Joni Sherman's account and are now ready to start the lab.
