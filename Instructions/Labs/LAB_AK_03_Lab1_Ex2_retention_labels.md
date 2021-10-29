# Lab 3 Exercise 2 - Implement Retention Labels

In this exercise, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Sudbury England and has legal obligations to retain finance documents. 

Your finance department has created a retention plan to set retention labels on documents for Value Added Tax (VAT) returns with supporting documents and Credit Card receipts.
 
### Task 1 – Create Retention Labels

In this task, you will create a retention label that can be assigned to documents and emails that contain VAT returns and a retention label that can be applied to Credit Card receipts.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft 365 compliance center as **Joni Sherman**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

4. On the Information governance Page, select **Labels** tab.

5. Select the **+ Create a label** button.

6. On the **Name your retention label page** for the **Name**, **Description for users**, and **Description for admins**, enter the following information:

	- **Name**: VAT Returns and supporting documents
	- **Description for users**: Assign this label to VAT Documents to ensure they are retained for the legal period of seven years.
	- **Description for admins**: VAT returns with seven-year retention.

7. Select the **Next** button.

8. On the **Define retention settings** page, enable the **Retain items for a specific period** setting.

9. For the **Define retention settings** section set the following information:
	- **Retention period**: 7 Years
	- **At the end of the retention period**: Do nothing
	- **Start the retention period based on**: When items were created

10. Select the **Next** button.

11. On the **Review and finish** page, select the **Create label** button.  On the *Your retention label is created* page select **Do Nothing** option and select **Done**.

12. Return yourself to the **Information governance** page on the **Labels** tab.  We will publish labels in a later exercise.

13. Select the **+ Create a label** button

14. On the **Name your retention label** page for the **Name**, **Description for users**, and **Description for admins** enter the following information:
	- **Name**: Credit Card Receipts
	- **Description for users**: This label is auto applied to Credit card receipts with a retention period of three years
	- **Description for admins**: Auto applied retention label Credit for card receipts with three-year retention.

15. Select the **Next** button.

16. For the **Define retention settings** section set the following information:
	- **Retention period**: 3 Years
	- **At the end of the retention period**: Do nothing
	- **Start the retention period based on**: When items were created

17. Select the **Next** button.

18. On the **Review and finish** page, select the **Create label** button. On the *Your retention label is created* page select **Do Nothing** option and then select **Done**.

You have successfully created a retention label for VAT returns with a seven-year retention period and a retention label for Credit Card receipts.

### Task 2 – Publish Retention Labels

Following from Task 1 you will now publish the VAT returns retention label so that the published label will be available for the finance users to apply to the documents in Exchange emails and Sharepoint documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

4. On the **Information governance** Page, select the tab **Labels**.

5. Select the label **VAT Returns and supporting documents**, that you created in Task 1.

6. Select the **Publish labels** icon button.

7. On the **Choose labels to publish** page select the **Next** button.

8. On the **Choose locations** page enable the option **Let me choose specific locations**.

9. Enter the following information:
	- **Exchange email** location - **Status**: Enable
	- **SharePoint sites** location - **Status**: Enable
	- **OneDrive accounts** location - **Status**: Enable
	- **Office 365 groups** location - **Status**: Disable

10. Select the **Next** button.

11. On the **Name your policy** page for **Name** and **Description** enter the following information:

	- **Name**: VAT Returns and supporting documents Retention Label
	- **Description**: VAT Returns and supporting documents Retention label, retention period 3 years, Exchange email and SharePoint site locations.

12. Select the **Next** button.

13. On the **Review your settings** page, select the **Submit** button.  When your policy is created select **Done**.

You have successfully published the retention label for VAT Returns and supporting documents.

### Task 3 – Publish auto-apply Retention Labels

Following from Task 1 you will now auto-apply the Credit Card receipts retention label so that the information is retained.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

4. On the **Information governance** page, select the tab **Labels**.

5. Select the label **Credit Card Receipts**, that you created in Task 1.

6. Select the **Auto-apply a label** icon button.  The Automatically apply a label to content wizard will be displayed.

7. On the **Name your auto-labeling policy** page, for **Name** and **Description** enter the following information:
	- **Name**: Credit Card Receipts auto-applied
	- **Description**: Credit Card Receipts auto-applied retention label, with a retention period of three years for all location

8. Select the **Next** button.

9. On the **Choose the type of content you want to apply this label to** page select the following option for Choose the type of content you want to apply this label to:

	- **Apply label to content that contains sensitive info**

10. Select the **Next** button.

