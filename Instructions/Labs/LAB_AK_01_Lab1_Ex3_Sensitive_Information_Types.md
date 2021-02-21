# Exercise 3 - Manage Sensitive Information Types

Contoso Ltd. previously had issues with employees accidentally sending out personal information from customers when working on support tickets in the ticketing solution. To educate users in the future, a custom sensitive information type is required to identify employee IDs in emails and documents, which consist of three uppercase characters and six numbers. To lower the false positive rate, the keywords "Employee" and "IDs" will be used. In this task you will create a new custom sensitive information type, a database for EDM-based classification and a keyword dictionary.

### Task 1 – Create Custom Sensitive Information Types

In this exercise, you will use the Security & Compliance Center PowerShell module to create a new custom sensitive information type that recognizes the pattern of employee IDs near the keywords "Employee" and "ID".

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. Select **Data classification** from the left-side pane.

4. If a **What is data classification?** message is displayed, select **Close** and **Sensitive info types** from the top pane.

5. Select **(+) Create info type ** to open the wizard for a new sensitive information type.

6. On the **Choose a name and description** page, enter into *Contoso Employee IDs* into **Name**.

7. Enter *Pattern for Contoso employee IDs.* to the **Description** field and select **Next**.

8. On the **Requirements for matching** page, select **(+) Add an element**.

9. Select the dropdown field below **Detect content containing** and select **Regular expression**.

10. Enter the following to the input field: *\s[A-Z]{3}[0-9]{6}\s*

11. Below **Supporting elements**, select **Add supporting elements** and **Contains this keyword list**.

12. Enter the following into the text box below **Keyword list**: *Employee* and *IDs*

13. Decrease the **Character proximity** to *100* characters.

14. Select **Next**.

15. Finish the wizard by selecting **Finish**.

16. In the **compliance** window, select **Yes**.

17. Select the **Search** box in the upper right-side, type *Contoso* and press the enter key.

18. Select the newly created sensitive information type *Contoso Employee IDs* to open the right-side pane.

19. Review the configured settings of the sensitive information type.

20. Leave the browser window open.

You have successfully created a new sensitive information type to identify employee IDs in the pattern of three uppercase characters, six numbers, and the keywords 'Employee' or 'IDs' within a range of 100 characters.

### Task 2 – Create EDM-based classification information type

As an extra search pattern, you will create an EDM-based classification with a database schema of employee data. The database source file will be formatted with the following data fields of employees: Name, Birthdate, StreetAddress, and EmployeeID.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. To create the required Azure AD security group, sign out of Joni Sherman's account by selecting the JS in the upper right corner and select **Sign out**.

3. Close the browser window and open a new browser window.

4. In **Microsoft Edge**, navigate to **https://admin.microsoft.com**.

5. When the **Pick an account** page is displayed, select **Use another account** and sign in as **MOD Administrator**.

6. From the left side pane, select **Groups** and select **Active groups**.

7. Select **Add a group** from the top pane.

8. On the **Choose a group type** page, select **Security** and **Next**.

9. On the **Set up the basics**, enter the following to the **Name** field: *EDM_DataUploaders*

10. Select **Next**.

11. On the **Review and finish adding group** page, review your settings and select **Create group**.

12. When the **New group created** page is shown, select **Close**.

13. Select **Refresh** from the top pane and select the newly created **EDM_DataUploaders** group from the list to open the right side pane.

14. Select the **Members** tab and select **View all and manage members**.

15. In the right side pane, select **(+) Add members**.

16. Select the checkbox left from **Joni Sherman**, select **Save** and **Close**.

17. Verify **Joni Sherman** is listed below **Group members** and select **Close**.

18. Close the right side pane with **X**.

19. Select the circle with the MOD Administrator initials **MA** and select **Sign out**.

20. Close the browser window and open a new one.

21. Navigate to the Microsoft 365 Compliance Center at https://compliance.microsoft.com.

22. When the **Pick an account** page is displayed, select **Joni Sherman** and sign in.

23. Navigate to **Data classification** and **Exact data matches **from the top pane.

24. Select **(+) Create EDM schema** to create a new schema definition.

25. In the **Name** field, enter *employeedb*.

26. In the **Description** field, enter *Employee Database schema.*.

