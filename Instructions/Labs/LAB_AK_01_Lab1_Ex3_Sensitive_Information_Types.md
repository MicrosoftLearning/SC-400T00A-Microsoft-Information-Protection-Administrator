# Lab 1 - Exercise 3 - Manage Sensitive Information Types

Contoso Ltd. previously had issues with employees accidentally sending out personal information from customers when working on support tickets in the ticketing solution. To educate users in the future, a custom sensitive information type is required to identify employee IDs in emails and documents, which consist of three uppercase characters and six numbers. To lower the false positive rate, the keywords "Employee" and "IDs" will be used. In this task you will create a new custom sensitive information type, a database for EDM-based classification and a keyword dictionary.

### Task 1 – Create Custom Sensitive Information Types

In this exercise, you will use the Security & Compliance Center PowerShell module to create a new custom sensitive information type that recognizes the pattern of employee IDs near the keywords "Employee" and "ID".

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft 365 compliance portal and sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

3. Select **Data classification** from the left pane.

4. If a **What is data classification?** message is displayed, select **Close** and select **Sensitive info types** from the top pane.  Hint: If **Sensitive info types** don't appear in the compliance portal then it's possible Joni's permissions update to Compliance Admin in the earlier lab has not updated in your browser yet.  You may have to sign-out and sign-in again as JoniS.

5. On the **Sensitive ino types** tab select **+ Create sensitive info type** to open the wizard for a new sensitive information type.

6. On the **Name your sensitive info type** page, type *Contoso Employee IDs* into **Name**.

7. Type *Pattern for Contoso employee IDs.* to the **Description** field and select **Next**.

8. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

9. Select the dropdown field for **+ Add primary element** in the **Primary element** section and select **Regular expression**.

10. In the **ID** field type *Contoso IDs* and enter the following to the Regular expression field: *\s[A-Z]{3}[0-9]{6}\s* and then select **Done**.

11. Below **Supporting elements**, select **+ Add supporting elements or group of elements** drop-down menu and select **Keyword list**.

12. In the ID field enter *Employee ID keywords* and enter the following into the text box below **Case insensitive**, on separate lines in the box, and then select **Done**.

- *Employee*
- *ID* 

13. In the New pattern windows decrease the **Character proximity** value to *100* characters.

14. Select the **Create** button.

15. On the **Define patterns for this sensitive info type** page select **Next**.

16. On the **Choose the recommended confidence level to show in compliance policies** page use the default value and select **Next**.

17. On the **Review settings and finish** page review the settings and select **Create**. When successfully created select **Done**.

18. Leave the browser window open.

You have successfully created a new sensitive information type to identify employee IDs in the pattern of three uppercase characters, six numbers, and the keywords 'Employee' or 'IDs' within a range of 100 characters.

### Task 2 – Create EDM-based classification information type

As an extra search pattern, you will create an EDM-based classification with a database schema of employee data. The database source file will be formatted with the following data fields of employees: Name, Birthdate, StreetAddress, and EmployeeID.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. To create the required Azure AD security group, sign out of Joni Sherman's account by selecting the user image in the upper right corner and select **Sign out**.

3. Close the browser window and open a new browser window.

4. In **Microsoft Edge**, navigate to **https://admin.microsoft.com**.

5. When the **Pick an account** page is displayed, select **Use another account** and sign in as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

6. From the left pane, select **Teams & groups** and select **Active teams & groups**.

7. Select **Add a group** from the top pane.

8. On the **Choose a group type** page, select **Security** and **Next**.

9. On the **Set up the basics**, enter the following to the **Name** field: *EDM_DataUploaders*.  In the Description field, enter *people who will upload data for EDM*.

10. Select **Next**.

11. On the **Review and finish adding group** page, review your settings and select **Create group**.

12. When the **New group created** page is shown, select **Close**.

13. Select **Refresh** from the top pane, select the **Security** tab, and select newly created **EDM_DataUploaders** group from the list to open the right-side pane.

14. Select the **Members** tab and select **View all and manage members**.

15. In the **Manage group members** screen, select **(+) Add members**.

16. Select **Joni Sherman**, select the **Add (1)** button then select the back arrow button.

17. Verify **Joni Sherman** is listed below **Members**.

18. Close the right side pane with **X**.

19. Select the circle with the MOD Administrator initials **MA** and select **Sign out**.

20. Close the browser window and open a new one.

21. Navigate to the Microsoft 365 Compliance Center at https://compliance.microsoft.com.

22. When the **Pick an account** page is displayed, select **Joni Sherman** and sign in.

23. Select **Data classification** and select **Exact data matches** tab from the top pane.

