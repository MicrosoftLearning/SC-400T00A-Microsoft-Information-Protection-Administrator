---
lab:
    title: 'Data loss prevention'
    module: 'FY25 VTD Demo Session 2 - Implement data loss prevention'
---


# Part 1 Demo 2 - Implement Data Loss Prevention in Microsoft Purview

Contoso Ltd. has faced growing concerns over sensitive customer data being shared externally, especially as remote work has increased. To prevent this risk, they are implementing Data Loss Prevention (DLP) policies in Microsoft Purview to block unauthorized sharing of important information.

## Task 1 – Create a DLP policy in simulation mode

In this task, we'll create a DLP policy to protect customer data from being shared externally via Exchange email and Teams chat and channel messages.

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **MOD Administrator**. sign in as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Solutions** from the left sidebar, then select **Data Loss Prevention**.

1. On the left sidebar, select **Policies**.

1. On the **Policies** page, select **+ Create policy** to start the configuration for creating a new data loss prevention policy.

1. On the **Start with a template or create a custom policy** page, select **Custom** as the category, then select **Custom policy** under **Regulations**.

1. Select **Next**.

1. On the **Name your DLP policy** page enter:

   - **Name**: `Customer Data DLP Policy`
   - **Description**: `Protect customer data from being shared externally.`

1. Select **Next**.

1. On the **Assign admin units** page select **Next**.

1. On the **Choose locations to apply the policy** page, enable the locations for **Exchange email** and **Teams chat and channel messages** only. If any other locations are selected, deselect them.

1. Select **Next**.

1. On the **Define policy settings** page, select **Create or customize advanced DLP rules**, then select **Next**.

1. On the **Customize advanced DLP rules** page, select **+ Create rule**.

1. On the **Create rule** flyout page, enter `Customer Data Protection` as name in the **Name** field.

1. Under **Conditions**, select **Content is shared from Microsoft 365**.

1. In the new **Content is shared from Microsoft 365** section, select the **only with people outside of my organization** option.

1. Select **+ Add condition**, then select **Content contains**.

1. In the new **Content contains** area, select **Add**, then select **Trainable classifiers**.

1. On the **Trainable classifiers** page, search for `Customer`.

1. Select the trainable classifiers for **Customer Complaints** and **Customer Files** then select **Add**.

1. Under **Actions** select **+ Add an action**, then select **Restrict access or encrypt the content in Microsoft 365 locations**.

1. In the new **Restrict access or encrypt the content in Microsoft 365 locations** area select **Block only people outside your organization.**

1. Under **User notifications**, turn **On** the option for **Use notifications to inform your users and help educate them on the proper use of sensitive info.**, then select the checkbox to **Notify users in Office 365 service with a policy tip**.

1. Under **User overrides** select the checkbox to **Allow users to override policy restrictions Fabric (including Power BI), Exchange, SharePoint, OneDrive and Teams.**

1. Select the checkbox to **Require a business justification to override**.

1. Under **Incident reports**, in the **Use this severity level in admin alerts and reports** dropdown, select **High**.

1. At the bottom of the **Create rule** flyout panel, select **Save**.

1. Back on the **Customize advanced DLP rules**, select **Next**.

1. On the **Policy mode** page select **Run the policy in simulation mode** and select the checkbox for **Show policy tips while in simulation mode**.

1. Select **Next**.

1. On the **Review and finish** page review your settings then select **Submit**.

1. On the **New policy created** page select **Done**.

You have now created a DLP policy that scans for customer data in Exchange email and Teams chats and channels, allowing users to provide a business justification to override the policy.

## Task 2 – Activate a policy in simulation mode

In this task, you'll activate the Customer Data DLP Policy to enforce its protective actions.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft Purview as **MOD Administrator**.

1. In **Microsoft Edge**, navigate to DLP policies by going to `https://purview.microsoft.com` > **Solutions** > **Data Loss Prevention** then select **Policies** from the left sidebar.

1. On the  **Policies** page select the checkbox for the **Customer Data DLP Policy** and select **Edit policy** to open the policy configuration.

1. Select **Next** until you reach the **Policy mode** page and select **Turn the policy on immediately**.

1. On the **Review and finish** select **Submit**.

1. On the **Policy updated** page select **Done**.

You have successfully activated the DLP policy, ensuring that any attempts to share customer data are blocked and require a business justification.