27. Select **Ignore delimiters and punctuation for all schema fields**.

28. Select **Choose delimiters and punctuation to ignore** and select *Hyphen*, *Period*, *Space*, *Open parenthesis* and *Close parenthesis*.

29. In the first **Schema field name**, enter *Name* and select **Field is searchable**.

30. Select **(+) Add schema data field**.

31. In **Schema field name**, below **Schema field #2**, enter *Birthdate*.

32. Select **(+) Add schema data field**.

33. In **Schema field name**, below **Schema field #3**, enter *StreetAddress*.

34. Select **(+) Add schema data field**.

35. In **Schema field name**, below **Schema field #4**, enter *EmployeeID*.

36. Select **Field is searchable**. 

37. Select **Save**.

38. Select **EDM sensitive info types** from the left-side pane.

39. Select **(+) Create EDM sensitive info type** to open the **EDM rule package** wizard.

40. On the **Define data store schema** page, select **Choose an existing EDM schema**.

41. Select **employeedb** and select **Add**.

42. Review the data store schema and select **Next**.

43. On the **Define patterns for this EDM sensitive info type** page, select **(+) Create pattern**.

44. On the **New pattern** right-side pane, to the Primary element field, select *EmployeeID*.

45. Below **Choose primary element's sensitive info type**, select **Choose sensitive info type**. 

46. To the **Search** bar, enter *Contoso* and press the enter key.

47. Select **Contoso Employee IDs** and select **Done**.

48. Select **Done**.

49. Select **Next**.

50. To the **Character proximity** field, enter *100*.

51. Select **Next**.

52. To the **Name** field, enter *Contoso Employee EDM*.

53. To the **Description for admins** field, enter *EDM-based sensitive information type for employee personal information.*.

54. Select **Next**, review the settings and select **Submit**.

55. On the **Your EDM sensitive info type was created** page, select **Done**.

56. Leave the browser open with the Microsoft 365 Compliance Center.

You have successfully created a new EDM-based classification sensitive information type for identifying employee data from a database file source.

### Task 3 – Create EDM-based classification data source

To associate the EDM-based classification with a database containing sensitive data, hashing and uploading the actual data for the sensitive information type via the EDM Upload Agent tool is required next.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, navigate to **https://go.microsoft.com/fwlink/?linkid=2088639** to access the EDM download agent.

3. Select **Run** to download and install the tool.

4. When the setup wizard opens in the background, select the installer from the taskbar.

5. In the **Microsoft Exact Data Match Upload Agent Setup**, select **Next**.

6. Select **I accept the terms in the License Agreement** and select **Next**.

7. Do not change the default **Destination Folder** path and select **Next**.

8. Select **Install** to perform the installation.

9. When the **User Account Control** window opens, select **Yes**.

10. When the installation finishes, select **Finish**.

11. Select the Windows symbol in the lower left to open the start menu, enter **Notepad** and select **Notepad** from the start menu.

12. Enter the following text to the first line in the notepad window:

    Name,Birthdate,StreetAddress,EmployeeID

13. Use enter and add the following text to the second line in the notepad window:

    Joni Sherman,01.06.1980,1 Main Street,CSO123456

14. Use enter and add the following text to the third line in the notepad window:

    Lynne Robbins,31.01.1985,2 Secondary Street,CSO654321

15. Select **File** and **Save As** to save the file.

16. Select **Documents** from the left side pane and enter the following in the **File name** field: *EmployeeData.csv*

17. Select the dropdown at **Save as type:** and select **All Files (*.*)**.

18. Select the dropdown at **Encoding:** and select **UTF-8** and select **Save**.

19. Close the Notepad window.

20. Select the windows symbol in the taskbar with the right mouse button and select **PowerShell (Admin)**.

21. When the **User Account Control** window opens, select **Yes**.

22. Navigate to the EDM Upload Agent directory:

    cd "C:\Program Files\Microsoft\EdmUploadAgent"

23. Authorize with your Account to upload the database to your tenant:

    .\EdmUploadAgent.exe /Authorize

24. When the **Pick an account** window is displayed, select **Joni Sherman** and sign in.

25. Download the database schema definition of the EDM-based classification sensitive information type:

    .\EdmUploadAgent.exe /SaveSchema /DataStoreName employeedb /OutputDir "C:\Users\Admin\Documents\"

