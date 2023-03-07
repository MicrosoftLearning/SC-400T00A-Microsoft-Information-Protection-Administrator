---
lab:
    title: 'Exercise 2 - Implement Retention Labels'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 2 - Implement Retention Labels

In this exercise, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Sudbury England and has legal obligations to retain finance documents. 

Your finance department has created a retention plan to set retention labels on documents for Value Added Tax (VAT) returns with supporting documents and Credit Card receipts.
 
### Task 1 – Create Retention Labels

In this task, you will create a retention label that can be assigned to documents and emails that contain VAT returns and a retention label that can be applied to Credit Card receipts.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, select the **Labels** tab.

1. Select the **+ Create a label** button.

1. On the **Name your retention label page** for the **Name**, **Description for users**, and **Description for admins**, enter the following information:

	- **Name**: VAT Returns and supporting documents
	- **Description for users**: Assign this label to VAT Documents to ensure they are retained for the legal period of seven years.
	- **Description for admins**: VAT returns with seven-year retention.

1. Select the **Next** button.

1. On the **Define label settings** page, choose the **Retain items forever or for a specific period** setting and select the **Next** button.

1. On the **Define the period** page set the following information:
	- **How long is the period?**: 7 Years
	- **When should the period begin?**: When items were created
1. Select the **Next** button.
1. On the **Choose what happens after the retention period** page, choose **Deactivate retention settings**.

1. Select the **Next** button.

1. On the **Review and finish** page, select the **Create label** button.  On the **Your retention label is created** page select the **Do Nothing** option and select **Done**. The label will be published later in the Exercises.

1. On the **Data lifecycle management** page, select the **+ Create a label** button.

1. On the **Name your retention label** page for the **Name**, **Description for users**, and **Description for admins** enter the following information:
	- **Name**: Credit Card Receipts
	- **Description for users**: This label is auto applied to Credit card receipts with a retention period of three years.
	- **Description for admins**: Auto applied retention label for Credit card receipts with three-year retention.

1. Select the **Next** button.

1. On the **Define label settings** page, choose **Retain items forever or for a specific period** and select the **Next** button.
1. On the **Define the period** page set the following information:
	- **How long is the period?**: Select the drop down list and select **Custom**. Enter 3 for Years.
	- **When should the period begin?**: When items were created.
1. Select the **Next** button.
1. On the **Choose what happens after the retention period** page, choose **Deactivate retention settings** and select the **Next** button.

1. On the **Review and finish** page, select the **Create label** button. On the **Your retention label is created** page select the **Do Nothing** option and then select **Done**.

You have successfully created a retention label for VAT returns with a seven-year retention period and a retention label for Credit Card receipts with a three-year retention.

### Task 2 – Publish Retention Labels

Following from Task 1 you will now publish the VAT returns retention label so that the published label will be available for the finance users to apply to the documents in Exchange emails and Sharepoint documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** Page, select the tab **Labels**.

1. Select the label **VAT Returns and supporting documents**, that you created in Task 1.

1. Select the **Publish labels** icon button (next to the pencil).

1. On the **Choose labels to publish** page, select the **Next** button.

1. On the **Choose the type of retention policy to create** page, select the **Static** item.

1. Select the **Next** button.

1. On the **Choose locations** page select the option **Let me choose specific locations**.

1. Enter the following information:

	- **Exchange mailboxes** location - **Status**: On
	- **SharePoint classic and communication sites** location - **Status**: On
	- **OneDrive accounts** location - **Status**: On
	- **Microsoft 365 Groups mailboxes & sites** location - **Status**: OFF  

1. Select the **Next** button.

1. On the **Name your policy** page for **Name** and **Description** enter the following information:

	- **Name**: VAT Returns and supporting documents Retention Label
	- **Description**: VAT Returns and supporting documents Retention label, retention period 3 years, Exchange email and SharePoint site locations.

1. Select the **Next** button.

1. On the **Finish** page, select the **Submit** button.  When your policy is created select **Done**.

You have successfully published the retention label for VAT Returns and supporting documents.

### Task 3 – Publish auto-apply Retention Labels

Following from Task 1 you will now auto-apply the Credit Card receipts retention label so that the information is retained.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, select the tab **Labels**.

1. Select the label **Credit Card Receipts**, that you created in Task 1.

1. Select the **Auto-apply a label** icon button (lightning + cogwheel).

1. On the **Let's get started** page, for **Name** and **Description** enter the following information:

	- **Name**: Credit Card Receipts auto-applied
	- **Description**: Credit Card Receipts auto-applied retention label, with a retention period of three years for all location.

1. Select the **Next** button.

1. On the **Choose the type of content you want to apply this label to** page select:

	- **Apply label to content that contains sensitive info**

1. Select the **Next** button.

1. On the **Content that contains sensitive info** page, select the category **Financial**. 

1. Financial templates will then be displayed under Templates. 

