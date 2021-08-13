# Exercise 5 - Manage Sensitivity Labels

In this lab you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. 
Your organization is based in Rednitzhembach, Germany and is currently implementing a sensitivity plan to ensure that all employee documents in the HR department have been marked with a sensitivity label as part of your organizations information protection policies.

### Task 1 Enable support for sensitivity labels

In this task, you will install the MSOnline module and the SharePoint Online PowerShell module and enable support for sensitivity labels on your tenant.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. Open an elevated PowerShell window by selecting the start menu with the right mouse button and then select **Windows PowerShell** and run as administrator.

3. Confirm the **User Account Control** window with **Yes** and press Enter.

4. Enter the following cmdlet to install the latest MS Online PowerShell module version:

   `Install-Module -Name MSOnline`

5. Confirm the Untrusted repository security dialog with **Y** for Yes and press Enter.  This may take many seconds to complete processing.

6. Enter the following cmdlet to install the latest SharePoint Online PowerShell module version:

    `Install-Module -Name Microsoft.Online.SharePoint.PowerShell`

7. Confirm the Untrusted repository security dialog with **Y** for Yes and press Enter.

8. Enter the following cmdlet to connect to the MS Online service:

    `Connect-MsolService`

9. In the **Sign in to your account** form, sign in as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

10. After signing in, select the PowerShell window.

11. Enter the following cmdlet to get the domain:

    `$domain = get-msoldomain`

12. Enter the following cmdlet to create the SharePoint admin url:

    `$adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"`

13. Enter the following cmdlet to sign in to the SharePoint Online admin center:

    `Connect-SPOService -url $adminurl`

14. In the **Sign in to your account** form, sign in as **MOD Administrator**. admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

15. After signing in, select the PowerShell window.

16. Enter the following cmdlet to enable support for sensitivity labels:

    `Set-SPOTenant -EnableAIPIntegration $true`

17. Confirm the changes with **Y** for Yes and press Enter.

18. Close the PowerShell window.

You have successfully enabled support for sensitivity labels with Teams and SharePoint sites.

### Task 2 – Create Sensitivity Labels

In this task, your HR department has requested a sensitivity label to apply to HR employee documents. You will create a sensitivity label for Internal documents and a sublabel for the HR department.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

3. In the **Compliance Center**, in the left navigation pane, select **Information protection**.  

4. On the Information protection page, under the **Labels** tab select **+ Create a label**.

5. The **New sensitivity label** wizard will start. On the **Name and create a tooltip for your label** page for the **Name**, **Description for admins** and **Description for users**, enter the following information:

	- **Name**: Internal
	- **Display name**: Internal
	- **Description for users**: Internal sensitivity label.
	- **Description for admins**: Internal sensitivity label for Contoso.

6. Select **Next**.

7. On the **Define the scope for this label** page, select the option **Files & emails**.

8. Select **Next**.

9. On the **Choose protection settings for files & emails** page, select **Next**.

10. On the **Auto-Labeling for files and emails** page, select **Next**.

11. On the **Define protection settings for groups & sites** page, select **Next**.

12. On the **Auto-labeling for database columns** page, select **Next**. 

13. On the **Review your settings and finish** page, select **Create label**.

14. The label will be created and when complete a message will display: **Your label was created**

15. Select **Done**.

16. On the Information protection page, highlight (without selecting) the newly created **Internal** label and select the vertical **...**.

17. Select the **+ Add sub label** from the drop-down menu.

18. The **New sensitivity label** wizard will start. On the **Name and create a tooltip for your label** page for the **Name**, **Description for admins** and **Description for users**, enter the following information:

   - **Name**: Employee data (HR)
   - **Display name**: Employee data (HR)
   - **Description for users**: This HR label is the default label for all specified documents in the HR Department.
   - **Description for admins**: This label is created in consultation with Ms. Jones (Head of HR department). Contact her, when you want to chance settings of the label.