26. Note: If the last command fails, it possibly takes more time until the **EDM_DataUploaders** group membership is applied. It can take up to one hour until it is possible to download the schema file.

27. Hash the database file and upload it to the EDM-based classification sensitive information type:

    .\EdmUploadAgent.exe /UploadData /DataStoreName employeedb /DataFile "C:\Users\Admin\Documents\EmployeeData.csv" /HashLocation "C:\Users\Admin\Documents\" /Schema "C:\Users\Admin\Documents\employeedb.xml"

28. Check the upload progress until the State changes to Completed:

    .\EdmUploadAgent.exe /GetSession /DataStoreName employeedb

29. Close the PowerShell window.

You have successfully hashed and uploaded a database file for a EDM-based classification sensitive information type.

### Task 4 – Create Keyword Dictionary

Several violations of personal information leakage happened, when users sent out emails after colleagues reported in on sick leave and the reason or disease was sent out.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. Select **Data classification** from the left-side pane and **Sensitive info types** from the top pane.

4. Select **(+) Create info type ** to open the wizard for a new sensitive information type.

5. On the **Choose a name and description** page, enter *Contoso Diseases List* into **Name**.

6. Enter *List of possible diseases of employees.* to the **Description** field and select **Next**.

7. On the **Requirements for matching** page, select **(+) Add an element**.

8. Select the dropdown field below **Detect content containing** and select **Dictionary (Large keywords)**.

10. Select **(+) Add a dictionary** and **Create new keyword dictionaries**, to open the right-side pane.

11. Below **Choose a name for your keyword dictionary**, enter *Diseases Dictionary*.

12. Below **Enter the keywords, with each keyword on a separate line.**, enter the following keywords, each into a separate line:

    - *flu*
    - *influenza*
    - *cold*
    - *bronchitis*
    - *otitis*.

13. Select **Save**.

14. Below **Keyword dictionaries**. select **Diseases Dictionary** and select **Add**.

15. Below **Supporting elements**, select **Add supporting elements** and **Contains this keyword list** to add additional support for the keyword dictionary.

16. To the text box below **Keyword list**, enter the following keywords: *employee,absence,reason*

17. Increase the **Minimum Count** value to *2*.

18. Select **Next**, review the configuration and select **Finish**.

19. When the **compliance** window appears, select **No**.

20. Leave the browser window in the Microsoft 365 Compliance center open.

You have successfully created a new sensitive information type based on a keyword dictionary and added more keywords to decrease the false positive rate. Proceed with the next task.

### Task 5 – Work with custom Sensitive Information Types

Custom Sensitive Information Types always must be tested first, before using them in policies and data loss or leakage can happen, because of a malfunctioning custom search pattern. 

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. Select the Windows symbol in the lower left to open the start menu, enter **Notepad** and select **Notepad** from the start menu.

3. Enter the following text to the notepad window:

    Employee Joni Sherman with ID CSO123456 is on absence because of the flu/influenza.

4. Select **File** and **Save As**.

5. Select Documents in on the left-side pane.

6. In the **File name** field, enter *SitTestData* and select **Save**.

7. Close the Notepad window.

8. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

9. In the left navigation pane select **Data classification**, then select the **Sensitive info types** tab.

10. Select **Search** from the upper left side and enter *Contoso*.

11. Select **Contoso Employee IDs** to open the right side pane.

12. Select **Test type** from the right side pane.

13. On the **Upload file to test** page, select **Click to Browse**.

14. Select **Documents** from the left pane, select the file with the name *SitTestData* and select **Open**.

15. Select **Test** to start the analysis.

16. On the **Match results** page, review the found match.

17. Select **Finish** to close the test page.

18. Back on the **Data classification** page, select the Sensitive Information Type with the name **Contoso Diseases List**.

19. In the right side pane, select **Test type**.

20. On the **Upload file to test** page, select **Click to Browse**.

14. Select **Documents** from the left pane, select the file with the name *SitTestData* and select **Open**.

15. Select **Test** to start the analysis.

16. On the **Match results** page, review the found match.

You have successfully tested the two custom sensitive information types and validated the search pattern recognizes the desired patterns. You have finished the creation of sensitive information types and can proceed with the next exercise.

# Proceed to Exercise 4 