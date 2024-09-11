---
lab:
    title: 'Sensitive information types'
    module: 'FY25 VTD Demo - Create and manage sensitive information types'
---


# Session 1 demo 1 - Manage Sensitive Information Types

## Task 1 – Create custom sensitive information types

In this task, you'll create a new custom sensitive information type that recognizes the pattern of employee IDs near the keywords "Employee" and "ID".

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

1. Sign out of Joni's account by selecting the profile picture of Joni Sherman in the top right. Select **Sign out**, then close the browser window.

1. Close the browser window then open a new browser window.

You have successfully created a new sensitive information type to identify employee IDs in the pattern of three uppercase characters, six numbers, and the keywords 'Employee' or 'IDs' within a range of 100 characters.

## Task 2 – Create keyword dictionary

In this task, you'll create a keyword dictionary to prevent personal information leakage in emails.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **MOD Administrator**.

1. The Microsoft Purview portal should still be on the Classifiers page in Microsoft Edge. If not, in Microsoft Edge, navigate to `https://purview.microsoft.com` > **Solutions** > **Information protection**.

1. In the left sidebar, expand **Classifiers** then select **Sensitive info types**.

1. Select **+ Create sensitive info type** to open the configuration for a new sensitive information type.

1. On the **Name your sensitive info type** page, enter:

    - **Name**: `Contoso Diseases List`
    - **Description**: `List of possible diseases of employees`.

1. Select **Next**.

1. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

1. On the **New pattern** flyout panel on the right, under **Primary element** select **+ Add primary element**, then select **Keyword dictionary**.

1. On the **Add a keyword dictionary** page enter:

   - **Name**: `Diseases Dictionary`
   - **Keywords**:

    ```text
    flu
    influenza
    cold
    bronchitis
    otitis
    ```

1. Select **Done** at the bottom of the flyout panel.

1. Back on the **New pattern** page, under **Supporting elements**, select **+ Add supporting elements or group of elements**, then select **Keyword list** to add additional support for the keyword dictionary.

1. On the **Add a keyword list** page enter:

   - **ID**: `Employee absence`
   - **Case insensitive**:

    ``` text
    employee
    absence
    reason
    ```

1. Select **Done** at the bottom of the flyout panel.

1. Back on the **New pattern** page, review the configuration and select **Create**.

1. Back on the **Define patterns for this sensitive info type** select **Next**.

1. On the **Choose the recommended confidence level to show in compliance policies**, leave the default value, then select **Next**.

1. On the **Review settings and finish** page, review your settings and select **Create**. Once your sensitive info type is created, select **Done** on the **Your sensitive info type is created** page.

1. Leave the browser window in the Microsoft Purview portal open.

You have successfully created a new sensitive information type based on a keyword dictionary and added more keywords to decrease the false positive rate.

## Task 3 – Test custom sensitive information types

Custom sensitive information types should always be tested before using them in policies otherwise data loss or leakage may occur due to a malfunctioning custom search pattern. In this task, you'll test the custom sensitive information types to ensure they recognize the desired patterns.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **MOD Administrator**.

1. In your task bar, search for `Notepad` in the search field. Select the **Notepad** app from the **Best match** section of the search.

1. In Notepad, enter:

    ``` text
    Employee Joni Sherman EMP123456 is absent because of the flu/influenza.
    ```

1. Select **File** > **Save As**.

1. Select **Documents** on the left side pane and enter `SickTestData` as the **File name**, then select **Save**.

1. Close the Notepad window.

1. Back in **Microsoft Edge**, Microsoft Purview portal should still be open on the Sensitive info types page.

1. In the **Search** bar on the upper right, enter `Contoso` and press Enter.

1. Select **Contoso Employee IDs**.

1. Select **Test**.

1. On the **Upload file to test "Contoso Employee IDs"** flyout panel on the right, select **Upload file**.

1. Select **Documents** from the left pane, select the *SickTestData.txt* file, then select **Open**.

1. Select **Test** to start the analysis.

1. On the **Match results** page, review the matches, then select **Finish** to end the test.

1. Navigate back to **Sensitive info types** and search for `Contoso` again.

1. This time select the **Contoso Diseases List** sensitive info type, then select **Test**.

1. On the **Upload file to test "Contoso Diseases List"** flyout panel on the right, select **Upload file**.

1. On the **Upload file to test** pane, select **Upload file**.

1. Select **Documents** from the left pane, select the *SickTestData.txt* file, then select **Open**.

1. Select **Test** to start the analysis.

1. On the **Match results** page, review the matches, then select **Finish** to end the test.

You have successfully tested the two custom sensitive information types and validated the search pattern recognizes the desired patterns.