19. Select **Next**.

20. On the **Define the scope for this label** page, select the option **Files & emails**.

21. Select **Next**.

22. On the **Define protection settings for files and emails** page, select the **Encrypt files and emails** option.

23. Select **Next**.

24. Select **Configure encryption settings**.

25. Enter the following information into the encryption settings:

   - **Assign permissions now or let users decide?**: Assign permissions now
   - **User access to content expires**: Never
   - **Allow offline access**: Only for a number of days
   - **Users have offline access to the content for this many days**: 15

26. Select the **Assign permissions** link

27. On the Assign permissions side menu, select the **Add any authenticated users**.

28. Select **Save**.

29. On the **Encryption** page, select **Next**.

30. On the **Auto-labeling for files and emails** page, select **Next**.

31. On the **Define protection settings for groups and sites** page, select **Next**.

32. On the **Auto-labeling for database columns** page, select **Next**. 

33. On the **Review your settings and finish** page, select **Create label**.

34. The label will be created and when complete a message will display **Your label was created**.

35. Select **Done**.

You have successfully created a sensitivity label for your organizations internal policies and a sensitivity sublabel for the Human Resources (HR) department.

### Task 3 – Publish Sensitivity Labels

You will now publish the Internal and HR sensitivity label so that the published sensitivity labels will be available for the HR users to apply to their HR documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.  Sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

2. In **Microsoft Edge**, the Microsoft 365 Compliance center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Information protection**. 

4. On the **Information protection** page, on the **Labels** tab, select **Publish label**.

5. The publish sensitivity labels wizard will start.

6. On the **Choose sensitivity labels to publish** page, select the **Choose sensitivity labels to publish** link.

7. A side bar called **Sensitivity labels to publish** will appear on the right.

8. Select the **Internal** and **Internal/Employee Data (HR)** checkboxes.

9. Select **Add**.

10. On the **Choose sensitivity labels to publish** page, select **Next**.

11. On the **publish to users and groups page**, select **Next**.

12. On the **Policy settings** page, select **Next**.

13. On the **Name your policy** page, enter the following information:

   - **Name**: Internal HR employee data
   - **Enter a description for your sensitivity label policy**: This HR label is to be applied to internal HR employee data.

14. Select **Next**.

15. On the **Review and finiah** page, select **Submit**.

16. The policy will be created and when complete a message will display **New policy created**.

17. Select **Done**.

You have successfully published the Internal and HR sensitivity labels. Note that it can take up to 24 hours for changes to replicate to all users and services.

### Task 4 – Work with Sensitivity Labels

In this task, you will create sensitivity labels in Word and Outlook emails. The document created will be stored in OneDrive and sent to an HR employee via email.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. Select the address bar and navigate to **https://portal.office.com**.

3. If a **Get your work done with Office 365** message is shown, close it with the **X** in the upper right corner.

4. Select the Microsoft Word symbol from the left side pane to open Word Online.

5. Select **New blank document** to create a new document.

6. If a **Your privacy options** message is shown, close it with selecting **Close**.

7. Enter the following contents into the word document: 

   - Important HR employee document.

8. Select **Sensitivity** from the top pane top open the dropdown menu. Select **Internal**  to apply the label.
    Be aware, the script you ran in task 1 of this exercise activated sensitivity labels in Word for your tenant.  It can sometimes take an hour for that activation to be realized in Microsoft Word online.  If you don't see the Sensitivity label menu in Word, you may need to return to this lab later or make sure you properly completed task 1 of this exercise.
    ![Sensitivity label. ](../Media/word_label.png)

9. Select the **Document - Saved** in the upper left of the window, enter **HR Document** as the File Name and press Enter key.

10. Close the tab to return to the Word Online tab. Select the Outlook symbol from the left side pane to open Outlook on the web.

11. If a welcome message is shown, close it with selecting the **X**.

12. In Outlook on the web, select **New message** from the upper left of the window.

