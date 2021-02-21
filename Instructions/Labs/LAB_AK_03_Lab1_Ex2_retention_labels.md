# Exercise 2 - Implement Retention Labels

In the labs of this course, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Sudbury England and has legal obligations to retain finance documents. 
Your finance department has created a retention plan to set retention labels on documents for Value Added Tax (VAT) returns with supporting documents and Credit Card receipts.
 
### Task 1 – Create Retention Labels

In this task, you will create a retention label that can be assigned to documents and emails that contain VAT returns and a retention label that can be applied to Credit Card receipts.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

6. On the Information Governance Page, select **Labels** tab.

7. Select the **+ Create a label** button

8. On the **Name your policy page** for the **Name**, **Description for admins** and **Description for users**, enter the following information:

	- **Name**: VAT Returns and supporting documents
	- **Description for admins**: VAT returns with seven year retention.
	- **Description for users**: Assign this label to VAT Documents to ensure they are retained for the legal period of seven years.

9. Select the **Next** button.

10. On the **Label settings page**, enable the **Retention** setting.

11. For the **When this label is applied to content...** section set the following information:
	- **Retain the content**: Set to enable
	- For this long – 7 – [Years]
	- **What do you want to do after this time?**: Nothing. Leave the content as is.
	- **Retain the content based on**: When it was created

11. Select the **Next** button.

12. On the Review your settings page, select the **Create this label** button.

13. You will be on returned back to the **Information Governance** Page on the **Labels** tab.

14. Select the **+ Create a label** button

15. On the Name your policy page for the **Name**, **Description for admins** and **Description for users**, enter the following information:
	- **Name**: Credit Card Receipts
	- **Description for admins**: Auto applied retention label Credit for card receipts with three year retention.
	- **Description for users**: This label is auto applied to Credit card receipts with a retention period of three years

16. Select the **Next** button.

17. On the **Label settings** page, enable the **retention setting**.

18. For the **When this label is applied to content...** section set the following information:
	- **Yes, I want to retain it**: Set to enable
	- For this long – 3 – Years
	- **What do you want to do after this time?**: Nothing. Leave the content as is.
	- **Retain the content based on**: When it was created

19. Select the **Next** button.

20. On the **Review your settings** page, select the **Create this label** button.

You have successfully created a retention label for VAT returns with a seven year retention period and a retention label for Credit Card receipts.

### Task 2 – Publish Retention Labels

Following from Task 1 you will now publish the VAT returns retention label so that the published label will be available for the finance users to apply to the documents in locations Exchange emails and Sharepoint documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

6. On the **Information Governance** Page, select the tab **Labels**.

7. Select the label **VAT Returns and supporting documents**, that you created in Task 1.

8. Select the **Publish label** button.

10. On the Choose labels to publish page select the **Next** button.

11. On the Choose locations page enable the option **Let me choose specific locations**.

12. Enter the following information:
	- **Exchange email** location - **Status**: Enable
	- **SharePoint sites** location - **Status**: Enable
	- **OneDrive accounts** location - **Status**: Enable
	- **Office 365 groups** location - **Status**: Disable

13. Select the **Next** button.

14. On the **Name your policy** page for **Name** and **Description** enter the following information:

	- **Name**: VAT Returns and supporting documents Retention Label
	- **Description**: VAT Returns and supporting documents Retention label, retention period 3 years, Exchange email and SharePoint site locations.

15. Select the **Next** button.

16. On the **Review your settings** page, select the **Publish labels** button.

You have successfully published the retention label for VAT Returns and supporting documents.

### Task 3 – Publish auto-apply Retention Labels

Following from Task 1 you will now auto-apply the Credit Card receipts retention label so that the 

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

6. On the **Information Governance** page, select the tab **Labels**.

7. Select the label **Credit Card Receipts**, that you created in Task 1.

8. Select the **Auto-apply a label** button

9. The Automatically apply a label to content wizard will be displayed.

9. On the **Choose label to auto-apply** page, select the **Next** button.

10. On the **Choose conditions** page select the following option for Choose the type of content you want to apply this label to:

	- **Apply label to content that contains sensitive info**

11. Select the **Next** button.

12. On the Select from a template section, select the following template category **Financial**. 

13. Financial templates will then be displayed as results to the right of the template categories panel. 

14. On the Financial templates panel, scroll down through the results and select the **U.K. Financial Data**.

15. Select the **Next** button.

