---
lab:
    title: 'Demo setup'
    module: 'FY25 VTD Demo - Setup'
---

# Demo Lab 0 - VTD Demo Setup

This lab is to setup the demo environment for the FY25 VTDs. The primary tasks in these labs are to:

- Enable Audit in Microsoft Purview for Insider Risk Management
- Onboard devices for endpoint DLP, Insider Risk Management, Adaptive Protection, and AI Hub.

Please ensure you perform these tasks before running the demos for VTDs 48 hours in advance to ensure the environment is ready for demos.

## Task 1 – Set user passwords demo walkthrough

In this task, you'll set passwords for the user accounts needed for the labs.

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account. The password should be provided by your lab hosting provider.

1. Open **Microsoft Edge** and navigate to **`https://admin.microsoft.com`** and log into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. On the left navigation pane, expand **Users** then select **Active users**.

1. Select the checkbox to the left of **Joni Sherman**.

   This accounts will be in demo walkthroughs.

1. Select the **Reset password** button from the top, navigation ribbon to reset Joni's password.

   ![Screenshot showing the Reset password button in the Microsoft 365 admin center.](/Instructions/Media/reset-password-button.png)

1. In the **Reset Password** flyout page on the right, ensure all options are deselected.

   This will ensure that you can select a password for Joni for the demo walkthroughs, and this passwords won't need to be reset when you first sign in.

1. In the **Password** field, enter a password you can remember to reset the user passwords to be used in future exercises.

1. At the bottom of the **Reset password** flyout page, select the **Reset password** button.

1. On the **Passwords have been reset** page, you should see the three user accounts that have been reset. At the bottom of this flyout page, select **Close**.

You have successfully reset passwords for lab exercises.

## Task 2 – Enable Audit in Microsoft Purview

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account. The password should be provided by your lab hosting provider.

1. Open **Microsoft Edge** and navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. A message about the new Microsoft Purview portal will appear on the screen. Select the option to agree with the terms of data flow disclosure and the privacy statement, then select **Try now**.

    ![Screenshot showing the Welcome to the new Microsoft Purview portal screen.](/Instructions/Media/welcome-purview-portal.png)

1. Select **Solutions** from the left sidebar, then select **Audit**.

1. On the **Search** page, select the **Start recording user and admin activity** bar to enable audit logging.

    ![Screenshot showing the Start recording user and admin activity button.](/Instructions/Media/enable-audit-button.png)

1. Once you select this option, the blue bar should disappear from this page.

You have successfully enabled auditing in Microsoft 365.

## Task 3 – Onboard a device for Endpoint DLP

In this task, you'll enable device onboarding for your organization.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin**.

    You should also still be logged into Microsoft Purview as the MOD Administrator.

1. In the Microsoft Purview portal, select **Settings** from the left sidebar. Expand **Device onboarding** then select **Devices**.

1. On the **Devices** page, select **Turn on device onboarding** to enable the solution for your tenant.

1. Accept the **Turn on device onboarding** dialog by selecting **OK**.

1. Accept the **Device monitoring is being turned on** dialog by selecting **OK**.

You have now enabled device onboarding and can start to onboard devices to be protected with Endpoint DLP policies. The process of enabling the feature might take up to 30 minutes.

## Task 4 – Onboard a device to endpoint DLP

In this task, you'll use the local script option to onboard a Windows 11 device to allow it to be protected by Endpoint DLP policies.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account logged.

   You should also still be logged into Microsoft Purview as the MOD Administrator.

   You should also still be on the **Devices** page for endpoint DLP.

1. In the Microsoft Purview portal, from the **Devices** page, ensure **Device onboarding** is expanded, then select **Onboarding**.

1. On the **Device onboarding** page, in the navigation pane, select **Onboarding**.

1. In the **Deployment method** dropdown menu, select **Local Script (for up to 10 machines)** and select **Download package**.

1. In the **Downloads** dialog, hover over the download, then select the folder icon to **Show in folder**.

1. Extract the zip-file to the **Desktop** of SC-400-CL1. You should see a script named **DeviceComplianceLocalOnboardingScript.cmd**.

