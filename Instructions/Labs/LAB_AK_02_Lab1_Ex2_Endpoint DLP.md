# Exercise 2 - Manage Endpoint DLP

You are Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. For this reason, you decide to not only implement Microsoft 365 DLP policies but extend this protection to devices in your organization.

### Task 1 – Enable device onboarding

In this exercise, you will turn on device onboarding for your organization. 

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center** in the left navigation pane, select **Settings** and select **device onboarding**.

4. Select **Turn on device onboarding**.

5. Accept the **Turn on device onboarding** dialog by selecting **OK**.

6. Accept the **Device monitoring is being turned on** dialog by selecting **OK**.

You have now enabled device onboarding and can start to onboard Windows 10 devices to be protected with Endpoint DLP policies. The process of enabling the feature may take up to 30 minutes.

### Task 2 - Onboard a device to Endpoint DLP

In this exercise, you will use the local script option to onboard a Windows 10 device to allow it to be protected by Endpoint DLP policies.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **MOD Administrator**.

3. In the **Compliance Center** in the left navigation pane, select **Settings** and select **device onboarding**.

4. On the **Device onboarding** page, in the navigation pane, select **Onboarding**.

5. In the **Deployment Method** dropdown menu, select **Local Script (For up to 10 machines)** and select **Download package**.

6. In the download dialog, select **Save**, then select **Open folder**.

7. Extract the ZIP-file to the **Desktop**. You should see a script named **DeviceComplianceLocalOnboardingScript.cmd**.

8. In the start menu, search for **Command Prompt** and select **Run as Administrator**.

9. In the **Command Prompt**, run the script by typing **%userprofile%\Desktop\DeviceComplianceLocalOnboardingScript.cmd**, then select **Y** to confirm.

10. When the script completes **Press any key to continue**.

7. Open the start menu and select **Access work or school**.

8. In the **Access work or school** window, select **+ Connect**.

9. In the **Set up a work or school account** dialog, select the **Join this device to Azure Active Directory** link and sign in as **Joni Sherman**.

10. In the **Make sure this is your organization** dialog, review the tenant url and select **Join**.

11. Select **Done**.

12. Restart the Client 1 VM (LON-CL1).

You have successfully onboarded a device and joined it to Azure AD to be protected by Endpoint DLP policies.

### Task 3 - Create Endpoint DLP policy

In this exercise, you will create a Data Loss Prevention policy in the Compliance Center to protect sensitive data residing on Windows 10 devices in your organization. The DLP Policy that you create will block your users if they want to copy content from documents that contain Credit Card information.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

4. In the **Data loss prevention** window, select **+Create policy** to start the wizard for creating a new data loss prevention policy.

5. On the **Start with a template or create a custom policy** page, you want to select **Custom** in the left pane and **Custom policy** in the middle pane; however, by default, both these options should already be selected (if not, then select them now), select **Next**.

6. In the **Name your DLP policy** page, type **Credit Card Endpoint DLP Policy** in the **Name** field and **Protect credit card numbers from being shared on Endpoints.** in the **Description** field. Select **Next**.

7. On the **Choose locations to apply the policy** page, select only the **Devices** option and then select **Next**.

8. On the **Define policy settings** page, the option **Create or customize advanced DLP rules** needs to be selected, which it should be by default. Select **Next**.

9. On the **Customize advanced DLP rules** page, select **+ Create rule**.

10. On the **Create rule** page, type **Endpoint Credit Card information**.

11. Select **+ Add Condition** and then select **Content contains** from the dropdown menu.

12. On the **Create rule** page, in the new **Content contains** area, select **Add** and select **sensitive info types** from the dropdown menu.

13. On the **Sensitive info types** page, select **Credit card number** and select **Add**.

14. On the **Create rule** page, select **+ Add an action** and select **Audit or restrict activities on Windows devices**.

15. Uncheck every checkbox except **Copy to Clipboard**.

16. In the dropdown menu behind **Copy to Clipboard** select **Block**.

16. On the **Create rule** page, in the **User Notifications** section, select the switch to put it in the **On** position.

18. In the **Incident reports** section, in the **Use this severity in admin alerts and reports** dropdown, select **Low**.

19. In the **Incident reports** section, select the **Send an alert to admins when a rule match occurs.** switch to put it in the **On** position and review the options. The default settings will notify the user creating the policy.

20. Select **Save**, then select **Next**.

21. On the **Test or turn on the policy** page select **Yes, turn it on right away**.

22. Select **Next** and review the policy configuration.

23. Select **Submit** to create the policy.

You have successfully activated the DLP Policy. If the policy detects an attempt to copy content from a file containing credit card information, it will now block the attempt and inform your user.

### Task 4 - Configure Endpoint DLP Settings

In this exercise, you will configure a file path exclusion to a folder on your Windows 10 devices to make sure that the content of this folder is not monitored by the Endpoint DLP policy you created.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

4. In the **Data loss prevention** window, select the **Endpoint DLP settings** tab.

5. In the **Endpoint DLP settings** tab, expand the **file path exclusions** area and select **+ Add file path exclusion**.

6. In the **Enter a path to exclude** field, type **C:\FilePathExclusionTest**, then select **+**.

7. Select **Add**.

You have now configured a general exception to your Endpoint DLP policies. Every policy you create will ignore content in the folder you configured.

# Proceed to Exercise 3 