16. On the settings page, select the **Next** button.

17. On the **Name your policy** page, for **Name** and **Description** enter the following information:
	- **Name**: Credit Card Receipts auto-applied
	- **Description**: Credit Card Receipts auto-applied retention label, with a retention period of three years for all location

18. On the **Choose locations** page select the option: **All locations. Includes content in Exchange email, OneDrive, and SharePoint documents**.

19. On the **Review your settings** page select the **Auto-apply** button.

You have successfully published a retention label with auto-apply. Over the next seven days all documents containing credit card details will be automatically labeled with the published label Credit Card Receipts, a retention period of three years will be applied to these items.

### Task 4 – Manage Document Lifecycle with SharePoint

Your organization has implemented a yearly review cycle that all approved documents will have a retention period of one year. You will set up a SharePoint document library for the approval process.

1. Log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log Microsoft 365 as **MOD Administrator**.

5. In the Microsoft O365 landing page, select the App launcher icon in the top-left corner with nine dots, then select **SharePoint** from the submenu.

6. On the SharePoint landing page, scroll down and select the **Communication site** SharePoint site.

7. In the top navigation bar, select the **Documents** link.

8.  On the **Documents** library, in the top-right corner select the **Settings** cogwheel.

9. A Settings tab will display, select **Library settings**.

10. On the Settings page within the **General settings**, select **Versioning settings**.

11. On the **Versioning Settings** page within the **Content Approval**, set **Require content approval for submitted items** to **Yes**

12. At the bottom of the form select the **OK** button.

You have successfully configured a SharePoint document library for the approval process.

### Task 5 - Mapping a SharePoint Managed Property 

Following from the previous task, you will now map the approval column from a SharePoint document library to a managed property field.

1. You should still be logged into your Client 2 VM (LON-CL2) as the **lon-cl2\admin** account, and you should be logged into Microsoft 365 as **MOD Administrator**. 

2. In **Microsoft Edge**, navigate to **https://admin.microsoft.com**.

3. On the left navigation, select the **... Show all**.

4. Navigate down the left navigation menu and select **SharePoint**.

5. In the **SharePoint admin center**, on the left side navigation select **More features**.

6. On the **More features page**, in the center page under **Search**, select the **Open** button.

7. In the **Search page**, select **Manage Search Schema**.

8. In the **Managed Property** filter enter: RefinableString00

9. Select the Apply button, which is a Green arrow pointing right.

10. After a short duration, in the filter results select the **RefinableString00** link.

11. Scroll to the bottom of the page.

12. Select the **Add a mapping** button.

13. A model window will appear, if the window is not displayed scroll to the top of the page until the crawled property selection window is fully displayed.

14. Enter the following for **Search for a crawled property name**: ows__ModerationStatus

15. Select the **Find** button.

16. Within the **Select a crawled property** results, select **ows__ModerationStatus**

17. Select the **OK** button

18. Scroll to the bottom of the page and select the **OK** button

You have successfully updated a SharePoint managed property, mapping the approval field to the RefinableString00 managed property. 


### Task 6 - Create and auto-apply a retention label that contains a managed property

You will create a retention label and publish using auto-apply. The auto-applied Retention label will be configured to apply to the managed properties configured in the previous task.

1. You should still be logged into your Client 2 VM (LON-CL2) as the **lon-cl2\admin** account, and you should be logged into Microsoft 365 as **MOD Administrator**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

5. On the **Information Governance** Page, select the **Labels** tab.

6. Select the **+ Create a label** button.

7. On the **Name your policy** page for the **Name**, **Description for admins** and **Description for users**, enter the following information:

	- **Name**: Published document retention
	- **Description for admins**: Published documents with one year retention.
	- **Description for users**: This label will be auto applied to published documents to ensure they are retained for business requirements of one years.

8. Select the **Next** button.

9. On the **Label settings** page, enable the **Retention** setting.

11. For the **When this label is applied to content...** section set the following information:
	- **Yes, I want to retain it**: Set to enable
	- For this long – 1 – Years
	- **What do you want to do after this time?**: Nothing. Leave the content as is.
	- **Retain the content based on**: When it was created

12. Select the **Next** button.

13. On the **Review your settings** page select **Create this label**.

14. You will be returned back to the **Information Governance** Page on the **Labels** tab.

15. Select the label **Published document retention**, that you created.

16. Select the **Auto-apply a label** button

