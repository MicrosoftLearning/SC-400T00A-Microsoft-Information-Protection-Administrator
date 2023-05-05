---
lab:
    title: 'Exercise 5 - Use eDiscovery for Recovery'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 5 - Use eDiscovery for Recovery

In this exercise you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to adhere to local laws. The Uniform Preservation of Private Business Records Act specifies that records may be destroyed after three years without constituting an offense under the law (with some exceptions), to adhere to this law your organization has created a retention plan to retain all items in the organization for three years.

## Task 1 – Create eDiscovery Case

In this exercise, you will create an eDiscovery Case and start a search for mails containing Information about the Mark 8 Project sent by Megan Bowen. The legal department requested this information for a compliance review.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the portal, on the left navigation pane, expand **eDiscovery** and select **Standard**.

1. On the **eDiscovery (Standard)** page, select **+ Create a case**.

1. On the **New case** page in the **Name** field, type *Mark 8 Project Case* and in the **Description** type *This case will be used to evaluate Megan Bowen's mails regarding the Mark 8 Project.*, then select **Save**.

1. Back on the **Core eDiscovery (Standard)** page, select the **Mark 8 Project Case** to open the case.

1. In the Case view, select the **Searches** tab.

1. Select **+ New search** to start a new search.

1. On the **Name and description** page, type *Mark 8 Project* for the name and select **Next**.

1. On the **Locations** page, turn **Exchange mailboxes** to **On**, then select **Choose users, groups, or teams**.

1. On the **Exchange mailboxes** page search *Megan Bowen* and select Megan's mailbox.  Select **Done**.

1. On the **Locations** page uncheck the **Add App Content for On-Premises Users** checkbox and select **Next**.

1. On the **Define your search conditions** page in the **Keywords** area type *Mark 8* and select **Next**.

1. In the **Review your search and create it** window select **Submit**.

1. Once your search is created select **Done**.

You have successfully created an eDiscovery case and searched for all mails Megan Bowen sent or received containing information about the Mark 8 Project.

## Task 2 – Assign Records Management and eDiscovery Manager permissions

In this task, you will prepare to export the data you discovered in Task 1 to a PST-file that you can provide to the legal department. First you need to assign the Records Management role to your compliance administrator. Otherwise they will not be able to export search results.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. Select the **Profile picture** of **Joni Sherman** in the top right corner and select **Sign out**. Afterwards close the browser.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider. 

1. In the left navigation pane, select **Permissions** and then under **Microsoft Purview solutions** select **Roles**.  Select the **Records Management** role.

1. In the **Records Management** pane, select **Edit** next to the **Members** category.

1. Select **Choose members** and then select **+ Add**.
 
1. Search for **Joni Sherman** and select the checkbox in front of their name, then select **Add**.

1. Review the changes to the member list and then select **Done**.

1. Select **Save** and **Close**.

1. On the **Role groups for Microsoft Purview solutions** select the **eDiscovery Manager** role.

1. On the **eDiscovery Manager** pane, select **Edit** next to the **eDiscovery Manager** category.

1. On the **Editing Choose eDiscovery Manager** pane select **Choose eDiscovery Manager**.

1. Select **+ Add** and search for **Joni Sherman** and select the checkbox in front of their name, then select **Add**.

1. Review the changes to the member list and then select **Done**.

1. Select **Save** and **Close**.

You have successfully granted your compliance administrator the permission to export search results and perform records management tasks. It can take up to 60 minutes until the permissions are applied to the user, but you can proceed to the next task.

## Task 3 – Export Data from eDiscovery Case

In this task, you will prepare to export the data you discovered in Task 1 so that you can provide to the legal department.  Remember it may take 60 minutes for permissions to become available in your tenant.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. Select the **Profile picture** of **MOD Administrator** in the top right corner and select **Sign out**. Afterwards close the browser.

1. Open **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In the **Microsoft Purview** portal, in the left navigation pane, expand **eDiscovery** and select **Standard**.

1. Select the **Mark 8 Project case** to open the case.

1. Select the **Searches** tab and select the **Mark 8 Project** search.

	>[!TIP]
	If your eDiscovery search has no data consider the parameters of the search. Megan's mailbox should include some messages about the *Mark 8* project.  If not consider changing the keyword in the search to any of the terms in any of the existing emails in Megan's mailbox.  For example, the term "planner" usually appears in several of  Megan's existing emails.  The search must have data in order for the export to have anything process.

1. In the **Mark 8 Project** dialog, select **Actions** button drop-down, and select **Export results**.

1. In the **Export results** pane, under **Output options** review the options.  Select the **Export** button.

	[//]: <> (Request failed with status code 500 in LOD tenant - worked before in our M365 Dev tenants)

1. Once the **compliance** window pops up select **OK**.

1. Select the **Exports** tab from the case screen.  Double-click the export that was just created.

1. In the export pane, under **Export key** select **Copy to clipboard**, and then select **Download results**.
  
1. When prompted select **Open** in the browswer to install the eDiscovery Export Tool, and then select **Install**.

1. In the dialog box that appears paste in the key you copied to clipboard earlier.  Select a suitable location to download the file. Select **Start**. 

You have successfully exported the discovered data.

## Task 4 – Perform Search & Purge on Mailboxes

An investigation showed that users received a few phishing mails and you are tasked with deleting these across all mailboxes in your environment.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the Purview portal, in the left navigation pane, select **Content search**.

1. Select **+ New search**.

1. In the **Name and description** window type *Phishing mail removal* as the **Name** and select **Next**.

1. In the **Locations** section, select **Exchange mailboxes** and select **Next**.

1. In the **Define your search conditions** page in the **Keywords** field, type *From:phishingmail@outlook.com AND subject:"Password changed"* and select **Next**.

1. In the **Review your search and create it** window select **Submit**. Then **Done**.

1. Once you created the search, you need to use the **Security & Compliance PowerShell** to start a purge. In the start menu, select **Windows PowerShell** run as Administrator.

1. In the **PowerShell** window, use the following cmdlet and then sign in as **MOD Administrator**:

	```powershell
	Connect-IPPSSession
	```

1. In the **PowerShell** window, use the following command:

	```powershell
	New-ComplianceSearchAction -SearchName "Phishing mail removal" -Purge -PurgeType HardDelete
	```

1. In PowerShell type **Y** for Yes and press **Enter** to confirm the action.

You have successfully created a new content search to look for specific emails and then used the purge action to delete the phishing mails from your user's mailboxes. You can only run the purge action as a member of the Organization Management role, which a Compliance Admin is not part of.
