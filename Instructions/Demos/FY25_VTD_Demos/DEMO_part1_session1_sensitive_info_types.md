---
lab:
    title: 'Sensitive information types'
    module: 'FY25 VTD Demo Session 1 - Create and manage sensitive information types'
---


# Part 1 Demo 1 - Manage Sensitive Information Types

Today, we'll create and test a custom sensitive information type (SIT) for Contoso Ltd. to help prevent the accidental sharing of employee IDs. This classification step is crucial before applying data protection policies, like DLP, to secure sensitive employee information.

## Task 1 – Create custom sensitive information types

In this first task, we'll build a custom SIT that detects employee IDs using a specific pattern and keywords such as 'Employee' and 'ID.' This ensures that we can accurately classify sensitive employee data before applying protection policies.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. On the left sidebar, select **Solutions** then select **Information Protection**.

1. On the left sidebar, expand **Classifiers** then select **Sensitive info types**.

1. On the **Sensitive info types** page, select **+ Create sensitive info type** to start the sensitive information type configuration.

1. On the **Name your sensitive info type** page, enter:

    - **Name**: `Contoso Employee IDs`
    - **Description**: `Pattern for Contoso employee IDs.`

1. Select **Next**.

1. On the **Define patterns for this sensitive info type** page, select **Create pattern**.

1. On the **New pattern** flyout panel on the right, select **+ Add primary element** > **Regular expression**.

1. On the **+ Add a regular expression​** flyout panel on the right, enter:

    - **ID**: `Contoso IDs`
    - **Regular expression**: `[A-Z]{3}[0-9]{6}`
    - Select the radio button for *String match*

1. Select **Done** at the bottom of the flyout panel.

1. Back on the **New pattern** flyout panel, under **Supporting elements**, select **+ Add supporting elements or group of elements** drop-down menu and select **Keyword list**.

1. On the **Add a keyword list** flyout panel on the right, enter:

    - **ID**: `Employee ID keywords`
    - **Case insensitive**:

       ```text
       Employee
       ID
       ```

    - Select the radio button for *Word match*

1. Select **Done** at the bottom of the flyout panel.

1. Back on the **New pattern** flyout panel, under **Character proximity**, decrease the **Detect primary AND supporting elements** value to `100` characters.

1. Select the **Create** button at the bottom of the flyout panel.

1. Back on the **Define patterns for this sensitive info type** page select **Next**.

1. On the **Choose the recommended confidence level to show in compliance policies** page use the default value and select **Next**.

1. On the **Review settings and finish** page review the settings and select **Create**. When successfully created select **Done**.

You have successfully created a new sensitive information type to identify employee IDs in the pattern of three uppercase characters, six numbers, and the keywords 'Employee' or 'IDs' within a range of 100 characters.

## Task 2 – Test custom sensitive information types

After creating the custom SIT, we need to test it using real data. In this task, we'll validate that the SIT detects employee IDs correctly in a CSV file, ensuring accuracy before it's used in any protection measures.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **MOD Administrator**.

1. In your task bar, search for `Notepad` in the search field. Select the **Notepad** app from the **Best match** section of the search.

1. In Notepad, enter:

    ``` text
    Employee Name,Employee ID,Net Pay,Deduction, Deduction Type
    Joni Sherman,EMP123456,$5000,$500, Health Insurance
    Megan Bowen,EMP654321,$4000,$400, Pension
    Lynne Robbins,EMP789123,$5500,$450, 401k
    ```

1. Select **File** > **Save As**.

1. Select **Documents** on the left side pane and enter `EmployeePayroll.csv` as the **File name**, then select **Save**.

1. Close the Notepad window.

1. Back in **Microsoft Edge**, Microsoft Purview portal should still be open on the Sensitive info types page.

1. In the **Search** bar on the upper right, enter `Contoso` and press Enter.

1. Select **Contoso Employee IDs**.

1. Select **Test**.

1. On the **Upload file to test "Contoso Employee IDs"** flyout panel on the right, select **Upload file**.

1. Select **Documents** from the left pane, select the *EmployeePayroll.csv* file, then select **Open**.

1. Select **Test** to start the analysis.

1. On the **Match results** page, review the matches, then select **Finish** to end the test.

You have successfully tested the custom sensitive information type and validated the search pattern recognizes the desired patterns.
