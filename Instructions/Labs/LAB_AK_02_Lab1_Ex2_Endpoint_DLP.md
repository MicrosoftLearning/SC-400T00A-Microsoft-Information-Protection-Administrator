---
lab:
    title: 'Exercise 2 - Manage Endpoint DLP'
    module: 'Module 2 - Implement Data Loss Prevention'
---

# Lab 2 - Exercise 2 - Manage Endpoint DLP

You are Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. For this reason, you decide to not only implement Microsoft 365 DLP policies but extend this protection to devices in your organization.

## Task 1 – Enable device onboarding

In this task, you will turn on device onboarding for your organization.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**. sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in a previous exercise.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`**, then select the **Settings** card.

1. In the left navigation pane, expand **Device onboarding** then select **Devices**.

1. On the **Devices** page, select **Turn on device onboarding** to enable the solution for your tenant.

1. Accept the **Turn on device onboarding** dialog by selecting **OK**.

1. Accept the **Device monitoring is being turned on** dialog by selecting **OK**.

You have now enabled device onboarding and can start to onboard devices to be protected with Endpoint DLP policies. The process of enabling the feature might take up to 30 minutes, but you can proceed with the next task as it's not dependent on this.

## Task 2 - Onboard a device to Endpoint DLP

In this task, you will use the local script option to onboard a Windows 10 device to allow it to be protected by Endpoint DLP policies.

1. Log into Client 2 VM (SC-400-CL2) as the **SC-400-cl1\admin** account.

1. In Microsoft Edge, you should still be at the **Devices** page in Microsoft Purview logged in as Joni Sherman. If not, navigate to **`https://purview.microsoft.com`** > **Settings** > **Device onboarding** > **Devices**.

1. On the left navigation pane, in the **Device onboarding** section, select **Onboarding**.

1. On the **Device onboarding** page, in the navigation pane, select **Onboarding**.

1. In the **Deployment method** dropdown menu, select **Local Script (for up to 10 machines)** and select **Download package**.

1. In the **Downloads** dialog, hover over the download, then select the folder icon to **Show in folder**.

1. Extract the zip-file to the **Desktop** of SC-400-CL1. You should see a script named **DeviceComplianceLocaSC-400boardingScript.cmd**.

1. On the desktop right-click the **DeviceComplianceLocaSC-400boardingScript.cmd** file you just extracted and select **Show more options**, then select **Properties**.

1. Towards the bottom of the **General** tab of the properties window, in the **Security** section, select **Unblock**, then select **OK** to save this setting.

1. Back on the desktop, right click **DeviceComplianceLocaSC-400boardingScript.cmd**, then select **Run as administrator**. On the **User Account Control** dialogue, select **Yes**.

1. In the **Command Prompt** screen type **Y** to confirm, and then press Enter.

1. When the script completes, you'll get a success message and a prompt to **Press any key to continue**. Press any key to close the command line window. It can take a minute to complete the onboarding.

1. Open the start menu and search for `Access work or school`. Select **Access work or school** under **Best match**.

1. In the **Access work or school** window, for **Add a work or school account** select **Connect**.

1. In the **Set up a work or school account** dialog, select the **Join this device to Microsoft Entra ID** link and sign in as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in a previous exercise.

1. In the **Make sure this is your organization** dialog, review the tenant URL and select **Join**.  

1. Once your device has connected select **Done** on the **You're all set!** screen.

1. Restart Client 2 VM (SC-400-CL2).

You have successfully onboarded a device and joined it to Microsoft Entra ID to be protected by endpoint DLP policies.

## Task 3 - Create an endpoint DLP policy

In this task, you will create a data loss prevention policy in the Microsoft Purview portal to protect sensitive data residing on Windows 10 devices in your organization. The DLP Policy that you create will block your users if they want to copy content from documents that contain credit card information.

1. Log on to Client 1 VM (SC-400-CL1) as the SC-400-cl1\admin account.

1. Open Microsoft Edge from the taskbar, navigate to the Microsoft Purview portal at `https://compliance.microsoft.com` and when the Sign in window is displayed, sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the **Microsoft Purview** portal on the left navigation pane, expand **Data loss prevention** the select **Policies**.

1. Select **+ Create policy** to start the wizard for creating a new data loss prevention policy.

1. On the **Start with a template or create a custom policy** page, select **Custom** and **Custom policy**, then select **Next**.

1. In the **Name your DLP policy** page, enter the following information:

    - **Name**: Employee Diseases Endpoint DLP Policy
    - **Description**: Protect employee ID numbers and diseases from being shared on endpoints.

1. On the **Assign admin units** page, select **Next**.

1. On the **Choose locations to apply the policy** page, select only the **Devices** option then select **Next**.

1. On the **Define policy settings** page, select **Create or customize advanced DLP rules** then select **Next**.

1. On the **Customize advanced DLP rules** page, select **+ Create rule**.

