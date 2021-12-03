# Lab 2 - Exercise 1 - Manage DLP Policies

You are Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company that offers driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization.

### Task 1 – Create a DLP policy in test mode

In this exercise, you will create a Data Loss Prevention policy in the Compliance Center to protect sensitive data from being shared by users. The DLP Policy that you create will inform your users if they want to share content that contains Credit Card information and allow them to provide a justification for sending this information. The policy will be implemented in test mode because you do not want the block action to affect your users yet.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft 365 compliance portal as **Joni Sherman**. sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

3. In the **Microsoft 365 compliance** portal, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

4. In the **Data loss prevention** window select the **Policies** tab, and then select **+Create policy** to start the wizard for creating a new data loss prevention policy.

5. On the **Start with a template or create a custom policy** page, scroll dowb and you want to select **Custom** and **Custom policy** under the template however, by default, both these options should already be selected (if not, then select them now), select **Next**.

6. In the **Name your DLP policy** page, type *Credit Card DLP Policy* in the **Name** field and *Protect credit card numbers from being shared.* in the **Description** field. Select **Next**.

7. On the **Choose locations to apply the policy** page, enable only the **Teams chat and channel messages** option to be enabled and then select **Next**. 

8. On the **Define policy settings** page, the option **Create or customize advanced DLP rules** needs to be selected, which it should be by default. Select **Next**.

9. On the **Customize advanced DLP rules** page, select **+ Create rule**.

10. On the **Create rule** page, type *Credit card information* in the **Name** field.

11. Under **Conditions**, select **+ Add Condition** and then select **Content contains** from the dropdown menu.

12. On the **Create rule** page, in the new **Content contains** area, select **Add** and select **sensitive info types** from the dropdown menu.

13. On the **Sensitive info types** page, select **Credit Card Number** and select **Add**.

14. On the **Create rule** page, select **+ Add condition** and select **Content is shared from Microsoft 365** from the dropdown menu.

15. In the **Content is shared from Microsoft 365** section, select the **Only with people inside my organization** option, which should be selected by default.

16. On the **Create rule** page, select **+ Add an action** and select **Restrict access or encrypt the content in Microsoft 365 locations**.

17. Check the box in front of **Restrict access or encrypt the content in Microsoft 365 locations** and then select **Block Everyone**.

18. On the **Create rule** page, in the **User notifications** section, select the switch to put it in the **On** position.

19. On the **Create rule** page, in the **User overrides** section, under the **Allow overrides from M365 services**, check the box **Allow overrides from M365 services. Allows users in Exchange, Sharepoint, OneDrive and Teams to override policy restrictions**
**Note:** If you were not able to select the check box of **Allow overrides from M365 services**, enable the **Notify users in Office 365 with a policy tip** which can be found under the **User notification >>  Microsoft 365 services** from previous step. 

20. Check the box **Require a business justification to override**

21. In the **Incident reports** section, in the **Use this severity level in admin alerts and reports** dropdown, select **Low**.

22. In the **Incident reports** section, select the **Send an alert to admins when a rule match occurs.** switch to put it in the **On** position and review the options. The default settings will notify the user creating the policy.

23. Select **Save**, then select **Next**.

24. On the **Test or turn on the policy** page select **Test it out first** and select **Show policy tips while in test mode**.

25. Select **Next** and review the policy configuration.

26. Select **Submit** to create the policy.

27. Once the policy is created select **Done**.

You have now created a DLP policy that scans for Credit Card numbers in Microsoft Teams chats and channels and notifies allows users to provide a business justification to override the policy.

### Task 2 - Modify a DLP policy

In this task, you will modify the existing DLP policy you created in the previous to also scan e-mails for Credit Card information and inform users if they want to share this content in an e-mail.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Microsoft 365 compliance portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

4. In the **Data loss prevention** window select the **Policies** tab, then select the policy named **Credit Card DLP Policy** and then select **Edit policy** (pencil icon) to open the policy wizard.

5. On the **Name your DLP policy** page, select **Next**.

6. On the **Choose locations to apply the policy** page, enable the **Exchange email** option and then select **Next** until you reach the **Review your policy and create it** page.

7. Select **Submit** to apply the change you made in the policy.

You have now modified an existing DLP policy and changed the locations it scans for content.

### Task 3 - Create a DLP policy in PowerShell

In this task, you use PowerShell to create a DLP policy to protect driver's license numbers of your customers and prevent them from being shared in Exchange. Users will be informed that they are attempting to share sensitive data and are blocked from sending the e-mail if it includes driver license numbers.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In the start menu, select **Windows PowerShell**.

3. In the **PowerShell** window, type **Connect-IPPSSession** and then sign in as **Joni Sherman**. sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

4. Enter the following command into PowerShell to create a DLP policy that scans all Exchange mailboxes:

	`New-DlpCompliancePolicy -Name "Driver's License DLP Policy" -Comment "This policy blocks sharing of Driver's License Numbers." -ExchangeLocation All`

5. Enter the following command into PowerShell to add a DLP rule to the DLP policy you created in the previous step:

	`New-DlpComplianceRule -Name "Driver's License Rule" -Policy "Driver's License DLP Policy" -BlockAccess $true -ContentContainsSensitiveInformation @{Name="U.S. Driver's License Number";minCount="1";minconfidence="75"}`

6. Use the following command to review the **Driver's License DLP Policy**:

	`Get-DLPComplianceRule -Identity "Driver's License Rule"`

You have now created a DLP Policy that scans for Driver's license numbers in Exchange by using PowerShell.