24. Select **+ Create EDM schema** to create a new schema definition.

25. In the **Name** field, enter *employeedb*.

26. In the **Description** field, enter *Employee Database schema.*.

27. Select **Ignore delimiters and punctuation for all schema fields**.

28. Select **Choose delimiters and punctuation to ignore** and select *Hyphen*, *Period*, *Space*, *Open parenthesis* and *Close parenthesis*.

29. In the first **Schema field name**, enter *Name* and mark the **Field is searchable** box.

30. Select **+ Add schema data field**.

31. In **Schema field name**, below **Schema field #2**, enter *Birthdate*.

32. Select **+ Add schema data field**.

33. In **Schema field name**, below **Schema field #3**, enter *StreetAddress*.

34. Select **+ Add schema data field**.

35. In **Schema field name**, below **Schema field #4**, enter *EmployeeID*.

36. Select **Field is searchable**. 

37. Select **Save**.

38. Select **EDM sensitive info types** from the left pane.

39. Click the more options(...) on the top menu and select **+ Create EDM sensitive info type** to open the **EDM rule package** wizard.  

40. On the **Define data store schema** page, select **Choose an existing EDM schema**.

41. Select **employeedb** and select **Add**.

42. Review the data store schema and select **Next**.

43. On the **Define patterns for this EDM sensitive info type** page, select **+ Create pattern**.

44. On the **New pattern** pane on the right-side, in the Primary element field, select *EmployeeID*.

45. Below **Primary element's sensitive info type**, select **Choose sensitive info type**. 

46. In the **Search** bar, enter *Contoso* and press the enter key.

47. Select **Contoso Employee IDs** and select **Done**.

48. Select **Done**.

49. Select **Next** in the *Define patterns for this EDM sensitive info type* screen.

50. In the **Choose the recommended confidence level and character proximity** let the default value persist and select **Next**.

51. In the **Name and describe your EDM sensitive info type** page, enter *Contoso Employee EDM* for the name.

52. In the **Description for admins** field, enter *EDM-based sensitive information type for employee personal information.*.

53. Select **Next**, review the settings and select **Submit**.

54. On the **Your EDM sensitive info type was created** page, select **Done**.

55. Leave the browser open with the Microsoft 365 Compliance Center.

You have successfully created a new EDM-based classification sensitive information type for identifying employee data from a database file source.

### Task 3 – Create EDM-based classification data source

To associate the EDM-based classification with a database containing sensitive data, hashing and uploading the actual data for the sensitive information type via the EDM Upload Agent tool is required next.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, navigate to **https://go.microsoft.com/fwlink/?linkid=2088639** to access the EDM download agent.

3. Select **Run** to download and install the tool.

4. When the setup wizard opens in the background, select the installer from the taskbar.

5. In the **Microsoft Exact Data Match Upload Agent Setup Wizard**, select **Next**.

6. Select **I accept the terms in the License Agreement** and select **Next**.

7. Do not change the default **Destination Folder** path and select **Next**.

8. Select **Install** to perform the installation.

9. When the **User Account Control** window opens, select **Yes**.

10. When the installation finishes, select **Finish**.

11. Select the Windows symbol in the lower left to open the start menu, enter **Notepad** and select **Notepad** from the start menu.

12. Enter the following text to the first line in the notepad window:

    `Name,Birthdate,StreetAddress,EmployeeID`

13. Use enter button and add the following text to the second line in the notepad window:

    `Joni Sherman,01.06.1980,1 Main Street,CSO123456`

14. Use enter button and add the following text to the third line in the notepad window:

    `Lynne Robbins,31.01.1985,2 Secondary Street,CSO654321`

15. Select **File** and **Save As** to save the file.

16. Select **Documents** from the left side pane and enter the following in the **File name** field: *EmployeeData.csv*

17. Select the dropdown at **Save as type:** and select **All Files (*.*)**.

18. Select the dropdown at **Encoding:** and select **UTF-8** and select **Save**.

19. Close the Notepad window.

20. Select the windows symbol in the taskbar with the right mouse button and select **PowerShell** and run as administrator.

21. When the **User Account Control** window opens, select **Yes**.

22. Navigate to the EDM Upload Agent directory:

    `cd "C:\Program Files\Microsoft\EdmUploadAgent"`

23. Authorize with your Account to upload the database to your tenant by running the following cmdlet:

    `.\EdmUploadAgent.exe /Authorize`

24. When the **Pick an account** window is displayed, sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

