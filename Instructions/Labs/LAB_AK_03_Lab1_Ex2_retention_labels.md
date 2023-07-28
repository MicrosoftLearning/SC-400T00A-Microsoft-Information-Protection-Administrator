---
lab:
    title: 'Exercise 2 - Implement Retention Labels'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 2 - Implement Retention Labels

In this exercise, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Sudbury England and has legal obligations to retain finance documents.

Your finance department has created a retention plan to set retention labels on documents for Value Added Tax (VAT) returns with supporting documents and Credit Card receipts.

## Task 1 – Create Retention Labels

In this task, you will create a retention label that can be assigned to documents and emails that contain VAT returns and a retention label that can be applied to Credit Card receipts.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, in the left navigation pane, expand **Data lifecycle management** then select **Microsoft 365**.

1. On the **Data lifecycle management** page select the **Labels** tab then select **+ Create a label**.

1. On the **Name your retention label** page input:

    - **Name**: VAT Returns and supporting documents
    - **Description for users**: Assign this label to VAT Documents to ensure they are retained for the legal period of seven years.
    - **Description for admins**: VAT returns with seven-year retention.

1. Select **Next**.

1. On the **Define label settings** page, choose the **Retain items forever or for a specific period** then select **Next**.

1. On the **Define the period** input:

    - **How long is the period?**: 7 Years
    - **When should the period begin?**: When items were created

1. Select **Next**.

1. On the **Choose what happens after the retention period** page select **Deactivate retention settings** then select **Next**.

1. On the **Review and finish** page select  **Create label**.

1. On the **Your retention label is created** page select the option to **Do Nothing** then select **Done**. The label will be published later in the Exercises.

1. On the **Data lifecycle management** page select **+ Create a label**.

1. On the **Name your retention label** input:

    - **Name**: Credit Card Receipts
    - **Description for users**: This label is auto applied to Credit card receipts with a retention period of three years.
    - **Description for admins**: Auto applied retention label for Credit card receipts with three-year retention.

1. Select **Next**.

1. On the **Define label settings** page select **Retain items forever or for a specific period** then select **Next**.

1. On the **Define the period** page input:

    - **Retain items for**: Select the drop down list and select **Custom**. Enter 3 for Years.
    - **Start the retention period based on**: When items were created.

1. Select **Next**.

1. On the **Choose what happens after the retention period** page select **Deactivate retention settings** then select **Next**.

1. On the **Review and finish** page select **Create label**.

1. On the **Your retention label is created** page select **Do Nothing** then select **Done**.

You have successfully created a retention label for VAT returns with a seven-year retention period and a retention label for Credit Card receipts with a three-year retention.

## Task 2 – Publish Retention Labels

Following from Task 1 you will now publish the VAT returns retention label so that the published label will be available for the finance users to apply to the documents in Exchange emails and Sharepoint documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, in the left navigation pane, expand **Data lifecycle management** then select **Microsoft 365**.

1. On the **Data lifecycle management** page select the tab **Labels**.

1. Select the label **VAT Returns and supporting documents** that was created in Task 1.

1. Select the **Publish labels** icon button (next to the pencil).

1. On the **Choose labels to publish** page select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Static** then select **Next**.

1. On the **Choose where to publish labels** page select **Let me choose specific locations** and enable:

    - **Exchange mailboxes**
    - **SharePoint classic and communication sites**
    - **OneDrive accounts**
    - Disable **Microsoft 365 Group mailboxes & sites**

1. Select **Next**.

1. On the **Name your policy** input:

    - **Name**: VAT Returns and supporting documents Retention Label
    - **Description**: VAT Returns and supporting documents Retention label, retention period 3 years, Exchange email and SharePoint site locations.

1. Select **Next**.

1. On the **Finish** page select **Submit**.  

1. On the **Your retention label was published** page select **Done**.

You have successfully published the retention label for VAT Returns and supporting documents.

## Task 3 – Publish auto-apply Retention Labels

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

1. On the **Choose the type of content you want to apply this label to** page select  **Apply label to content that contains sensitive info** then select **Next**.

1. On the **Content that contains sensitive info** page, select the category **Financial**.

1. Financial templates will then be displayed under Templates. Scroll down and select the **U.K. Financial Data** template then select **Next**.

1. On the **Define content that contains sensitive info** page select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page, select the **Static** item then select **Next**.

