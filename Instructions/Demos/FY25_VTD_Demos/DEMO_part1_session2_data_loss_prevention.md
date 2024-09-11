---
lab:
    title: 'Data loss prevention'
    module: 'FY25 VTD Demo Session 2 - Implement data loss prevention'
---


# Session 1 demo 2 - Implement Data Loss Prevention in Microsoft Purview

## Task 1 – Create a DLP policy in simulation mode

In this exercise, you'll create a data loss prevention (DLP) policy to protect sensitive data from being shared by users.

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **MOD Administrator**. sign in as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Solutions** from the left sidebar, then select **Data Loss Prevention**.

1. On the left sidebar, select **Policies**.

1. On the **Policies** page, select **+ Create policy** to start the configuration for creating a new data loss prevention policy.

1. On the **Start with a template or create a custom policy** page, select **Custom** as the category, then select **Custom policy** under **Regulations**.

1. Select **Next**.

1. On the **Name your DLP policy** page enter:

   - **Name**: `Credit Card DLP Policy`
   - **Description**: `Protect credit card numbers from being shared`

1. Select **Next**.

1. On the **Assign admin units** page select **Next**.

1. On the **Choose locations to apply the policy** page, enable the location for **Teams chat and channel messages** only. If any other locations are selected, deselect them.

1. Select **Next**.

1. On the **Define policy settings** page, select **Create or customize advanced DLP rules**, then select **Next**.

1. On the **Customize advanced DLP rules** page, select **+ Create rule**.

1. On the **Create rule** flyout page, enter `Credit card information` as name in the **Name** field.

1. Under **Conditions**, select **+ Add Condition**, then select **Content contains**.

1. In the new **Content contains** area, select **Add**, then select **Sensitive info types**.

1. On the **Sensitive info types** page, select **Credit Card Number** then select **Add**.

1. Select **+ Add condition**, then select **Content is shared from Microsoft 365**.

1. In the new **Content is shared from Microsoft 365** section, select the **only with people inside my organization** option.

1. Under **Actions** select **+ Add an action**, then select **Restrict access or encrypt the content in Microsoft 365 locations**.

1. In the new **Restrict access or encrypt the content in Microsoft 365 locations** area select **Block everyone.**

1. Under **User notifications**, turn **On** the option for **Use notifications to inform your users and help educate them on the proper use of sensitive info.**, then select the checkbox to **Notify users in Office 365 service with a policy tip**.

1. Under **User overrides** select the checkbox to **Allow users to override policy restrictions Fabric (including Power BI), Exchange, SharePoint, OneDrive and Teams.**

1. Select the checkbox to **Require a business justification to override**.

1. Under **Incident reports**, in the **Use this severity level in admin alerts and reports** dropdown, select **Low**.

1. At the bottom of the **Create rule** flyout panel, select **Save**.

1. Back on the **Customize advanced DLP rules**, select **Next**.

1. On the **Policy mode** page select **Run the policy in simulation mode** and select the checkbox for **Show policy tips while in simulation mode**.

1. Select **Next**.

1. On the **Review and finish** page review your settings then select **Submit**.

1. On the **New policy created** page select **Done**.

You have now created a DLP policy that scans for credit card numbers in Microsoft Teams chats and channels, allowing users to provide a business justification to override the policy.

## Task 2 – Modify a DLP policy

In this task, you'll modify the existing DLP policy created in the previous task to also scan emails for credit card information. This modification ensures that sensitive data is protected across more communication channels.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. You should still be on the **Policies** page in Microsoft Purview. If not, open **Microsoft Edge** and navigate to `https://purview.microsoft.com`. Select **Solutions** > **Data Loss Prevention** > **Policies**.

1. On the **Policies** page select the checkbox for the recently created **Credit Card DLP Policy**, then select **Edit policy** to open the policy configuration.

1. On the **Name your DLP policy** page, select **Next**.

1. On the **Assign admin units** page select **Next**.

1. On the **Choose locations to apply the policy** page, select the checkbox for **Exchange email** to add this location to your DLP policy.

1. Select **Next** until you reach the **Review and finish** page.

1. Select **Submit** on the **Review and finish** page to apply the change you made to the policy.

1. Once the policy is updated select **Done** on the **Policy updated** page.

You have successfully modified the DLP policy to include email scanning, enhancing the protection of sensitive information.

## Task 3 – Test your DLP Policy

In this task you'll test the DLP policy that was created in the previous task.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account and logged into Microsoft 365 as MOD Administrator.

1. Open a Microsoft Edge browser window and navigate to **`https://outlook.office.com`**

1. Select the **New mail** button on the top left to compose a new email message.

1. In the **To** field, enter `Megan` and select **Megan Bowen**'s email address.

1. In the subject field enter `Help with employee information`.

1. In the body of the email enter:

   ``` text
   Please help me with the start dates for the following employees:
   ABC123456
   DEF678901
   GHI234567

   Thank you
   ```

1. Select the **Send** button in the upper right of the message window to send the email.

1. You should receive a message that the email was undeliverable and blocked by a DLP policy.

      ![Screenshot of Manage roles option](../Media/dlp-email-blocked.png)

You have successfully tested your DLP policy.

## Task 4 – Activate a policy in simulation mode

In this task, you'll activate the **Credit Card DLP Policy** you created in simulation mode so it enforces its protective actions.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, navigate to DLP policies by going to `https://purview.microsoft.com` > **Solutions** > **Data Loss Prevention** then select **Policies** from the left sidebar.

1. On the  **Policies** page select the checkbox for the **Credit Card DLP Policy** and select **Edit policy** to open the policy configuration.

1. Select **Next** until you reach the **Policy mode** page and select **Turn the policy on immediately**.

1. On the **Review and finish** select **Submit**.

1. On the **Policy updated** page select **Done**.

You have successfully activated the DLP policy, ensuring that any attempts to share credit card information are blocked and require a business justification.