### Task 4 - Activate a policy in test mode

In this task, you will activate the credit card information DLP policy you created in test mode so it enforces its protective actions.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Microsoft 365 compliance center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Microsoft 365 compliance** portal, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

4. In the **Data loss prevention** window select the **Policies** tab, and then select the policy named **Credit Card DLP policy** and then select **Edit policy** to open the policy wizard.

5. Select **Next** until you reach the **Test or turn on the policy** page and then select **Turn it on right away**.

6. Select **Next** and then select **Submit** to activate the policy.

7. Once the policy is updated select **Done**.

You have successfully activated the DLP Policy. If the policy detects an attempt to share credit card information, it will now block the attempt and allow the users to provide a business justification to override the block action.

### Task 5 - Modify policy priority

After creating two DLP policies, you want to make sure that the more restrictive policy is processed at a higher priority than the less restrictive policy. For this reason, you want to move the Driver's license policy into the higher priority.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Microsoft 365 compliance portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Microsoft 365 compliance** portal, in the left navigation pane, select **Policies** and under **Data** select **Data loss prevention**.

4. In the **Data loss prevention** window select the **Policies** tab, select the three vertical dots next to the **Driver's License DLP Policy** to open the **Actions** selection.

5. Select **Move to top**.

6. In the **Data loss prevention** window, select **Refresh** and then review the priority in the **Order** column of the policy table.

You successfully modified the priority of your DLP policies. If both policies match the same content the action of the higher priority policy will be enforced.

### Task 6 - Enable file monitoring in Microsoft Defender for Cloud Apps

You want to use file policies in Microsoft Defender for Cloud Apps to protect files in your OneDrive and SharePoint Online locations. Before you can create a file policy, you need to enable file monitoring so Microsoft Defender for Cloud Apps can scan files in your organization.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://portal.cloudappsecurity.com** and log into the Microsoft Defendger for Cloud Apps portal as **MOD Administrator**. admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

3. In the top-right corner, next to your profile information, select the **Settings** cogwheel and select **Settings** in the dropdown menu.

4. On the **Settings** page, under **Information Protection** select **Files**.

5. Select the **Enable file monitoring** checkbox and then select **Save** if it is not already marked.

You successfully enabled file monitoring in Microsoft Defender for Cloud Apps and can now scan files for sensitive content using file policies.

### Task 7 - Create File Policy for Microsoft Defender for Cloud Apps

In this task, you want to create a file policy in Microsoft Defender for Cloud Apps to scan files in OneDrive and SharePoint Online and automatically quarantine files containing credit card information if they are shared.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

2. In **Microsoft Edge**, the Microsoft Defender for Cloud Apps portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://portal.cloudappsecurity.com**.

3. In the **Microsoft Defender for Cloud Apps** portal, in the left navigation pane, expand **Control** and select **Policies**.

4. On the **Policies** page, expand **+ Create policy** and then select **File policy**.

5. On the **Create file policy** page, type *Credit Card Information for files* in the **Policy name** field, and type *Protect credit card numbers from being shared in files.* in the **Description** field.

6. Keep the **Policy Severity** on **Low** (one lighted icon) and make sure the **Category** is set to **DLP**. For a file policy, this should be the default.

7. In the **Filters** area, expand the dropdown menu **Public (Internet), External, Public** and add **Internal**.

8. In the **Inspection Method** dropdown menu, select **Data Classification Service**.

9. In the **Choose inspection type...** dropdown menu, select **sensitive information type...**.

10. In the **Select a sensitive information type** dialog, select **Credit Card Number**, then select **Done** in the upper right corner.

11. Under **Alerts**, check the **Create an alert for each matching file** checkbox and review your options. Keep the settings at the default.

12. In the **Governance actions** section, expand **Microsoft OneDrive for Business** and select **Put in user quarantine**.

13. In the **Governance actions** section, expand **Microsoft SharePoint Online** and select **Put in user quarantine**.

14. Select **Create** at the bottom of the page.

You have now created a file policy that will continuously scan files saved in OneDrive and SharePoint for credit card information and quarantine them if they are shared inside your organization.

### Task 8 - Create a DLP Policy for PowerPlatform

Your company uses PowerAutomate flows to share data between SharePoint Online and SalesForce. In this task, you will create a DLP policy for PowerPlatform that allows your existing flows to keep working, but prevents the creation of flows that will share data between SharePoint Online and Apps defined as non-business.

1. Log into the Client 2 VM (LON-CL1) as the **lon-cl2\admin** account.

2. In **Microsoft Edge**, navigate to **https://admin.powerplatform.microsoft.com** and log into the Power Platform admin center as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

3. In the **Power Platform admin center**, in the left navigation pane, select the drop-down for **Policies** and then select **Data policies**.

4. On the **Data policies** page, select **+ New Policy**.

5. On the **Name your policy** page, type *Tenant-wide SharePoint Policy*, then select **Next**.

6. On the **Non-business** tab, select **SharePoint** and **Salesforce**, then select **Move to Business** at the top of the page.

7. In the **Assign connectors** page, select the **Business** tab to make sure both SharePoint and Salesforce now appear.

8. Select **Next** twice.

9. On the **Define scope** page, select **Add all environments**, then select **Next**.

10. On the **Review and create policy** page, review your policy settings, then select **Create policy**.

You have now created a PowerPlatform DLP policy that prevents users from creating flows involving a SharePoint Online Connector and any connector that is not SalesForce.

# Proceed to Lab 2 - Exercise 2