17. The Automatically apply a label to content wizard will be displayed.

18. On the **Choose label to auto-apply** page, select the **Next** button.

19. On the **Choose conditions** page select the following option for Choose the type of content you want to apply this label to:

	- **Apply label to content that contains specific words or phrases, or properties**

20. Select the **Next** button.

21. In the Keyword query editor, enter the following information

    RefinableString00:0

22. Select the **Next** button.

23. On the **Name your policy** page, for **Name** and **Description** enter the following information:
	- **Name**: Published document retention auto-applied
	- **Description**: Published documents within all locations will have this label automatically applied.

23. On the **Choose locations** page select the option: **All locations. Includes content in Exchange email, OneDrive, and SharePoint documents**.

27. On the **Review your settings** page select the **Auto-apply** button.

You have successfully created and auto-applied retention label that contains managed properties.
All existing and future documents that are published in SharePoint will have the label, "Published document retention" applied to them and will have a retention period of one year set.

The auto-apply label process can take up to seven days.

### Task 7 – Work with retention labels in Outlook emails

In this task, you will assign retention labels to Outlook emails.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. On the taskbar at the bottom of the page, select the Start button, scroll down and then select **Outlook**. If necessary, sign in as **Megan Bowen**.
 
3. In the Outlook application, select the **Inbox**

4. With the right mouse button select the first email item in the center pane, and in the menu, select **Assign Policy**.

5. A list of retention policies will be displayed.

6. As there is some delay when creating retention policies, the policy created in the previous exercise may not be available for selection. If available select the **VAT Returns and supporting documents** otherwise select **one Month delete** from the existing policies. (just for the purpose of applying a setting within this exercise).

7. Keep **Outlook** open.

You have successfully applied a retention label to an Outlook email.

### Task 8 – Work with retention labels for Outlook folders

In this task, you will assign retention labels to an Outlook folder.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and **Outlook** should be opened. If not open **Outlook** again and sign-in as **Megan Bowen**.

2.  Select right click on the **Inbox** in the left panel

3.  Select **New folder** and enter: VAT Returns

4.  Select right click on the newly created **VAT Returns** folder in the left panel

5.  From the menu, select **Properties**

6.  Select the **Policy** tab

7.  If available set the **Folder Policy** drop down list to  **VAT Returns and supporting documents** otherwise select **5 Year delete** from the existing policies (just for the purpose of applying a setting within this exercise).

8. Select the **OK** button

9. Close the Outlook application by selecting the close **X** button in the top-right corner

You have successfully applied a retention label to an Outlook folder, the default retention label for all emails within this folder will be assigned this based on your selection from this subtask.

You have successfully applied a retention label to an Outlook folder.

### Task 9 – Work with retention labels in SharePoint

In this task, you will apply a retention label to a document in a SharePoint document library.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log into the Microsoft 365 as **Joni Sherman**.

5. In the Microsoft O365 landing page, select the App launcher icon in the top-left corner with nine dots, then select **SharePoint** from the submenu.

12. On the SharePoint landing page, scroll down and select the **Communication site** SharePoint site.

13. In the top navigation bar, select the **Documents** link

14. Select the **CAS** folder

15. Within the CAS folder, highlight (but do not select) the **Blog Post preview.docx** document

16. For the highlighted document, select the **...** button

17. From the menu select, select the **Details** button

18. A side menu will appear on the right.

19. If the option is available, set the **Apply Retention Label** to **VAT Returns and supporting documents**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, do not worry, continue to the next sub task.

You have successfully applied a retention label to a document in SharePoint.

### Task 10 – Work with retention labels in OneDrive

In this task, you will apply a retention label to a document in OneDrive.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, navigate to **https://www.office.com** and log into Microsoft 365 as **Joni Sherman**.

5. In the Microsoft O365 landing page, select the App Launcher icon in the top-left corner with nine dots, then select **OneDrive** from the submenu.

6.  Within the OneDrive application, highlight (but do not select) the **Contractor Legal Info.docx**

7. For the highlighted document, select the **...** button

8. From the menu select, select the **Details** button

9. A side menu will appear on the right.

10. If the option is available, set the **Apply Retention Label** to **VAT Returns and supporting documents**. As it can take some time for retention labels to be published you may not have the option available immediately, if it is not available, do not worry, continue to the next exercise.

You have successfully applied a retention label to a document in OneDrive.

# Proceed to Exercise 3
