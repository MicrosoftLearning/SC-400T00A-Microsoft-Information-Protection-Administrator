---
lab:
    title: 'Exercise 1 - Configure Communication Compliance'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---
## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab 5 - Exercise 1 - Configure Communication Compliance

As the Compliance Administrator for your organization, you are responsible for configuring Microsoft Communication Compliance to help ensure that your organization meets its compliance requirements. Microsoft Communication Compliance allows you to monitor communication activities in various channels, such as email, Microsoft Teams, and other chat and collaboration tools, to help detect and mitigate policy violations and other inappropriate behaviors.

**Tasks**:

1. Assign Compliance Administrator Role
1. Configure a Custom Policy
1. Test your custom policy (Optional)
1. Manage your communication compliance policy (Optional)
1. Modify communication compliance policy

## Task 1 – Assign Compliance Administrator Role

In this exercise, you will assign the Communication Compliance role to Joni to grant access to perform communication compliance tasks in the Microsoft Purview portal.

1. Log into the Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. In Microsoft Edge, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as MOD Administrator, **`admin@WWLxZZZZZZ.onmicrosoft.com`** (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Select **Settings** from the left sidebar.

1. Expand **Roles and Scopes** then select **Role groups**.

1. On the **Role groups for Microsoft Purview solutions** page select **Communication Compliance**.

1. On the **Communication Compliance** flyout panel on the right, select **Edit**.

1. On the **Edit members of the role group** page select **+ Choose users**.

1. On the **Choose users** flyout panel, search for `Joni` then select the checkbox for **Joni Sherman**.

1. Select the **Select** button at the bottom of the panel.

1. On the **Edit members of the role group** page select **Next**.

1. On the **Review the role group and finish** page select **Save**.

1. Once you have successfully added Joni to the role group, select **Done** on the **You successfully updated the role group** page.

1. Sign out of the Mod Administrator account by selecting the MA icon on the top right of the window, then selecting **Sign out**.

You have successfully assigned the Communication Compliance role to Joni Sherman, granting her access to perform communication compliance tasks in the Microsoft Purview portal.

## Task 2 – Configure a Custom Policy

In this exercise, you will configure a custom policy in Microsoft Communication Compliance to monitor communications for sensitive financial information.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. On left sidebar, select **Solutions** then select **Communication Compliance**.

1. On the **Communication compliance** page, from the top navigation bar,  select **Policies**.

1. On the left sidebar, select **Policies**.

1. On the **Policies** page, select **+ Create policy**, then select **Custom policy**.

1. On the **Name and describe your policy** enter:

    - **Name**: `Detect Financial Secrets`
    - **Description** `Detection of sharing financial secrets`

1. Select **Next**.

1. On the **Choose users and reviews** page, under **Choose users and groups**, leave **All users** selected.

1. In the **Reviewers** field, enter and select **`Joni Sherman`** and **`MOD Administrator`**, then select **Next**.

1. On the **Choose locations to detect communications** page select **Exchange**. Leave all other locations deselected, then select **Next**.

1. On the **Choose conditions and review percentage** page under **Communication direction** leave defaults selected.

1. Under **Condition** select **+ Add condition**, then select **Message contains any of these words**.

1. In the field under **Message contains any of these words** enter `secret,secrets`.

    >**Note:** To apply the policy based on specific words or phrases in a message, enter them separated by commas. No spaces between comma-separated items. Use quotation marks for phrases of two or more words. Each word or phrase is applied independently (only one word is needed to trigger the policy).

1. Under **Review percentage** adjust the slider to **100%**, then select **Next**.

1. On the **Review and finish** page, select **Create policy**.

1. Once your policy has been successfully created, select **Done** on the **Your policy was created** page.

1. Your communication compliance policy has been created.

1. Log out of Joni's account and close all browser windows.

    >**Note:** Make sure you give your policies time to activate before testing the policy. Email messages can take approximately 24 hours to fully process in a policy. Communications in Microsoft Teams, Yammer, and third-party platforms can take approximately 48 hours to fully process in a policy.

## Task 3 – Test your custom policy (Optional)

In this task, you will verify the effectiveness of your configured custom policy. Through testing different scenarios, you will assess the policy's ability to identify and flag sensitive financial information. These tests provide valuable real-world insights into the policy's behavior.

>**Note:** Make sure you give your policies time to activate before testing the policy. Email messages can take approximately 24 hours to fully process in a policy. Communications in Microsoft Teams, Viva Engage, and third-party platforms can take approximately 48 hours to fully process in a policy.

1. In **Microsoft Edge**, navigate to **`https://outlook.office.com`** and log into Outlook on the web as `LynneR@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **New mail** in Outlook on the web.

1. In the **To** line enter **`Joni Sherman`** and select the suggested email address. Enter **`New Secret Message`** in the subject line and **`My super-secret message.`** in the body of the email.

1. Select **Send** to send the message.

1. Once that message is sent, select **New mail** again in Outlook on the web.

1. In the **To** line enter **`Megan Bowen`** and select the suggested email address. Enter **`Big secret!`** in the subject line, and **`We have a surprise baby shower coming for Debra! Keep it secret!`** in the body of the email.

1. Select **Send**

1. Lynne wants to send one last email. Select **New mail** in Outlook on the web.

1. In the **To** line enter **`Debra Berger`** and select the suggested email address. In the subject line enter **`Northwind Acquisition`**, and enter **`Debra! I just heard a HUGE financial secret about Northwind's acquisition! Let's get together at lunch to discuss.`** in the body of the email.

1. Select **Send**

1. Logout of Lynne's account and close all browser windows.

You have successfully tested your custom policy to verify its effectiveness in identifying and flagging sensitive financial information.

## Task 4 – Manage your communication compliance policy (Optional)

In this task, you will manage your communication compliance policy in the Microsoft Purview portal. You will review and take action on the pending items for the **Detect Financial Secrets** policy to ensure your policy is working effectively to identify and handle any potential compliance issues.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in a previous task.

1. Select **Solutions** from the left sidebar, then select **Communication Compliance**.

1. Select **Policies** then select the **Detect Financial Secrets** policy.

1. Select the **Pending** tab to review the pending items for the Detect Financial Secrets policy.

    >**Note:** Please note that if the **Pending** count is 0, it might require additional time for your tests to be completely processed by the policy. Keep in mind that email messages can take approximately 24 hours to fully process within a policy.

1. Select the item with the subject **Big Secret!**.

1. Since this message is a simple notification of a party, select **Resolve**. In the **Resolve** pane enter **Policy modification needed** in the **Comment** field then select **Resolve**.

1. There will now be 2 pending items for the Detect Financial Secrets policy. Select the item with the subject **New Secret Message**.

1. Under the message that appears in the right, select **Tag as**.

1. In the **Tag item** pane, select **Questionable**. In the **Comment** field enter **Questionable secret item** then select **Save**.

1. In the Detect Financial Secrets policy, select the item with the subject **Northwind Acquisition**.

1. Select **Notify** under the Northwind Acquisition item.

1. In the **Send a notice pane** select the dropdown for **Chose a notice template**. Select **+ Create a new notification** to create a new notice template.

1. In the **Create a notice template** panel, enter:

   - **Template Name**: `Offending message`
   - **Send from:** `Joni Sherman`, then select **Joni Sherman**
   - **Subject**: `Offending message detected`
   - **Message body**: `This is to notify an offending message was detected and will be escalated.`

1. Select **Create**.

1. Once the template is successfully created, select **Close** on the **Notice template Offending message was created** panel.

1. In the **Send a notice** panel under **Choose a notice template**, select the newly created **Offending message** notice template then select **Save**.

1. In the **Notification has been sent** panel select **Close**.

1. In the Detect Financial Secrets policy, select the item with the subject **Northwind Acquisition**.

1. Select **Escalate** under the Northwind Acquisition item.

1. In the **Escalate remediation for this item** select **MOD Administrator** as an additional reviewer. In the **Reason for escalation** field enter **`Data leak plans detected.`** then select **Escalate**.

1. In the **Escalation has been sent** panel select **Close**.

1. Back in the view for the message for the Northwind Acquisition message, select **Tag as**. In the **Tag item** pane select **Non-compliant**. Enter **`Non-compliant message`** in the **Comment** field then select **Save**.

You have successfully managed your communication compliance policy by reviewing and resolving pending items.

## Task 5 – Modify communication compliance policy

In this task you will make modifications to your Communication compliance policy. You will fine-tune the policy settings and add new conditions to detect sensitive information to ensure your policy aligns with the compliance needs of Contoso Ltd.

1. You should still be logged in with Joni's account in **Communication compliance** in the Microsoft Purview compliance portal.

1. Select **Policies** from the left sidebar.

1. Select the checkbox for the **Detect Financial Secrets** policy.

1. Select **Edit** from the top navigation bar.

1. On the **Name and describe your policy** page select **Next**.

1. On the **Choose users and reviewers** page select **Next**.

1. On the **Choose locations to detect communications** page select **Next**.

1. On the **Choose conditions and review percentage** page select **+ Add Condition** then select **Content matches any of these trainable classifiers**.

1. Under **Content matches any of these trainable classifiers** select **Add** then select **Trainable classifiers**.

1. On the **Trainable classifiers** flyout panel, select **Unauthorized disclosure**, then select **Add** at the bottom of the panel.

1. Back on the **Choose conditions and review percentage** page, select **Next**.

1. On the **Review and finish** page select **Save**.

1. On the **Your policy was updated** page select **Done**.

You have successfully modified your communication compliance policy to include a new condition for detecting a sensitive info type.