1. Scroll down and select the **U.K. Financial Data** template.

1. Select the **Next** button.

1. On the **Define content that contains sensitive info** page, select the **Next** button.

1. On the **Choose the type of retention policy to create** page, select the **Static** item and select **Next**. 

1. On the **Choose locations to apply the policy** page, turn **On** the options for: **Exchange mailboxes, SharePoint classic and communication sites, OneDrive accounts, and Microsoft 365 Group mailboxes & sites** and select **Next**.

1. On the **Choose a label to auto-apply** page, select **Next**.

1. On the **Decide whether to test or run your policy** select **Turn on policy** then select **Next**.

1. On the **Review and finish** page select the **Submit** button.  When the policy is created, select **Done**.

You have successfully published a retention label with auto-apply. Over the next seven days all documents containing credit card details will be automatically labeled with the published label Credit Card Receipts, a retention period of three years will be applied to these items.

### Task 4 – Work with retention labels in Outlook emails

In this task, you will assign retention labels to Outlook emails.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. On the taskbar at the bottom of the page, select the Start button, scroll down and then select **Outlook**. If necessary, sign in as **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Megan's password should be provided by your lab hosting provider.

1. In the Outlook application, select the **Inbox**

1. With the right mouse button select the first email item in the center pane, and in the menu, select **Assign Policy**.

1. A list of retention policies will be displayed.

1. If available, select the **VAT Returns and supporting documents** otherwise select **one Month delete** from the existing policies(just for applying a setting within this exercise).

	  Note: Published retention labels can take seven days to appear in Exchange Online and the mailbox must contain 10 MB of data.

1. Keep **Outlook** open.

You have successfully applied a retention label to an Outlook email.

### Task 5 – Work with retention labels for Outlook folders

In this task, you will assign retention labels to an Outlook folder.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and **Outlook** should be opened. If not open **Outlook** again and sign-in as **Megan Bowen**.

1.  Select right click on the **Inbox** in the left panel

1.  Select **New folder...** and under **Name** enter VAT Returns

1.  Select the **OK** button

1.  Right-click on the newly created **VAT Returns** folder in the left panel

1.  From the menu, select **Properties**

1.  Select the **Policy** tab

1.  If available, set the **Folder Policy** drop-down list to **VAT Returns and supporting documents** otherwise select **5 Year delete** from the existing policies (just for applying a setting within this exercise).

	 Note: Published retention labels can take seven days to appear in Exchange Online and the mailbox must contain 10 MB of data

1. Select the **OK** button

1. Close the Outlook application by selecting the close **X** button in the top-right corner

You have successfully applied a retention label to an Outlook folder, the default retention label for all emails within this folder will be assigned this based on your selection from this subtask.

You have successfully applied a retention label to an Outlook folder.

### Task 6 – Work with retention labels in SharePoint

In this task, you will apply a retention label to a document in a SharePoint document library.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://www.office.com** and log into the Microsoft 365 as **Joni Sherman**.

1. In the Microsoft O365 landing page, select the App launcher icon in the top-left corner (the icon with nine dots), then select **SharePoint** from the sub-menu.
1. If prompted, close the **Welcome to SharePoint Start Page** window.

1. On the SharePoint landing page, select the **Communication site** SharePoint site.

	Note: Type **Communication site** in the search bar and search for it.

1. In the top navigation bar, select the **Documents** tab.

1. Select the **CAS** folder.

1. Within the CAS folder, highlight (but do not select) the **Blog Post preview.docx** document

1. For the highlighted document, select the horizontal **...** button.  Hover over the **More** option.

1. From the expanded menu select, select the **Compliance details** button.

1. A new window will appear.  For **Label Status** the word *None* should appear, select it.  This will open a new browser tab that will allow you to apply a label.

1. If the option is available, set the **Apply label** to **VAT Returns and supporting documents (Retain for 7 years)** and select **Save**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, continue to the next task. Feel free to come back later to this task and try again.

You have successfully applied a retention label to a document in SharePoint.

### Task 7 – Work with retention labels in OneDrive

In this task, you will apply a retention label to a document in OneDrive.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, navigate to **https://www.office.com** and log into Microsoft 365 as **Joni Sherman**.

1. In the Microsoft O365 landing page, select the App Launcher icon in the top-left corner (icon with nine dots), then select **OneDrive** from the sub-menu.

1. Within the OneDrive application, highlight (but do not select) the **Contractor Legal Info.docx**

1. For the highlighted document, select the three vertical **...** button.

1. From the menu select, select the **Details** button.  

1. A side menu will appear on the right. Under **Properties** you should see an **Apply label** option. Select the drop-down menu.

1. If the option is available, set the **Apply Retention Label** to **VAT Returns and supporting documents**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, continue to the next task. Feel free to come back later to this task and try again.

You have successfully applied a retention label to a document in OneDrive.