11. On the **Content that contains sensitive info** page, select the following category **Financial**. 

12. Financial templates will then be displayed as results to the right of the template categories panel. 

13. On the Financial templates panel, scroll down through the results and select the **U.K. Financial Data**.

14. Select the **Next** button.

15. On the **Define content that contains sensitive info** page, select the **Next** button.

16. On the **Choose locations to apply the policy** page enable the options for: **Exchange email, OneDrive accounts, SharePoint sites, and Microsoft 365 Groups** and select **Next**.

17. On the **Choose a label to auto-apply** page, select **Next**.

18. On the **Choose a label to auto-apply** page select the **Submit** button.  When the policy is created, select **Done**.

You have successfully published a retention label with auto-apply. Over the next seven days all documents containing credit card details will be automatically labeled with the published label Credit Card Receipts, a retention period of three years will be applied to these items.


### Task 4 – Work with retention labels in Outlook emails

In this task, you will assign retention labels to Outlook emails.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. On the taskbar at the bottom of the page, select the Start button, scroll down and then select **Outlook**. If necessary, sign in as **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Megan's password should be provided by your lab hosting provider.
 
3. In the Outlook application, select the **Inbox**

4. With the right mouse button select the first email item in the center pane, and in the menu, select **Assign Policy**.

5. A list of retention policies will be displayed.

6. As there is some delay when creating retention policies, the policy created in the previous exercise may not be available for selection. If available select the **VAT Returns and supporting documents** otherwise select **one Month delete** from the existing policies. This is just for applying a setting within this exercise, remember it can take a day or more for retention policies to become available in a tenant.

7. Keep **Outlook** open.

You have successfully applied a retention label to an Outlook email.

### Task 5 – Work with retention labels for Outlook folders

In this task, you will assign retention labels to an Outlook folder.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and **Outlook** should be opened. If not open **Outlook** again and sign-in as **Megan Bowen**.

2.  Select right click on the **Inbox** in the left panel

3.  Select **New folder...** and enter: VAT Returns

4.  Right-click on the newly created **VAT Returns** folder in the left panel

5.  From the menu, select **Properties**

6.  Select the **Policy** tab

7.  If available set the **Folder Policy** drop-down list to  **VAT Returns and supporting documents** otherwise select **5 Year delete** from the existing policies (just for applying a setting within this exercise).

8. Select the **OK** button

9. Close the Outlook application by selecting the close **X** button in the top-right corner

You have successfully applied a retention label to an Outlook folder, the default retention label for all emails within this folder will be assigned this based on your selection from this subtask.

You have successfully applied a retention label to an Outlook folder.

### Task 6 – Work with retention labels in SharePoint

In this task, you will apply a retention label to a document in a SharePoint document library.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log into the Microsoft 365 as **Joni Sherman**.

3. In the Microsoft O365 landing page, select the App launcher icon in the top-left corner (the icon with nine dots), then select **SharePoint** from the sub-menu.

4. On the SharePoint landing page, scroll down and select the **Communication site** SharePoint site.

5. In the top navigation bar, select the **Documents** link

6. Select the **CAS** folder

7. Within the CAS folder, highlight (but do not select) the **Blog Post preview.docx** document

8. For the highlighted document, select the vertical **...** button.  Hover over the **More** option.

9. From the expanded menu select, select the **Compliance details** button.

10. A side menu will appear.  For **Label Status** the word *None* should appear, select it.  This will open a new browser tab that will allow you to apply a label.

11. If the option is available, set the **Apply label** to **VAT Returns and supporting documents** and select **Save**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, do not worry, continue to the next task.

    ![sample SharePoint label applied. ](../Media/sharepoint_label.png)

You have successfully applied a retention label to a document in SharePoint.

### Task 7 – Work with retention labels in OneDrive

In this task, you will apply a retention label to a document in OneDrive.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log into Microsoft 365 as **Joni Sherman**.

3. In the Microsoft O365 landing page, select the App Launcher icon in the top-left corner (icon with nine dots), then select **OneDrive** from the sub-menu.

4. Within the OneDrive application, highlight (but do not select) the **Contractor Legal Info.docx**

5. For the highlighted document, select the three vertical **...** button

6. From the menu select, select the **Details** button.  

7. A side menu will appear on the right.  You should see an **Apply label** option, click in it.

8. If the option is available, set the **Apply Retention Label** to **VAT Returns and supporting documents**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, do not worry, continue to the next exercise.

You have successfully applied a retention label to a document in OneDrive.

# Proceed to Exercise 3
