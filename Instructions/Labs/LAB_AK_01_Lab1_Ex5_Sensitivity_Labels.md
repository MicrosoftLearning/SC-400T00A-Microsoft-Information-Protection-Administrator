# Exercise 5 - Manage Sensitivity Labels

In the labs of this course, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. 
Your organization is based in Rednitzhembach Germany and is currently implementing a sensitivity plan to ensure that all employee documents in the HR department have been marked with a sensitivity label as part of your organizations information protection policies.

### Task 1 Enable support for sensitivity labels

In this task, you will install the MSOnline module and the SharePoint Online PowerShell module and enable support for sensitivity labels on your tenant.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. Open an elevated PowerShell window by selecting the start menu with the right mouse button and then select **Windows PowerShell (Admin)**.

3. Confirm the **User Account Control** window with **Yes**.

4. Enter the following cmdlet to install the latest MS Online PowerShell module version:

    Install-Module -Name MSOnline

5. Confirm the Untrusted repository security dialog with **Y** for Yes.

6. Enter the following cmdlet to install the latest SharePoint Online PowerShell module version:

    Install-Module -Name Microsoft.Online.SharePoint.PowerShell

7. Confirm the Untrusted repository security dialog with **Y** for Yes.

8. Enter the following cmdlet to connect to the MS Online service:

    Connect-MsolService

9. In the **Sign in to your account** form, sign in as **Joni Sherman**.

10. After signing in, select the PowerShell window.

11. Enter the following cmdlet to get the domain:

    $domain = get-msoldomain

12. Enter the following cmdlet to create the SharePoint admin url:

    $adminurl = "https://" + $domain.Name.split('.')[0] + "-admin.sharepoint.com"

13. Enter the following cmdlet to sign in to the SharePoint Online admin center:

    Connect-SPOService -url $adminurl

14. In the **Sign in to your account** form, sign in as **MOD Administrator**.

15. After signing in, select the PowerShell window.

16. Enter the following cmdlet to enable support for sensitivity labels:

    Set-SPOTenant -EnableAIPIntegration $true

17. Confirm the changes with **Y** for Yes. 

18. Close the PowerShell window.

You have successfully enabled support for sensitivity labels with Teams and SharePoint sites.


### Task 2 – Create Sensitivity Labels

In this task, your HR department has requested a sensitivity label to apply to HR employee documents. You will create a sensitivity label for Internal documents and a sublabel for the HR department.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the **Compliance Center**, in the left navigation pane, select **... Show all** and then select **Information Protection**.  

4. On the Information protection page, select **+ Create a label**.

5. The **New sensitivity label** wizard will start. On the **Name & description** page for the **Name**, **Description for admins** and **Description for users**, enter the following information:

	- **Name**: Internal
	- **Display name**: Internal
	- **Description for users**: Internal sensitivity label.
	- **Description for admins**: Internal sensitivity label.

6. Select **Next**.

7. On the **Scope** page, select the option **Files & emails**.

8. Select **Next**.

9. On the **Files & email** page, select **Next**.

10. On the **Auto-Labeling** page, select **Next**.

11. On the **Groups & sites** page, select **Next**.

12. On the **Azure Purview assets (preview)** page, select **Next**. 

13. On the **Finish** page, select **Create label**.

14. The label will be created and when complete a message will display **Your label was created**

15. Select **Done**.

16. On the Information protection page, highlight (without selecting) the newly created **Internal** label, and select the three dots.

17. Select the **+ Add sub label** menu item.

18. The **New sensitivity label** wizard will start. On the **Name & description** page for the **Name**, **Description for admins** and **Description for users**, enter the following information:

   - **Name**: Employee data (HR)
   - **Display name**: Employee data (HR)
   - **Description for users**: This HR label is the default label for all specified documents in the HR Department.
   - **Description for admins**: This label is created in consultation with Ms. Jones (Head of HR department). Please contact her, when you want to chance settings of the label.

19. Select **Next**.

20. On the **Scope** page, select the option **Files & emails**.

21. Select **Next**.

22. On the **Files & email** page, select the **Encrypt files and emails** option

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

29. On the Encryption page, select **Next**.

30. On the **Auto-Labeling** page, select **Next**.

31. On the **Groups & sites** page, select **Next**.

32. On the **Azure Purview assets (preview)** page, select **Next**. 

33. On the **Finish** page, select **Create label**.

34. The label will be created and when complete a message will display **Your label was created**.

35. Select **Done**.

You have successfully created a sensitivity label for your organizations internal policies and a sensitivity sublabel for the HR department.

### Task 3 – Publish Sensitivity Labels

You will now publish the Internal and HR sensitivity label so that the published sensitivity labels will be available for the HR users to apply to their  HR documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **... Show all** and then select **Information protection**. 

4. On the **Information protection** page, select **Publish labels**.

5. The publish sensitivity labels wizard will start.

6. On the **Choose labels to publish** page, select the **Choose sensitivity labels to publish link**.

7. A side bar called **Sensitivity labels to publish** will appear on the right.

8. Select the **Internal** and **Internal/Employee Data (HR)** checkboxes.

9. Select **Add**.

10. On the **Choose labels to publish** page, select **Next**.

