---
lab:
    title: 'Demo Setup: Preparing Your Environment for Administration'
    module: 'Module 0 - Lab Setup'
---

## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab Setup: Preparing Your Environment for Administration

In this lab you'll configure and prepare your environment for administration tasks. By following the provided steps, you'll ensure that essential features and settings are enabled in advance, allowing for an easier learning experience in upcoming lab activities. This preparation will include activating necessary features, setting up administrative permissions, and ensuring the proper configuration of key elements.

## Task - Enable Audit in the Microsoft Purview portal

In this task, you'll enable Audit in the Microsoft Purview compliance portal. This tracking feature ensures visibility and accountability by monitoring portal activities.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account and logged into Microsoft 365 with the MOD Administrator account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com**.

1. In the left navigation pane select **Audit**.

1. On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.

## Task - Enable support for sensitivity labels

In this task, you will install the MSOnline module and the SharePoint Online PowerShell module and enable support for sensitivity labels on your tenant.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the start menu with the right mouse button and then select **Windows PowerShell** and run as administrator.

1. Confirm the **User Account Control** window with **Yes** and press Enter.

1. Enter the following cmdlet to install the latest MS Online PowerShell module version:

   ```powershell
   Install-Module -Name MSOnline
   ```

1. Confirm the Nuget security dialog and the Untrusted repository security dialog with **Y** for Yes and press Enter.  This may take a while to complete processing.

1. Enter the following cmdlet to install the latest SharePoint Online PowerShell module version:

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. Confirm the Untrusted repository security dialog with **Y** for Yes and press Enter.

1. Enter the following cmdlet to connect to the MS Online service:

    ```powershell
    Connect-MsolService
    ```

1. In the **Sign into your account** form, sign in as **MOD Admin** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. After signing in, select the PowerShell window.

1. Enter the following cmdlet to get the domain:

    ```powershell
    $domain = get-msoldomain
    ```

1. Enter the following cmdlet to create the SharePoint admin url:

    ```powershell
    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"
    ```

1. Enter the following cmdlet to sign in to the SharePoint Online admin center:

    ```powershell
    Connect-SPOService -url $adminurl
    ```

1. In the **Sign into your account** form, sign in as **MOD Administrator**. admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

1. After signing in, select the PowerShell window.

1. Enter the following cmdlet to enable support for sensitivity labels:

    ```powershell
    Set-SPOTenant -EnableAIPIntegration $true
    ```

1. Confirm the changes with **Y** for Yes and press Enter.

1. Close the PowerShell window.

You have successfully enabled support for sensitivity labels with Teams and SharePoint sites.