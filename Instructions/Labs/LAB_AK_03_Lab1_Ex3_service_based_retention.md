---
lab:
    title: 'Exercise 3 - Configure Service-based Retention'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 3 - Configure Service-based Retention

You assume the role of Joni Sherman, a Compliance Admin for Contoso Ltd. The legal department requires you to assist them in stopping a disgruntled employee from deleting company data.

## Task 1 – Configure Mailbox Holds

In this task, you will activate a Mailbox Hold to prevent any content in the employee's mailbox from being deleted.

1. Log into the Client 1 virtual machine (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://admin.exchange.microsoft.com** and log into the Exchange Admin Center as **Joni Sherman**. Sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Close all tip windows if any appear.

1. In the Exchange Admin Center, in the left navigation pane, expand **Recipients** then select **Mailboxes**.

1. Select the mailbox of **Alex Wilber**, then select the Pencil icon to edit the mailbox.

1. Select  **Alex Wilber** from the list of mailboxes, and a flyout page on the right displaying Alex's mailbox settings will appear.

1. On Alex Wilber's flyout page, select the **Others** tab.

1. Under **Litigation hold** select **Manage litigation hold**.

1. On the **Manage litigation hold** hold page, toggle the **Litigation hold** setting from _Off_ to _On_ to display the litigation hold settings.

1. Set the the following hold settings:

    - **Hold duration (days).**: 90
    - **Note (visible to the user)**: Your mailbox has been put on hold for the next 90 days. You will not be able to delete any messages.

1. Select **Save**, then a message displaying **Litigation hold updated** should appear.

You have successfully activated the Mailbox Hold on a mailbox in your environment and stopped everyone with access from permanently deleting any content in the mailbox. Applying the hold can take up to 4 hours.  You can proceed to the next task immediately.

## Task 2 – Recover SharePoint Documents

In this task, you will delete and restore a deleted document to make sure you can restore documents the employee might delete after he is informed about the litigation hold against his mailbox.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://www.office.com** and log in Microsoft 365 as **Joni Sherman**.

1. If a welcome screen is displayed, close it. If the Office 365 apps notification appears, also close it.

1. In the Microsoft Office 365 landing page, select the App launcher icon in the top-left corner (icon with nine dots), then select **SharePoint** from the sub-menu.

1. If the **Welcome to SharePoint Start Page** appears, close it.

1. On the SharePoint landing page, select the **Benefits @ Contoso** SharePoint site.

1. In the left navigation pane, select **Documents**.

1. On the **Documents** page, select the checkbox to the left of **Vacation Policies.pptx** then select **Delete** from the action bar.

1. In the **Delete?** dialog, select **Delete**.

1. In the left navigation pane, select **Recycle bin**, then highlight **Vacation Policies.pptx** by selecting the checkbox in front of it.

1. In the top action bar, select **Restore**.

1. In the left navigation pane, select **Documents** and review if the file has been restored.

You have successfully recovered a deleted document from a SharePoint Site.