25. Download the database schema definition of the EDM-based classification sensitive information type by running the following script in PowerShell:

    `.\EdmUploadAgent.exe /SaveSchema /DataStoreName employeedb /OutputDir "C:\Users\Admin\Documents\"`

    Note: If the last command fails, it possibly takes more time until the **EDM_DataUploaders** group membership is applied. It can take up to one hour until it is possible to download the schema file.  If it fails proceed to the next task and return to this step later.

26. Hash the database file and upload it to the EDM-based classification sensitive information type by running the following script in PowerShell:

    `.\EdmUploadAgent.exe /UploadData /DataStoreName employeedb /DataFile "C:\Users\Admin\Documents\EmployeeData.csv" /HashLocation "C:\Users\Admin\Documents\" /Schema "C:\Users\Admin\Documents\employeedb.xml"`

27. Check the upload progress until the state changes to completed then run the following PowerShell command:

    `.\EdmUploadAgent.exe /GetSession /DataStoreName employeedb`

28. Close the PowerShell window.

You have successfully hashed and uploaded a database file for a EDM-based classification sensitive information type.

### Task 4 – Create Keyword Dictionary

Several violations of personal information leakage happened when users sent out emails after colleagues reported on sick leave.  When that happened the reason for illness or disease was sent out.  We do not want that to happen.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. Select **Data classification** from the left-side pane and select **Sensitive info types** tab from the top pane.

4. Select **+ Create sensitive info type** to open the wizard for a new sensitive information type.

5. On the **Name your sensitive info type** page, enter *Contoso Diseases List* into **Name** field.

6. Enter *List of possible diseases of employees.* to the **Description** field and select **Next**.

7. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

8. Select the dropdown field below **Primary element** and select **Keyword dictionary**.

10. In the **Add a keyword dictionary** page enter the name *Diseases Dictionary*. 

11. In the **Keywords** area enter the following keywords, each into a separate line:

    - *flu*
    - *influenza*
    - *cold*
    - *bronchitis*
    - *otitis*.

12. Select **Done**.

13. Below **Supporting elements**, select **+ Add supporting elements or group of elements** drop-down and select **keyword list** to add additional support for the keyword dictionary.

14. In the **Add a keyword list** page enter *Employee absence* in the **ID** field. In the **Case insensitive** box, enter the following keywords, each into a separate line:
    
    - *employee*
    - *absence*
    - *reason*   

15. Select **Done**.

16. In the **New pattern** page, review the configuration and select **Create**.

17. In the **Define patterns for this sensitive info type** select **Next**.

18. In the **Choose the recommended confidence level to show in compliance policies** let the default value persist and select **Next**. 

19. In the **Review settings and finish** page, review your settings and select **Create**.  When the process is complete select **Done**.

20. Leave the browser window in the Microsoft 365 compliance center open.

You have successfully created a new sensitive information type based on a keyword dictionary and added more keywords to decrease the false positive rate. Proceed with the next task.

### Task 5 – Work with custom Sensitive Information Types

Custom Sensitive information types should always be tested before using them in policies otherwise data loss or leakage may occur due to a malfunctioning custom search pattern. 

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. Select the Windows symbol in the lower left to open the start menu, enter **Notepad** and select **Notepad** from the start menu.

3. Enter the following text to the notepad window:

    `Employee Joni Sherman EMP123456 is on absence because of the flu/influenza.`

4. Select **File** and **Save As**.

5. Select Documents on the left-side pane.

6. In the **File name** field, enter *SickTestData* and select **Save**.

7. Close the Notepad window.

8. In **Microsoft Edge**, the Microsoft 365 compliance center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

9. In the left navigation pane select **Data classification**, then select the **Sensitive info types** tab.

10. In the **Search** box from the upper right side and enter *Contoso* and press Enter.

11. Select **Contoso Employee IDs** to open the right side pane.

12. Select **Test** from the right-side pane.

13. On the **Upload file to test** page, select **Upload file**.

14. Select **Documents** from the left pane, select the file with the name *SickTestData* and select **Open**.

15. Select **Test** to start the analysis.

16. On the **Match results** page, review the found match.

17. Select **Finish** and close the test page by clicking the **X** button.

18. Back on the **Data classification** page, select the Sensitive Information Type with the name **Contoso Diseases List**.

19. In the right side pane, select **Test**.

20. On the **Upload file to test** page, select **Upload file**.

21. Select **Documents** from the left pane, select the file with the name *SickTestData* and select **Open**.

22. Select **Test** to start the analysis.

23. On the **Match results** page, review the found match. When done review select **Finish**.

You have successfully tested the two custom sensitive information types and validated the search pattern recognizes the desired patterns. You have finished the creation of sensitive information types and can proceed with the next exercise.

# Proceed to Lab 1 - Exercise 4 