1. On the **Choose locations to apply the policy** page, turn **On** the options for:

    - **Exchange mailboxes**
    - **SharePoint classic and communication sites**
    - **OneDrive accounts**
    - **Microsoft 365 Group mailboxes & sites**

1. Select **Next**.

1. On the **Choose a label to auto-apply** page, select **Next**.

1. On the **Decide whether to test or run your policy**, select **Turn on policy** then select **Next**.

1. On the **Review and finish** page, select **Submit**.  When the policy is created, select **Done**.

1. Sign out of Joni's account by selecting her image in the top, right hand corner and selecting **Sign out**.

You have successfully published a retention label with auto-apply. Over the next seven days all documents containing credit card details will be automatically labeled with the published label Credit Card Receipts, a retention period of three years will be applied to these items.

## Task 4 – Work with retention labels in Outlook emails

In this task, you will assign retention labels to Outlook emails.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://outlook.office.com/** and login with **Megan Bowen**'s account.

1. In Megan's inbox, select the first email with the right mouse button, then select **Advanced actions > Assign policy > VAT Returns and supporting documents**. If the newly created label is not available, select **1 Month Delete** for this exercise.

    >**Note**: Published retention labels can take seven days to appear in Exchange Online and the mailbox must contain 10 MB of data.

1. Keep **Outlook** window open.

You have successfully applied a retention label to an Outlook email.

## Task 5 – Work with retention labels for Outlook folders

In this task, you will assign retention labels to an Outlook folder.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account. Your Microsoft Edge browser window with **Outlook** should still be open, and you should still be logged in as **Megan Bowen**.

1. Select right click on the **Inbox** in the left panel

1. Select **Create new subfolder**.

1. A cursor with a blank field should appear to ender in the new file name. Enter _VAT Returns_ in this field then select **Save**.

1. Right-click the newly created **VAT Returns** folder in the left panel and select **Assign policy > VAT Returns and supporting documents**. If the newly created label is not available, select **5 Year Delete** for this exercise.

    >Note: Published retention labels can take seven days to appear in Exchange Online and the mailbox must contain 10 MB of data.

1. Log out of Megan's account by selecting her picture in the top right and selecting **Sign out**.

You have successfully applied a retention label to an Outlook folder, the default retention label for all emails within this folder will be assigned this based on your selection from this subtask.

You have successfully applied a retention label to an Outlook folder.

## Task 6 – Work with retention labels in SharePoint

In this task, you will apply a retention label to a document in a SharePoint document library.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://www.office.com** and log into Microsoft 365 as **Joni Sherman**.

1. In the Microsoft 365 landing page, select the App launcher icon in the top-left corner (the icon with nine dots), then select **SharePoint** from the sub-menu.
1. If prompted, close the **Welcome to SharePoint Start Page** window.

1. On the SharePoint landing page, search for _Communication site_ then select **Communication site** from the search results.

1. In the top navigation bar, select the **Documents** tab.

1. Select the **CAS** folder.

1. Within the CAS folder, highlight (but do not select) the **Blog Post preview.docx** document

1. For the highlighted document, select the horizontal ellipses, **...**, button, then select **More > Compliance details**.

1. A new window displaying the **Compliance details** for the document opens. For **Label Status** select **None** to open the **Apply Label** window.

1. If the option is available, set the **Apply label** to **VAT Returns and supporting documents (Retain for 7 years)** then select **Save**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, continue to the next task. Feel free to come back later to this task and try again.

You have successfully applied a retention label to a document in SharePoint.

## Task 7 – Work with retention labels in OneDrive

In this task, you will apply a retention label to a document in OneDrive.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, navigate to **https://www.office.com** and log into Microsoft 365 as **Joni Sherman**.

1. In the Microsoft 365 landing page, select the App Launcher icon in the top-left corner (icon with nine dots), then select **OneDrive** from the sub-menu.

1. Select **My files** from the left navigation pane, then select the checkbox to the left of **Contractor Legal Info.docx**.

1. For the highlighted document, select select the horizontal ellipses, **...**, button then select **Details**.

1. On the flyout page on the right, under **Properties** you should see an option to **Apply label**. Select **Choose a label** to expand a dropdown, then select **VAT Returns and supporting documents** if available.

    >**Note**: As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, continue to the next task. Feel free to come back later to this task and try again.

You have successfully applied a retention label to a document in OneDrive.
