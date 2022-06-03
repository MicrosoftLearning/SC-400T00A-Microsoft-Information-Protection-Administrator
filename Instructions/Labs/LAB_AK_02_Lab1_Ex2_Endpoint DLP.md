# Lab 2 - Exercise 2 - Manage Endpoint DLP

You are Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. For this reason, you decide to not only implement Microsoft 365 DLP policies, but extend this protection to devices in your organization.

### Task 1 – Enable device onboarding

In this task, you will turn on device onboarding for your organization. 

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal in the left navigation pane, select **Settings** and select **Device onboarding**.

1. Select **Turn on device onboarding**.

1. Accept the **Turn on device onboarding** dialog by selecting **OK**.

1. Accept the **Device monitoring is being turned on** dialog by selecting **OK**.

You have now enabled device onboarding and can start to onboard Windows 10 devices to be protected with Endpoint DLP policies. The process of enabling the feature may take up to 30 minutes, but you may proceed with the next task as it's not dependant on this.

### Task 2 - Onboard a device to Endpoint DLP

In this task, you will use the local script option to onboard a Windows 10 device to allow it to be protected by Endpoint DLP policies.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and you should be logged into Microsoft 365 as **Joni Sherman**..

1. In the **Microsoft Purview** portal on the left navigation pane, select **Settings** and select **device onboarding**.

1. On the **Device onboarding** page, in the navigation pane, select **Onboarding**.

1. In the **Deployment method** dropdown menu, select **Local Script (For up to 10 machines)** and select **Download package**.

1. In the download dialog, select **Save**, then select **Open folder**.

1. Extract the Zip-file to the **Desktop** of LON-CL1. You should see a script named **DeviceComplianceLocalOnboardingScript.cmd**.

1. On the desktop right-click the **DeviceComplianceLocalOnboardingScript.cmd** file you just extracted, and select **Run as administrator**.  You might encounter a Windows SmartScreen warning box, if you do choose **more info** and then choose **Run anyway**.  If you encounter the User Account Control window select **Yes** to all this script to make changes to your PC.

1. In the **Command Prompt** screen type **Y** to confirm, and then press Enter.

1. When the script completes **Press any key to continue**.  It can take a minute to complete the onboarding.

1. Open the start menu then find and select **Access work or school**.

1. In the **Access work or school** window, select **+ Connect**.

1. In the **Set up a work or school account** dialog, select the **Join this device to Azure Active Directory** link and sign in as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In the **Make sure this is your organization** dialog, review the tenant url and select **Join**.  If your device fails to join you may need to troubleshoot your Azure AD configuration join settings. Do the following to ensure devices may be joined:
        1. Open a new browser tab and go to the Azure Portal https://portal.azure.com
        1. Sign in as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com
        1. Select **Manage Azure Active Directory**.
        1. Select **Devices**
        1. Select **Device settings**
        1. Scroll-down until you see **Maximum number of devices per user** change the value to **20 (Recommended)**
        1. Once you have updated the setting re-try to connect your device.

1. Once your device has connected select **Done**.

1. Restart the Client 1 VM (LON-CL1).

You have successfully onboarded a device and joined it to Azure AD to be protected by Endpoint DLP policies.

### Task 3 - Create and Endpoint DLP policy

In this task, you will create a Data Loss Prevention policy in the Microsoft Purview portal to protect sensitive data residing on Windows 10 devices in your organization. The DLP Policy that you create will block your users if they want to copy content from documents that contain Credit Card information.

1. Log on to your Client 1 VM (LON-CL1) as the lon-cl1\admin account.

1. In Microsoft Edge, navigate to https://compliance.microsoft.com.

3. When the Sign in window is displayed, sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider. Hint: The password is probably the same as the MOD Administrator used earlier. 

1. In the **Microsoft Purview** portal on the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

1. In the **Data loss prevention** window select the **Policies** tab, and then select **+Create policy** to start the wizard for creating a new data loss prevention policy.

1. On the **Start with a template or create a custom policy** page, you want to select **Custom** in the left pane and **Custom policy** in the middle pane; however, by default, both these options should already be selected (if not, then select them now), select **Next**.

1. In the **Name your DLP policy** page, type *Credit Card Endpoint DLP Policy* in the **Name** field and *Protect credit card numbers from being shared on endpoints.* in the **Description** field. Select **Next**.

1. On the **Choose locations to apply the policy** page, select only the **Devices** option and then select **Next**.

1. On the **Define policy settings** page, the option **Create or customize advanced DLP rules** needs to be selected, which it should be by default. Select **Next**.

1. On the **Customize advanced DLP rules** page, select **+ Create rule**.

1. On the **Create rule** page, type *Endpoint Credit Card information* in the **Name** field.

1. Select **+ Add condition** and then select **Content contains** from the dropdown menu.

1. On the **Create rule** page, in the new **Content contains** area, select **Add** and select **sensitive info types** from the dropdown menu.

1. On the **Sensitive info types** page, select **Credit Card Number** and select **Add**.

1. On the **Create rule** page, select **+ Add an action** drop-down and select **Audit or restrict activities on Windows devices**.

1. Uncheck every checkbox except **Copy to Clipboard**.

1. In the dropdown menu behind **Copy to Clipboard** select **Block**.

1. On the **Create rule** page, in the **User Notifications** section, select the switch to put it in the **On** position.

1. In the **Incident reports** section, in the **Use this severity in admin alerts and reports** dropdown, select **Low**.

1. In the **Incident reports** section, select the **Send an alert to admins when a rule match occurs.** switch to put it in the **On** position and review the options. The default settings will notify the user creating the policy.

1. Select **Save**, then select **Next**.

1. On the **Test or turn on the policy** page select **Turn it on right away**.

1. Select **Next** and review the policy configuration.

1. Select **Submit** to create the policy.

1. Once the policy is created select **Done**.

You have successfully activated the DLP Policy. If the policy detects an attempt to copy content from a file containing credit card information, it will now block the attempt and inform your user.

### Task 4 - Configure Endpoint DLP Settings

In this task, you will configure a file path exclusion to a folder on your Windows 10 devices to make sure that the content of this folder is not monitored by the Endpoint DLP policy you created.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

1. In the **Data loss prevention** window, select the **Endpoint DLP settings** tab.

1. In the **Endpoint DLP settings** tab, expand the **File path exclusions for Windows** area and select **+ Add file path exclusion**.

1. In the **Enter a path to exclude** field, type *C:\FilePathExclusionTest*, then select **+**.

1. Select **Add**.

You have now configured a general exception to your Endpoint DLP policies. Every policy you create will ignore content in the folder you configured.

# Proceed to Lab 2 - Exercise 3 
