---
lab:
    title: 'Lab Setup: Preparing Your Environment for Administration'
    module: 'Module 0 - Lab Setup'
---

## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab Setup: Preparing Your Environment for Administration

In this lab you'll configure and prepare your environment for administration tasks. By following the provided steps, you'll ensure that essential features and settings are enabled in advance, allowing for an easier learning experience in upcoming lab activities. This preparation will include activating necessary features, setting up administrative permissions, and ensuring the proper configuration of key elements.

## Task - Set user passwords for lab exercises

In this task, you'll set passwords for the user accounts needed for the labs.

1. Log into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account. The password should be provided by your lab hosting provider.

1. In **Microsoft Edge**, navigate to **https://admin.microsoft.com** and log into the Microsoft Purview portal as the MOD Administrator, admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. On the left navigation pane, expand **Users** then select **Active users**.

1. Select the check box next to **Display name** to select all users.

1. Deselect the check boxes next to **MOD Administrator** and **Microsoft Service Account**.

    >[!alert] Do not change the **MOD Administrator** or **Microsoft Service Account** passwords. This will negatively impact your lab experience.
    ><p>
    > ![Screenshot displaying Microsoft Service Account and MOD Administrator deselected.](../Media/deselectserviceaccounts.png)

1. Select the **Reset password** from the middle action ribbon to open the **Reset password** flyout page on the right.

1. Deselect the options for **Automatically create a password** and **Require these users to change their password when they first sign in**. No options should be selected on the Reset password page.

1. Ensure none of the checkboxes are selected on the **Reset password** flyout page. In the Password field, enter a password you can remember to reset all user passwords available in the tenant.

   >[Note] You can reset the password to the same password as the admin's account, which should be provided by your lab hosting provider. Setting all user passwords to the same password is not advised in a real world scenario. This can be help for the purpose of this lab.

1. Select the **Reset password** button to reset all user passwords, except for the **MOD Administrator** and **Microsoft Service Account**.

1. On the **Passwords have been reset** page, select the **Close** button to go back to the **Active users** page.

## Task - Enable Audit in the Microsoft Purview portal

In this task, you'll enable Audit in the Microsoft Purview compliance portal. This tracking feature ensures visibility and accountability by monitoring portal activities.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account and logged into Microsoft 365 with the MOD Administrator account.

1. In **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`**.

1. In the left navigation pane select **Audit**.

1. On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.

## Task - Enable Search by Name in Microsoft Teams

In this task, you'll enable the **Search by Name** feature in Microsoft Teams for the lab setup. This allows easy user location and connection within the organization. Follow the steps to activate it beforehand, ensuring availability when working with Information Barriers.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account and logged into Microsoft 365 with the MOD Administrator account.

1. In **Microsoft Edge**, navigate to **`https://admin.teams.microsoft.com`**.

1. In the left navigation pane, under the **Teams** drop down, select **Teams settings**.

1. Scroll down to **Search by name** toggle this feature **On** to enable this feature

1. Select **Save** to save this setting.

## Task - Enable information barriers in SharePoint Online and OneDrive

In this task, you'll enable information barriers in SharePoint Online and OneDrive to promote secure collaboration and prevent unauthorized communication.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

1. Confirm the **User Account Control** window with **Yes**.

1. Run the following cmdlet to install the latest version of the SharePoint Online PowerShell module:

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. If prompted to install the PowerShell NuGet provider, enter **Y** to install the provider.

1. If prompted to install from an untrusted repository, enter **Y** to install the module from the PSGallery.

1. Run the following cmdlet to connect to the admin center for SharePoint Online:

    ```powershell
     Connect-SPOService -Url https://WWLxZZZZZZ-admin.sharepoint.com -Credential admin@WWLxZZZZZZ.onmicrosoft.com
    ```

    >**Note:** Be sure to update ZZZZZZ. ZZZZZZ is your unique tenant ID provided by your lab hosting provider.

1. Login with the MOD Administrator password provided by your lab hosting provider.

1. To enable information barriers in SharePoint and OneDrive, run the following command:

    ```powershell
    Set-SPOTenant -InformationBarriersSuspension $false
    ```

1. Close the PowerShell window once this is complete.
