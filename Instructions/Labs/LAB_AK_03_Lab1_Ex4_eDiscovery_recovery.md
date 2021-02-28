# Exercise 4 - Use eDiscovery for Recovery

In this exercise you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to adhere to local laws. The Uniform Preservation of Private Business Records Act specifies that records may be destroyed after three years without constituting an offense under the law (with some exceptions), to adhere to this law your organization has created a retention plan to retain all items in the organization for three years.

### Task 1 – Create eDiscovery Case

In this exercise, you will create an eDiscovery Case and start a search for mails containing Information about the Mark 8 Project sent by Megan Bowen. The legal department requested this information for a compliance review.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider. 

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the Compliance Center, in the left navigation pane, select ***... Show all**, then expand **eDiscovery** and select **Core**.

4. On the **Core eDiscovery** page, select **+ Create a case**.

5. In the **Case name** field, type *Mark 8 Project Case* and in the **Case description** type *This case will be used to evaluate Megan Bowen's mails regarding the Mark 8 Project.*, then select **Save**

6. On the **Core eDiscovery** page, select **Mark 8 Project Case** and select **Open case**.

7. In the Case view, select the **Searches** tab.

8. Select **+ New search**.

9. In the **Keywords** section, type *Mark 8 Project*.

10. In the **Locations** section, select **Specific locations**, then select **Modify...**.

11. In the **Modify locations** dialog, behind **Exchange email**, select **Choose users, groups, or teams**.

12. In the **Edit locations** dialog, select **Choose users, groups, or teams**.

13. In the search bar, type **Megan Bowen** and select the checkbox in front of **Megan Bowen** in the **Users, groups, or teams** list after the search completed, then select **Choose**.

14. Select **Done** and select **Save**.

15. Uncheck the **Add app content for On-Premises Users** checkbox.

16. Select **Save & run**.

17. In the **Save search** dialog, type **Mark 8 Project search** into the **Name** field, then select **Save**.

You have successfully created an eDiscovery case and searched for all mails Megan Bowen sent or received containing information about the Mark 8 Project.

### Task 2 – Assign Records Management permissions

In this task, you will prepare to export the data you discovered in Task 1 to a PST-file that you can provide to the legal department. First you need to assign the Records Management role to your compliance administrator. Otherwise they will not be able to export search results.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://protection.office.com** and log into the Security & Compliance Center as **MOD Administrator**.

3. In the left navigation pane, select **Permissions** and then select the **Records Management** role.

4. In the role overview pane, select **Edit** next to the **Members** category.

5. Select **Choose Members** and then select **+ Add**.
 
6. Search for **Joni Sherman** and select the checkbox in front of their name, then select **Add**.

7. Review the changes to the member list and then select **Done**.

8. Select **Save**.

You have successfully granted your compliance administrator the permission to export search results. It can take up to 60 minutes until the permissions are applied.

### Task 3 – Export Data from eDiscovery Case

In this task, you will prepare to export the data you discovered in Task 1 so that you can provide to the legal department.  Remember it may take 60 minutes for permissions to become available in your tenant.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the Compliance Center, in the left navigation pane, select ***... Show all**, then expand **eDiscovery** and select **Core**.

4. Check the checkbox in front of **Mark 8 Project Case** and select **Open case**.

5. Navigate to the **Searches** tab and select **Mark 8 Project search**.

6. In the **Mark 8 Project search** dialog, select **Export report**.

7. In **Output options**, select **All items, including ones that have unrecognized format, are encrypted, or weren't indexed for other reasons**.  Select **Generate report**.

You have successfully exported the discovered data.

### Task 4 – Perform Search & Purge on Mailboxes

An investigation showed that users received a few phishing mails and you are tasked with deleting these across all mailboxes in your environment.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the Compliance Center, in the left navigation pane, select ***... Show all**, then select **Content search**.

4. Select **+ New search**.

5. In the **Keywords** field, type *From:phishingmail@outlook.com AND subject:"Password changed"*

6. In the **Locations** section, select **Specific locations**, then select **Modify...**.

7. In the **Modify locations** dialog, next to **Exchange email**, switch **Select all** to **On**, then select **Save**.

8. Select **Save & run** and in the **Name** field, type *Phishing mail removal*, then select **Save**.

9. Once you created the search, you need to use the **Security & Compliance PowerShell** to start a purge. In the start menu, select **Windows PowerShell** run as Administrator.

10. In the **PowerShell** window, use the following cmdlet and then sign in as **MOD Administrator**:

	Connect-IPPSSession

11. In the **PowerShell** window, use the following command and confirm with **Y**:

	New-ComplianceSearchAction -SearchName "Phishing mail removal" -Purge -PurgeType HardDelete

12. In PowerShell type **Y** for Yes to confirm the action.

You have successfully created a new content search to look for specific emails and then used the purge action to delete the phishing mails from your user's mailboxes. You can only run the purge action as a member of the Organization Management role, which a Compliance Admin is not part of.

# Proceed to Exercise 5