1. On the **Create rule** page, enter:

    - **Name**: Employee ID and disease rule
    - **Description**: Detect if employee IDs and diseases are shared in near range.

1. Under **Conditions** select **+ Add condition** then select **Content contains** from the dropdown menu.

1. In the newly opened **Content contains** area, select **Add** then select **Sensitive info types** from the dropdown menu.

1. In the right-side pane **Sensitive info types**, select **Contoso Employee IDs** and **Contoso Disease List** then select **Add**.

1. Change the **Group operator** dropdown from **Any of these** to **All of these** to make the policy detect information in proximity.

1. Scroll down to **Actions** and select the **+ Add an action** dropdown then select **Audit or restrict activities on devices**.

1. In the **Audit or restrict activities on devices** area, leave all default checkboxes enabled. In the **File activities for all apps** section, change all dropdown selections from **Audit only** to **Block with Override**.

1. In the **User Notifications** section, toggle the **Use notifications to inform your users and help educate them on the proper use of sensitive info.** switch to **On**.

1. Under **Endpoint devices** select the checkbox for **Show users a policy tip notification when an activity is restricted. This is turned on when you select Block for an activity in Windows. To turn off the notifications on Windows devices, disable the restrictions**.

1. Under **Microsoft 365 services** select the checkbox for **Notify users in Office 365 service with a policy tip**.

1. Select **Save**, then select **Next** on the **Customize advanced DLP rules** page.

1. On the **Policy mode** page select **Turn the policy on immediately** then select **Next**.

1. On the **Review and finish** page, review your policy settings then select **Submit** to create the policy.

1. Once the policy is created select **Done**.

You have successfully activated the DLP Policy. If the policy detects an attempt to copy content from a file containing credit card information, it will now block the attempt and inform your user.

## Task 4 - Configure Endpoint DLP Settings

In this task, you will configure a file path exclusion to a folder on your Windows 10 devices to make sure that the content of this folder is not monitored by the Endpoint DLP policy you created.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **`https://compliance.microsoft.com`**.

1. In the **Microsoft Purview** portal, on the left navigation pane, expand **Data loss prevention** then select **Overview**.

1. Select **Data loss prevention settings** on the top right of the Overview page.

1. On the **Endpoint DLP settings** page, expand **File path exclusions for Windows**  then select **+ Add file path exclusion**.

1. On the **Exclude these file paths from Windows devices** flyout page in the **File path exclusion** field, enter _C:\FilePathExclusionTest_ then select the **+** button to the right. Select **Save** to save this entry.

1. Back on the **Endpoint DLP settings** page, expand **Browser and domain restrictions to sensitive data** and select **+ Add or edit unallowed browsers**.

1. On the **Add unallowed browsers** flyout page select the checkbox left of **Google Chrome** and select **Save**.

1. Back on the **Endpoint DLP settings** page, select the dropdown to the left of **Service domains** and change it from **Off** to **Block**.

1. In the **Update cloud app mode** dialogue select **Yes** to activate the block mode.

1. Under **Service domains** select **+ Add cloud service domain**.

1. On the **Add cloud service domain** flyout page in the **Domain** field enter _dropbox.com_ then select the **+** to the right. Select **Save** to save this setting.

1. Close the browser window.

You have now configured custom settings for your Endpoint DLP policies. Every policy you create will ignore content in the folder you configured and the Google Chrome browser has been added as unallowed browser to handle sensitive data.

## Task 5 - Configure Microsoft Purview Extension

As Compliance Administrator you need to evaluate the new business requirement of rolling out the Chrome browser to several users for working with sensitive data. For this test, you will install the Google Chrome browser to Client 01 and then add the Purview Compliance Extension for Google manually from the Google web store.

1. Open the Edge browser from the task bar.

1. Navigate to the Google Chrome download at **`https://chrome.google.com`**.

1. Select **Download Chrome** and select **Open file** below **Downloads** and **ChromeSetup.exe**.

1. Select **Yes** in the **User Account Control** dialog to install the Chrome browser.

1. When the installation is finished and the **Welcome to Chrome** page is open, navigate to the Microsoft Purview Extension in the Chrome web store at:

   ` https://chrome.google.com/webstore/detail/microsoft-purview-extensi/echcggldkblhodogklpincgchnpgcdco`

1. Verify you are on the extension page of **Microsoft Purview Extension** and select **Add to Chrome**.

1. On the **Add "Microsoft Purview Extension"** window, select **Add extension**.

1. Close the notification window and navigate to **`chrome://extensions`**.

1. Validate the **Microsoft Purview Extension** is visible and activated.

You have successfully installed the Chrome browser and added the Microsoft Purview Extension to your client. The Chrome browser can now be used like the Edge browser to work with sensitive data and the previously configured Endpoint DLP policy also applies when using the Chrome browser.