1. On the desktop right click the **DeviceComplianceLocalOnboardingScript.cmd** file you just extracted and select **Show more options**, then select **Properties**.

1. Towards the bottom of the **General** tab of the properties window, in the **Security** section, select **Unblock**, then select **OK** to save this setting.

1. Back on the desktop, right click **DeviceComplianceLocalOnboardingScript.cmd**, then select **Run as administrator**. On the **User Account Control** dialogue, select **Yes**.

1. In the **Command Prompt** screen type **Y** to confirm, and then press Enter.

1. When the script is complete, you'll get a success message and a prompt to **Press any key to continue**. Press any key to close the command line window. It can take a minute to complete the onboarding.

1. Open the start menu and search for `Access work or school`. Select **Access work or school** under **Best match**.

1. In the **Access work or school** window for **Add a work or school account** select **Connect**.

1. In the **Set up a work or school account** dialog, select the **Join this device to Microsoft Entra ID** link and sign in as **MOD Administrator** `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the **Make sure this is your organization** dialog, review the tenant URL and select **Join**.  

1. Once your device has connected select **Done** on the **You're all set!** screen.

1. Restart Client 1 VM (SC-400-CL1).

1. Once Client 1 VM is available, log back into Client 1 VM (SC-400-CL1).

1. Open Microsoft Edge and navigate back to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the Microsoft Purview portal, navigate to **Settings** > **Device onboarding** > **Devices** and verify the device has been successfully onboarded.

You have successfully onboarded a device and joined it to Microsoft Entra ID to be protected by endpoint DLP policies.

## Task 5 – Enable support for sensitivity labels

In this task, you'll install the necessary modules and enable support for sensitivity labels on your tenant.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**.

1. Confirm the **User Account Control** window with **Yes** and press Enter.

1. Run the **Install-Module** cmdlet to install the latest MS Online PowerShell module version:

    ```powershell
    Install-Module -Name MSOnline
    ```

1. Confirm the Nuget security dialog and the Untrusted repository security dialog with **Y** for Yes and press Enter. This might take a while to complete processing.

1. Run the **Install-Module** cmdlet to install the latest SharePoint Online PowerShell module version:

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

1. Confirm the Untrusted repository security dialog with **Y** for Yes and press Enter.

1. Run the **Connect-MsolService** to connect to the MS Online service:

    ```powershell
    Connect-MsolService
    ```

1. In the **Sign into your account** form, sign in as **MOD Administrator** `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. After signing in, navigate back to the terminal window.

1. Run the **Get-Msoldomain** cmdlet and save the domain as a variable:

    ```powershell
    $domain = get-msoldomain
    ```

1. Use the _$domain_ variable created in the previous step to create a new variable for _$adminurl_:

    ```powershell
    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"
    ```

1. Run the **Connect-SPOService** cmdlet using the _$adminurl_ variable created in the previous step:

    ```powershell
    Connect-SPOService -url $adminurl
    ```

1. In the **Sign into your account** form, sign in as **MOD Administrator**. `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. After signing in, navigate back to the terminal window.

1. Run the **Set-SPOTenant** cmdlet to enable support for sensitivity labels:

    ```powershell
    Set-SPOTenant -EnableAIPIntegration $true
    ```

1. Confirm the changes with **Y** for Yes and press Enter.

1. Close the PowerShell window.

You have successfully enabled support for sensitivity labels for Teams and SharePoint sites.

## Task 6 – Turn on the ability to process content in Office online files that have encrypted sensitivity labels applied and are stored in OneDrive and SharePoint

1. Open **Microsoft Edge** and navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Solutoins** in the left sidebar, then select **Information Protection** > **Sensitivity labels**.

1. Select **Turn on now** in the yellow dialogue box that states **Your organization has not turned on the ability to process content in Office online files that have encrypted sensitivity labels applied and are stored in OneDrive and SharePoint. You can turn on here, but note that additional configuration is required for Multi-Geo environments.**

1. You should now see a message stating **You can now create sensitivity labels with privacy and access control settings for Teams, SharePoint sites, and Microsoft 365 Groups.**
