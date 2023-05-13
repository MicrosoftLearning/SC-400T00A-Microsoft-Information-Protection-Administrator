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

In this lab you'll configure and prepare your environment for administration tasks. By following the provided steps, you'll ensure that essential features and settings are enabled in advance, allowing for an easier learning experience in upcoming lab activities. This preparation will include activating necessary features, setting up administrative permissions, and ensuring the proper configuration of key elements. Completing this lab setup will provide you with a solid foundation for effectively administering and managing your environment throughout the rest of the lab modules.

## Task - Enable Audit in the Microsoft Purview portal

In task, we'll focus on enabling Audit in the Microsoft Purview compliance portal. Enabling audit allows you to track and monitor activities within the portal, ensuring visibility and accountability. By following the provided steps, we will configure and activate the audit feature in advance, providing a comprehensive audit trail for the subsequent lab activities

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as the MOD Administrator, admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the left navigation pane select **Audit**

1. On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.

## Task - Enable Search by Name in Microsoft Teams

In this task, we'll enable the **Search by Name** feature in Microsoft Teams as part of the lab setup. This feature allows users to easily find and connect with specific individuals within their organization. By following the steps provided, we will configure and activate the **Search by Name** feature ahead of time, ensuring that it is readily available for users when working with Information Barriers.

1. In **Microsoft Edge**, navigate to **https://admin.teams.microsoft.com** and log into the Microsoft Purview portal as the MOD Administrator, admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). The admin's password should be provided by your lab hosting provider.

1. In the left navigation pane, under the **Teams** drop down, select **Teams settings**

1. Scroll down to **Search by name** toggle this feature **On** to enable this feature

1. Select **Save** to save this setting


## Task - Enable information barriers in SharePoint Online and OneDrive

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

1. Confirm the **User Account Control** window with **Yes**.

1. Enter the following cmdlet to install the latest version of the Sharepoint Online PowerShell module:

    ```powershell
    Install-Module Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. Enter the following cmdlet to connect to the admin center for SharePoint online **Enter**

    ```powershell
     Connect-SPOService -Url https://WWLxZZZZZZ-admin.sharepoint.com -Credential admin@WWLxZZZZZZ.onmicrosoft.com
    ```

    >**Note:** Be sure to update where ZZZZZZ. ZZZZZZ is your unique tenant ID provided by your lab hosting provider.

1. Login with the MOD Administrator password provided by your lab hosting provider

1. To enable information barriers in SharePoint and OneDrive, run the following command:

    ```powershell
    Set-SPOTenant -InformationBarriersSuspension $false
    ```
