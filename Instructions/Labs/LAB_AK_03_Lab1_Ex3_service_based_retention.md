# Exercise 3 - Configure Service-based Retention

You assume the role of Joni Sherman, a Compliance Admin for Contoso Ltd. The legal department requires you to assist them in stopping a disgruntled employee from deleting company data.

### Task 1 – Configure Mailbox Holds

In this exercise, you will activate a Mailbox Hold to prevent any content in the employee's mailbox from being deleted.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://outlook.office.com/ecp** and log into the Exchange Admin Center as **Joni Sherman**.

3. In the **Exchange Admin Center**, in the left navigation pane, select **Recipients**, then select **mailboxes**.

4. Select the mailbox of **Alex Wilber**, then select the Pencil icon to edit the mailbox.

5. In the **Edit User Mailbox** window, select **mailbox features**.

6. Under **Litigation Hold: Disabled**, select **Enable**.

7. On the **litigation hold** page, fill in the following information:

    - **Litigation hold duration (days)**: 90
    - **Note**: Your mailbox has been put on hold for the next 90 days. You will not be able to delete any messages.

8. Select **Save** twice.

You have successfully activated the Mailbox Hold on a mailbox in your environment and stopped everyone with access from permanently deleting any content in the mailbox. Applying the hold can take up to 4 hours.

### Task 2 – Recover SharePoint Documents

In this exercise, you will delete and restore the deleted document to make sure you can restore documents the employee might delete after he is informed about the litigation hold against his mailbox.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log Microsoft 365 as **Joni Sherman**.

5. In the Microsoft O365 landing page, select the App launcher icon in the top-left corner with nine dots, then select **SharePoint** from the submenu.

6. On the SharePoint landing page, select the **Benefits @ Contoso** SharePoint site.

7. In the left navigation pane, select **Documents**.

8. Highlight **Vacation Policies.pptx** by selecting the checkbox in front of it.

9. in the top action bar, select **Delete**.

10. In the **Delete?** dialog, select **Delete**.

11. In the left navigation pane, select **Recycle bin**, then highlight **Vacation Policies.pptx** by selecting the checkbox in front of it.

12. In the top action bar, select **Restore**.

In the left navigation pane, select **Documents** and review if the file has been restored.

You have successfully recovered a document from a SharePoint Site.

# Proceed to Exercise 4