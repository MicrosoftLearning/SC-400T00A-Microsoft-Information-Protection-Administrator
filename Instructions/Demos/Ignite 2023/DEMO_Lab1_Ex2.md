---
lab:
    title: 'Exercise 2 - Manage Sensitive Information Types'
    module: 'Module 1 - Implement Information Protection'
---


# Exercise 2 - Manage Sensitive Information Types

Contoso Ltd. previously had issues with employees accidentally sending out personal information from customers when working on support tickets in the ticketing solution. To educate users in the future, a custom sensitive information type is required to identify employee IDs in emails and documents, which consist of three uppercase characters and six numbers. To lower the false positive rate, the keywords "Employee" and "IDs" will be used. In this task you will create a new custom sensitive information type, a database for EDM-based classification and a keyword dictionary.

## Task 1 – Create custom sensitive information types

In this exercise, you will use the Security & Compliance Center to create a new custom sensitive information type that recognizes the pattern of employee IDs near the keywords "Employee" and "ID".

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to Microsoft Purview compliance portal, **https://compliance.microsoft.com**, and sign in as JoniS@WWLxZZZZZZ.onmicrosoft.com. Joni's password should be provided by your lab hosting provider.

1. Expand **Data classification** from the left pane and select **Classifiers**

1. If a **What is data classification?** message is displayed, select **Close**.

1. Select **Sensitive info types** from the top pane.

    >[!hint] **Hint:** If **Sensitive info types** doesn't appear in the Purview portal, then it's possible Joni's permissions update to Compliance Admin in the earlier lab has not updated in your browser. You may have to sign-out and sign-in as JoniS.

1. On the **Sensitive info types** tab select **+ Create sensitive info type** to open the wizard for a new sensitive information type.

1. On the **Name your sensitive info type** page, enter the following information:

    - **Name**: Contoso Employee IDs
    - **Description**: Pattern for Contoso employee IDs.

1. Select **Next**.

1. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

1. In the right-side **New pattern** pane, select **+ Add primary element** and select **Regular expression**.

1. In the new right-side pane **Add a regular expression**, enter the following:

    - **ID**: Contoso IDs
    - **Regular expression**: ```[A-Z]{3}[0-9]{6}```
    - *String match*

1. Select **Done**.

1. In the **New pattern** flyout page, below **Supporting elements**, select **+ Add supporting elements or group of elements** drop-down menu and select **Keyword list**.

1. In the new right-side pane **Add a keyword list**, enter the following:

    - **ID**: Employee ID keywords
    - **Case insensitive**:
        - *Employee*
        - *ID*
    - Select the radio for *Word match* under the **Case Sensitive** field

1. Select **Done**.

1. In the New pattern windows decrease the **Character proximity** value to *100* characters.

1. Select the **Create** button.

1. Back on the **Define patterns for this sensitive info type** page select **Next**.

1. On the **Choose the recommended confidence level to show in compliance policies** page use the default value and select **Next**.

1. On the **Review settings and finish** page review the settings and select **Create**. When successfully created select **Done**.

1. Leave the browser window open.

You have successfully created a new sensitive information type to identify employee IDs in the pattern of three uppercase characters, six numbers, and the keywords 'Employee' or 'IDs' within a range of 100 characters.

## Task 2 – Create keyword dictionary

Several violations of personal information leakage happened when users sent out emails after colleagues reported on sick leave. When that happened the reason for illness or disease was sent out. We do not want that to happen.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. Expand **Data classification** from the left-side pane then select **Classifiers**. Select **Sensitive info types** tab from the top pane.

1. Select **+ Create sensitive info type** to open the wizard for a new sensitive information type.

1. On the **Name your sensitive info type** page, enter the following:

    - **Name**: Contoso Diseases List
    - **Description**: List of possible diseases of employees.

1. Select **Next**.

1. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

1. On the **New pattern** page select the dropdown field below **Primary element** and select **Keyword dictionary**.

1. On the **Add a keyword dictionary** page enter the following:

   - **Name**: Diseases Dictionary
   - **Keywords**:
      - flu
      - influenza
      - cold
      - bronchitis
      - otitis

1. Select **Done**.

1. Below **Supporting elements**, select **+ Add supporting elements or group of elements** drop-down and select **Keyword list** to add additional support for the keyword dictionary.

1. In the **Add a keyword list** page enter the following:

   - **ID**: Employee absence
   - **Case insensitive**:
     - employee
     - absence
     - reason

1. Select **Done**.

1. On the **New pattern** page, review the configuration and select **Create**.

1. On the **Define patterns for this sensitive info type** select **Next**.

1. On the **Choose the recommended confidence level to show in compliance policies** let the default value persist and select **Next**.

1. On the **Review settings and finish** page, review your settings and select **Create**. When the process is complete select **Done**.

1. Leave the browser window in the Microsoft Purview portal open.

You have successfully created a new sensitive information type based on a keyword dictionary and added more keywords to decrease the false positive rate. Proceed with the next task.

## Task 3 – Work with custom sensitive information types

Custom Sensitive information types should always be tested before using them in policies otherwise data loss or leakage may occur due to a malfunctioning custom search pattern.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. Select the Windows symbol in the lower left to open the start menu, enter **Notepad** and select **Notepad** from the start menu.

1. Enter the following text to the notepad window:

    ``` text
    Employee Joni Sherman EMP123456 is absent because of the flu/influenza.
    ```

1. Select **File** and **Save As**.

1. Select Documents on the left-side pane.

1. In the **File name** field, enter *SickTestData* and select **Save**.

1. Close the Notepad window.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the left navigation pane expand **Data classification**, then select **Classifiers**. Select the **Sensitive info types** tab.

1. In the **Search** box on the upper right, enter *Contoso* and press Enter.

1. Select **Contoso Employee IDs**.

1. Select **Test**.

1. On the **Upload file to test** page, select **Upload file**.

1. Select **Documents** from the left pane, select the file with the name *SickTestData* and select **Open**.

1. Select **Test** to start the analysis.

1. On the **Match results** page, review the found match.

1. Select **Finish** to end the test.

1. Use the top bar navigation to navigate back to **Sensitive info types**.

1. Search for *Contoso*, then select the Sensitive Information Type with the name **Contoso Diseases List**.

1. Select **Test**.

1. On the **Upload file to test** pane, select **Upload file**.

1. Select **Documents** from the left pane, select the file with the name *SickTestData* and select **Open**.

1. Select **Test** to start the analysis.

1. On the **Match results** page, review the found match. When done review select **Finish**.

You have successfully tested the two custom sensitive information types and validated the search pattern recognizes the desired patterns. You have finished the creation of sensitive information types and can proceed with the next exercise.
