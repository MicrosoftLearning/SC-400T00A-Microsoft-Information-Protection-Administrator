# Lab 3 - Exercise 3 - Configure Service-based Retention

You assume the role of Joni Sherman, a Compliance Admin for Contoso Ltd. The legal department requires you to assist them in stopping a disgruntled employee from deleting company data.

### Task 1 – Configure Mailbox Holds

In this task, you will activate a Mailbox Hold to prevent any content in the employee's mailbox from being deleted.

1. Log into the Client 1 virtual machine (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://outlook.office.com/ecp** and log into the Exchange Admin Center as **Joni Sherman**.

3. In the **Exchange Admin Center**, in the left navigation pane, select **recipients**, then select **mailboxes**.

4. Select the mailbox of **Alex Wilber**, then select the Pencil icon to edit the mailbox.

5. In the **Edit User Mailbox** window, select **mailbox features**.

6. Under **Litigation Hold: Disabled**, select **Enable**.

7. On the **litigation hold** page, fill in the following information:

    - **Litigation hold duration (days)**: 90
    - **Note**: Your mailbox has been put on hold for the next 90 days. You will not be able to delete any messages.

8. Select **Save** twice.

You have successfully activated the Mailbox Hold on a mailbox in your environment and stopped everyone with access from permanently deleting any content in the mailbox. Applying the hold can take up to 4 hours.  You can proceed to the next task immediately.

### Task 2 – Recover SharePoint Documents

In this task, you will delete and restore a deleted document to make sure you can restore documents the employee might delete after he is informed about the litigation hold against his mailbox.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log Microsoft 365 as **Joni Sherman**.

3. In the Microsoft Office 365 landing page, select the App launcher icon in the top-left corner (icon with nine dots), then select **SharePoint** from the sub-menu.

4. On the SharePoint landing page, select the **Benefits @ Contoso** SharePoint site.

5. In the left navigation pane, select **Documents**.

6. Highlight **Vacation Policies.pptx** by selecting the checkbox in front of it.

7. in the action bar, select **Delete**.

8. In the **Delete?** dialog, select **Delete**.

9. In the left navigation pane, select **Recycle bin**, then highlight **Vacation Policies.pptx** by selecting the checkbox in front of it.

10. In the top action bar, select **Restore**.

11. In the left navigation pane, select **Documents** and review if the file has been restored.

You have successfully recovered a deleted document from a SharePoint Site.

# Proceed to Lab 3 - Exercise 4
