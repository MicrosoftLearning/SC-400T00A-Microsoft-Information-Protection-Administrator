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

If you encounter any issues with these labs, please reach out to me at richelle.swinton@microsoft.com to resolve these issues.

## Task 1 – Enable Audit in Microsoft Purview

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account. The password should be provided by your lab hosting provider.

1. Open **Microsoft Edge** and navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. A message about the new Microsoft Purview portal will appear on the screen. Select the option to agree with the terms of data flow disclosure and the privacy statement, then select **Try now**.

    ![Screenshot showing the Welcome to the new Microsoft Purview portal screen.](/Instructions/Media/welcome-purview-portal.png)

1. Select **Solutions** from the left sidebar, then select **Audit**.

1. On the **Search** page, select the **Start recording user and admin activity** bar to enable audit logging.

    ![Screenshot showing the Start recording user and admin activity button.](/Instructions/Media/enable-audit-button.png)

1. Once you select this option, the blue bar should disappear from this page.

You have successfully enabled auditing in Microsoft 365.

## Task 2 – Onboard a device for Endpoint DLP

In this task, you'll enable device onboarding for your organization.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account logged. You should also still be logged into Microsoft Purview as the MOD Administrator.

1. In the Microsoft Purview portal, select **Settings** from the left sidebar. Expand **Device onboarding** then select **Devices**.

1. On the **Devices** page, select **Turn on device onboarding** to enable the solution for your tenant.

1. Accept the **Turn on device onboarding** dialog by selecting **OK**.

1. Accept the **Device monitoring is being turned on** dialog by selecting **OK**.

You have now enabled device onboarding and can start to onboard devices to be protected with Endpoint DLP policies. The process of enabling the feature might take up to 30 minutes, but you can move on with the next task as it's not dependent on this.

## Task 3 – Onboard a device to endpoint DLP

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
