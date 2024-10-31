# Exercise 1 - Create Custom Sensitive Information Types

As Contoso adopts more AI-powered tools, it's crucial to protect sensitive data from accidental exposure. To prevent the sharing of employee IDs, you'll create custom sensitive information types. These will help Contoso detect and classify sensitive data in emails and documents, ensuring it stays protected from misuse.

In this exercise, you'll create and test a custom sensitive information type to identify employee IDs.

**Tasks**:

1. Create a custom sensitive information type
1. Test a custom sensitive information type

## Task 1 – Create a custom sensitive information types

Contoso has had instances where employee IDs were accidentally shared in emails or documents. To prevent this from happening, you'll create a custom sensitive information type that can detect employee IDs and flag them before they're exposed.

1. You should still be logged into the Microsoft Purview portal as Joni Sherman.

1. In the Microsoft Purview portal, in the left sidebar, select **Solutions** then select **Information Protection**.

1. On the left sidebar, expand **Classifiers** then select **Sensitive info types**.

1. On the **Sensitive info types** page, select **+ Create sensitive info type** to start the sensitive information type configuration.

1. On the **Name your sensitive info type** page, enter:

    - **Name**: `Contoso Employee IDs`
    - **Description**: `Pattern for Contoso employee IDs.`

1. Select **Next**.

1. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

1. On the **New pattern** flyout page, select **+ Add primary element** > **Regular expression**.

1. On the **+ Add a regular expression​** flyout page on the right, enter:

    - **ID**: `Contoso IDs`
    - **Regular expression**: `[A-Z]{3}[0-9]{6}`
    - Select the option for _String match_

1. Select **Done** at the bottom of the flyout page.

1. Back on the **New pattern** flyout page, under **Supporting elements**, select **+ Add supporting elements or group of elements** dropdown menu and select **Keyword list**.

1. On the **Add a keyword list** flyout page, enter:

    - **ID**: `Employee ID keywords`
    - **Case insensitive**:

       ```text
       Employee
       ID
       ```

    - Select the option for _Word match_

1. Select **Done** at the bottom of page.

1. Back on the **New pattern** flyout page, under **Character proximity**, decrease the **Detect primary AND supporting elements** value to `100` characters.

1. Select the **Create** button at the bottom of the page.

1. Back on the **Define patterns for this sensitive info type** page select **Next**.

1. On the **Choose the recommended confidence level to show in compliance policies** page, use the default value and select **Next**.

1. On the **Review settings and finish** page, review your settings then select **Create**. When successfully created select **Done**.

You have successfully created a custom sensitive information type.

## Task 2 – Test custom sensitive information types

After creating the custom SIT, we need to test it using real data. In this task, we'll validate that the SIT detects employee IDs correctly in a CSV file, ensuring accuracy before it's used in any protection measures.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the Admin account.

1. Select the **Search** icon from the task bar, then search for `Notepad`. Select the **Notepad** app from the **Best match** section of the search.

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

1. Back in **Microsoft Edge**, Microsoft Purview portal should still be open on the **Sensitive info types** page.

1. In the **Search** bar on the upper right, search for `Contoso`.

1. Select the **Contoso Employee IDs** sensitive info type.

1. On the **Contoso Employee IDs** page, select **Test**.

1. On the **Upload file to test "Contoso Employee IDs"** flyout panel on the right, select **Upload file**.

1. Select **Documents** from the left pane, select the _EmployeePayroll.csv_ file, then select **Open**.

1. Select **Test** to start the analysis.

   You should see that the **Contoso Employee IDs** sensitive info type is performing as expected.

1. On the **Match results** page, select **Finish** to finish the test.

You have successfully tested the custom sensitive information type.