11. On the **publish to users and groups page**, select **Next**.

12. On the **Policy settings** page, select **Next**.

13. On the **Name & Description** page, enter the following information:

   - **Name**: Internal HR employee data
   - **Enter a description for your sensitivity label policy**: This HR label is to be applied to internal HR employee data.

14. Select **Next**.

15. On the **Review your settings** page, select **Submit**.

16. The policy will be created and when complete a message will display **New policy created**.

17. Select **Done**.

You have successfully published the Internal and HR sensitivity labels. Note that it can take up to 24 hours for changes to replicate to all users and services.

### Task 4 – Work with Sensitivity Labels

In this exercise, you will create sensitivity labels in Word and Outlook emails. The document created will be stored in OneDrive and sent to an HR employee via email.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. Within the Start bar, select **Word**.

3. Within the Word application, select **Blank document**.

4. Enter the following contents into the word document: 

   - Important HR employee document.
    
5. In the menu, select **File**, then select **Save**, then select **OneDrive**.

6. In the **Enter file name here** set the file name to: **HR Document**.

7. Select **Save**.

8. At the top of the page, select the menu ribbon **Home**, within the center of the ribbon menu, select **Sensitivity**.

9. Select the Label **Internal** and the sub menu **Employee data (HR)**. 

10. Select the **File** menu, select the **Share** sub menu item.

11. A Send link dialogue will be displayed.

12. Select **Send a copy**, and in the menu select **Word Document**.

13. The **Outlook** application will start.

14. Maximize the email message window.

15. Select the **Message** menu item.

16. If the **Message** menu item **Sensitivity** is not visible, select the three dots **...**

17. Select the **Sensitivity** menu, select **Internal** and select  **Employee data (HR)**. 

18. In the To field enter the name: **Allan Deyoung**.

19. Select **Allan Deyoung** from the drop-down list. 

20. Within the email message (the large content panel at the bottom of the page), insert the following message: 


    Dear Mr. Deyoung, 

    Find attached the important HR employee document. 

	Kind regards,

	Joni Sherman

21. Select **Send**.

22. Close the **Outlook** application

You have successfully created an HR Word document with a sensitivity label, which was saved onto your OneDrive. You then emailed to document to an HR staff member where the email was also set with a sensitivity label.

### Task 4 – Configure Auto Labeling

In this task, you will create a Sensitivity Label that will auto label documents and emails found to contain information related to the European Data Protection Law (GPDR).

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the **Compliance Center**, in the left navigation pane, select **... Show all** and then select **Information Protection**.  

4. On the Information protection page, highlight (without selecting) the existing **Internal** label, and select the three dots.

5. Select the **+ Add sub label** menu item.

6. The **New sensitivity label** wizard will start. On the **Name & description** page, enter the following information:

   - **Name**: GDPR Germany
   - **Display name**: GDPR Germany
   - **Description for users**: This document or email contains data related to the European Data Protection Law (GPDR) for the region Germany.
   - **Description for admins**: This label is auto applied to German GDPR documents.

7. Select **Next**.

8. On the **Scope** page, select the option **Files & emails**.

8. Select **Next**.

9. On the **Files & email** page, select **Next**.

10. On the **Auto-Labeling** page, set the **Auto-labeling for files and emails** to enabled.

11. In the **Detect content that matches these conditions** section, select **+Add condition** and then select **Content contains**.

12. In **Content contains** section select the **Add** text and then select **Sensitive info types**.

13. A **Sensitive info types** panel will be displayed on the right.

14. In the **Search for sensitive info types** search panel, enter the following information: 

    German

15. Press the enter button, the results will display sensitivity info types related to Germany.

20. Press the **Select all** check box.

21. Select **Add**.

22. Select **Next**.

23. On the **Groups & sites** page, select **Next**.

24. On the **Azure Purview assets (preview)** page, select **Next**. 

25. On the **Finish** page, select **Create label**.

26. The label will be created and when complete a message will display **Your label was created**.

27. Select **Done**.

28. On the **Information protection** page, select **Publish labels**.

29. The Publish sensitivity labels wizard will start.

30. On the **Choose labels to publish** page, select the **Choose sensitivity labels to publish link**.

31. A side bar called **Sensitivity labels to publish** will appear on the right.

32. Select the **Internal/GDPR Germany** checkbox.

33. Select **Add**.

34. On the **Choose labels to publish** page, select **Next**.

35. On the **Publish to users and groups page**, select **Next**.

36. On the **Policy settings** page, select **Next**.

37. On the **Name & Description** page, enter the following information:

   - **Name**: GDPR Germany policy
   - **Enter a description for your sensitivity label policy**: This auto apply sensitivity labels policy is for the GDPR region of Germany.

38. Select **Next**.

39. On the **Review your settings** page, select **Submit**.

40. The policy will be created and when complete a message will display, **New policy created**.

41. Select **Done**.

You have successfully created and published an auto apply sensitivity label for GDPR documents in the region Germany.

Note that it can take up to 24 hours for auto applied sensitivity labels to be applied, this duration will be longer when applied to more than 25,000 documents (that is, the daily limit).


# Proceed to Lab 2 - Exercise 1