13. In the To field enter the name: **Allan** and select **Allan Deyoung** from the drop-down list.

14. In the subject field, enter: **Employee data for HR**

15. Within the email message (the large content panel at the bottom of the page), insert the following message: 

    Dear Mr. Deyoung, 

    Please find attached the important HR employee document. 

	Kind regards,

	Joni Sherman

16. Select the paperclip symbol from the bottom menu and select the **HR Document.docx** below **Suggested attachments** to attach the document.

17. Select **Send** to send out the email message with attached document.

18. Leave the browser window open.

You have successfully created an HR Word document with a sensitivity label, which was saved onto your OneDrive. You then emailed to document to an HR staff member.

You have successfully created an HR Word document with a sensitivity label, which was saved onto your OneDrive. You then emailed to document to an HR staff member where the email was also set with a sensitivity label.

### Task 5 – Configure Auto Labeling

In this task, you will create a Sensitivity Label that will auto label documents and emails found to contain information related to the European General Data Protection Regulation (GPDR).

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the **Microsoft 365 compliance** center, in the left navigation pane, select **Information protection**.  

4. On the Information protection page, highlight (without selecting) the existing **Internal** label, and select the three dots.

5. Select the **+ Add sub label** menu item.

6. The **New sensitivity label** wizard will start. On the **Name and create a tooltip for your label** page, enter the following information:

   - **Name**: GDPR Germany
   - **Display name**: GDPR Germany
   - **Description for users**: This document or email contains data related to the European General Data Protection Regulation (GPDR) for the region Germany.
   - **Description for admins**: This label is auto applied to German GDPR documents.

7. Select **Next**.

8. On the **Define the scope for this label** page, select the option **Files & emails**.

8. Select **Next**.

9. On the **Choose protection settings for files and emails** page, select **Next**.

10. On the **Auto-labeling for files and emails** page, set the **Auto-labeling for files and emails** to enabled.

11. In the **Detect content that matches these conditions** section, select **+Add condition** and then select **Content contains**.

12. In **Content contains** section select the **Add** text and then select **Sensitive info types**.

13. A **Sensitive info types** panel will be displayed on the right.

14. In the **Search for sensitive info types** search panel, enter the following information: 

    `German`

15. Press the enter button, the results will display sensitivity info types related to Germany.

16. Press the **Select all** check box.

17. Select **Add**.

18. Select **Next**.

19. On the **Define protection settings for groups and sites** page, select **Next**.

20. On the **Auto-labeling for database columns** page, select **Next**. 

21. On the **Review your settings and finish** page, select **Create label**.

22. The label will be created and when complete a message will display: **Your label was created**.

23. Select **Done**.

24. On the **Information protection** page, select **Publish labels**.

25. The Publish sensitivity labels wizard will start.

26. On the **Choose sensitivity labels to publish** page, select the **Choose sensitivity labels to publish link**.

27. A side bar called **Sensitivity labels to publish** will appear on the right.

28. Select the **Internal** and **Internal/GDPR Germany** checkbox.

29. Select **Add**.

30. On the **Choose sensitivity labels to publish** page, select **Next**.

31. On the **Publish to users and groups** page, select **Next**.

32. On the **Policy settings** page, select **Next**.

33. On the **Name your policy** page, enter the following information:

   - **Name**: GDPR Germany policy
   - **Enter a description for your sensitivity label policy**: This auto apply sensitivity labels policy is for the GDPR region of Germany.

34. Select **Next**.

35. On the **Review and finish** page, select **Submit**.

36. The policy will be created and when complete a message will display, **New policy created**.

37. Select **Done**.

You have successfully created and published an auto apply sensitivity label for GDPR documents in the region Germany.

Be aware that it can take up to 24 hours for auto applied sensitivity labels to be applied, this duration will be longer when applied to more than 25,000 documents (that is, the daily limit).


## You have completed the lab.
