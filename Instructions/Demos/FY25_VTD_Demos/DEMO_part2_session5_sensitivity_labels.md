---
lab:
    title: 'Session 5 - Microsoft Purview Information Protection'
    module: 'Learning Objective - Implement and manage information protection'
---

# Part 2 Demo 5 - Create a sensitivity label

With the introduction of Microsoft 365 Copilot, Contoso Ltd.’s HR department is concerned about protecting sensitive employee data in automatically generated documents. To ensure data security, they're applying sensitivity labels in Microsoft Purview. These labels will encrypt and apply access controls to any sensitive HR documents, including those created by AI, safeguarding confidential information.

## Task 1 – Create sensitivity labels

In this task, we will create a sensitivity label to protect internal documents, along with a sublabel specifically for HR employee data. These labels will help Contoso Ltd. secure sensitive information, such as employee records, by ensuring only authorized users can access them.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. Open **Microsoft Edge** and navigate to **`https://purview.microsoft.com`**. Log into Microsoft Purview as **MOD Administrator** `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the Microsoft Purview portal, select **Solutions** from the left sidebar, then select **Information Protection**.

1. On the **Microsoft Information Protection** page, on the left sidebar, select **Sensitivity labels**.

1. On the **Sensitivity labels** page select **+ Create a label**.

1. The **New sensitivity label** configuration will start. On the **Provide basic details for this label**, enter:

    - **Name**: `Internal`
    - **Display name**: `Internal`
    - **Description for users**: `Internal sensitivity label.`
    - **Description for admins**: `Internal sensitivity label for Contoso.`

1. Select **Next**.

1. On the **Define the scope for this label** page, select **Items**, then select **Files** and **Emails**. If the checkbox for **Meetings** is selected, make sure it's deselected.

1. Select **Next**.

1. On the **Choose protection settings for labeled items** page, select **Next**.

1. On the **Auto-labeling for files and emails** page, select **Next**.

1. On the **Define protection settings for groups and sites** page, select **Next**.

1. On the **Auto-labeling for schematized data assets (preview)** page, select **Next**.

1. On the **Review your settings and finish** page, select **Create label**.

1. On the **Your sensitivity label was created** page, select **Don't create a policy yet**, then select **Done**.

1. On the **Sensitivity labels** page, find the newly created **Internal** sensitivity label. Select the vertical ellipsis (**...**) next to it, then select **+ Create sublabel** from the dropdown menu.

    ![Screenshot showing the Action menu to create a sublabel for a sensitivity label.](/Instructions/Media/create-sublabel-button.png)

1. The **New sensitivity label** configuration will start. On the **Provide basic details for this label** page enter:

   - **Name**: `Employee data (HR)`
   - **Display name**: `Employee data (HR)`
   - **Description for users**: `This HR label is the default label for all specified documents in the HR Department.`
   - **Description for admins**: `This label is created in consultation with Ms. Jones (Head of HR department). Contact her if changes to this label are needed.`

1. Select **Next**.

1. On the **Define the scope for this label** page, select **Items**, then select **Files** and **Emails**. If the checkbox for **Meetings** is selected, make sure it's deselected.

1. Select **Next**.

1. On the **Choose protection settings for labeled items** page, select the **Control access** option, then select **Next**.

1. On the **Access control** page, select **Configure access control settings**.

1. Configure the encryption settings with these options:

   - **Assign permissions now or let users decide?**: Assign permissions now
   - **User access to content expires**: Never
   - **Allow offline access**: Only for a number of days
   - **Users have offline access to the content for this many days**: 15
   - Select the **Assign permissions** link. On the **Assign permissions** flyout panel, select the **+ Add any authenticated users**, then select **Save** to apply this setting.

1. On the **Access control** page, select **Next**.

1. On the **Auto-labeling for files and emails** page, select **Next**.

1. On the **Define protection settings for groups and sites** page, select **Next**.

1. On the **Auto-labeling for schematized data assets (preview)** page, select **Next**.

1. On the **Review your settings and finish** page, select **Create label**.

1. On the **Your sensitivity label was created** page, select **Don't create a policy yet**, then select **Done**.

You have successfully created a sensitivity label for internal company documents and a sublabel specifically for HR employee data.

## Task 2 – Publish sensitivity labels

Now that we have created the sensitivity labels, we will publish them so that they are available for use by HR staff at Contoso Ltd.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft Purview as **MOD Administrator**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If not, navigate to **`https://purview.microsoft.com`** > **Solutions** > **Information Protection** > **Sensitivity labels**.

1. On the **Sensitivity labels** page select **Publish label**.

1. The publish sensitivity labels configuration will start.

1. On the **Choose sensitivity labels to publish** page, select the **Choose sensitivity labels to publish** link.

1. On the **Sensitivity labels to publish** flyout panel, select the **Internal** and **Internal/Employee Data (HR)** checkboxes, then select **Add** at the bottom of the flyout panel.

1. Back on the **Choose sensitivity labels to publish** page, select **Next**.

1. On the **Assign admin units** page, select **Next**

1. On the **Publish to users and groups** page, select **Next**.

1. On the **Policy settings** page, select **Next**.

1. On the **Default settings for documents** select **Next**.

1. On the **Default settings for emails** select **Next**.

1. On the **Default settings for meetings and calendar events** select **Next**.

1. On the **Default settings for Power BI Content** select **Next**.

1. On the **Name your policy** page, enter:

   - **Name**: `Internal HR employee data`
   - **Enter a description for your sensitivity label policy**: `This HR label is to be applied to internal HR employee data.`

1. Select **Next**.

1. On the **Review and finish** page, select **Submit**.

1. On the **New policy created**, select **Done** to finish publishing your label policy.

1. Sign out of the MOD Administrator account.

You have now published the sensitivity labels, making them available to the HR team for use in their documents.

## Task 3 – Apply sensitivity labels

In this task, we will apply the newly created sensitivity labels to a document in Word and an email in Outlook, ensuring that sensitive HR data is properly protected.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. Navigate to https://www.office.com/ and **Sign in** as **Joni Sherman** `jonis@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in the demo setup.

1. On the **Welcome to Microsoft 365** page, select **Create new** in the middle of the page.

1. Select **Document** to create a new word document.

1. On the **Your privacy option** dialogue, select **Close**.

1. Enter this text in the new blank document:

   `Important HR employee document.`

1. Select **Sensitivity** from the navigation ribbon and select **Internal** > **Employee Data (HR)** to apply the newly created sensitivity label to this document.

    ![Screenshot showing the sensitivity label button in Word.](/Instructions//Media/word_label.png)

    >**Note:** It can take 24-48 hours for newly published sensitivity labels to be available for application. If the newly created sensitivity labels aren't available, you can use **Confidential** > **All Employees** for this exercise.

1. In the upper left of the document, select **Document** to rename this file, and rename it to **`HR Document`**. Press enter to apply this name change.

    ![Screenshot showing where to rename a file in Word on the web.](/Instructions//Media/rename-web-word-file.png)

1. Close the tab to return to the Word Online tab. Select the meatball menu on the top left and select **Outlook** to open Outlook on the web.

1. In Outlook on the web, select **New mail**.

1. In the **To** field enter the name: **`Allan`** and select **Allan Deyoung** from the drop-down list.

1. In the subject line, enter: **`Employee data for HR`**

1. In the body of the email, enter:

    ``` text
    Dear Mr. Deyoung, 

    Please find attached the important HR employee document. 

    Kind regards,

    Joni Sherman
    ```

1. Select the paperclip symbol from the top navigation ribbon to add an attachment. Under **Suggested files** select **HR Document.docx**.

1. Select **Send** to send out the email message with attached document.

1. Sign out of Joni's account.

You have successfully applied the Employee Data (HR) sensitivity label to both the document and the email.

## Task 4 – Configure auto labeling

In this task, you'll create a sensitivity label that will auto-label documents and emails containing sensitive HR-related employee information, ensuring they are protected automatically, even when generated by Microsoft 365 Copilot.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **MOD Administrator**.

1. In the Microsoft Purview portal, select **Solutions** from the left side bar, then select **Information protection**. Select **Sensitivity labels**.

1. On the **Sensitivity labels** page, find the newly created **Internal** sensitivity label. Select the vertical ellipsis (**...**) next to it, then select **+ Create sublabel** from the dropdown menu.

1. The **New sensitivity label** configuration will start. On the **Provide basic details for this label** page, enter:

   - **Name**: `Payroll data`
   - **Display name**: `Payroll data`
   - **Description for users**: `This label is for documents and emails containing payroll information.`
   - **Description for admins**: `Automatically applies to any content containing payroll data.`

1. Select **Next**.

1. On the **Define the scope for this label** page, leave all default locations selected, then select **Next**.

1. On the **Choose protection settings for labeled items** page, select **Next**.

1. On the **Auto-labeling for files and emails** page, set the **Auto-labeling for files and emails** to enabled.

1. In the **Detect content that matches these conditions** section, select **+ Add condition** > **Content contains**.

1. In **Content contains** section select the **Add** > **Trainable classifiers**.

1. In the **Sensitive info types** flyout panel, search for `paystub` to display the **Paystub** trainable classifiers.

1. Select the checkbox for **Paystub** then select **Add** at the bottom of the panel to add this classifier.

1. Back on the **Auto-labeling for files and emails** page, select **Next**.

1. On the **Define protection settings for groups and sites** page, select **Next**.

1. On the **Auto-labeling for schematized data assets (preview)** page, select **Next**.

1. On the **Review your settings and finish** page, select **Create label**.

1. On the **Your sensitivity label was created** page, select **Don't create a policy yet**, then select **Done**.

1. Back on the **Sensitivity labels** page, expand the **Internal** sensitivity label, then the newly created **Payroll data** sublabel.

1. In the **Payroll data** flyout panel on the right, select **Create auto-labeling policy**.

1. On the auto-labeling policy configuration, on the **Name your auto-labeling policy** page, enter:

   - **Name**: `Payroll data auto-labeling policy`
   - **Description**: `Automatically applies the Payroll Data label to sensitive payroll documents and emails.`

1. Select **Next**.

1. On the **Assign admin units** page, select **Next**.

1. On the **Choose locations where you want to apply the label** page, leave the default selections, then select **Next**.

1. On the **Set up common or advanced rules** page, select **Next**.

1. On the **Define rules for content in all locations** page, select the pencil icon to edit the rule.

1. In the **New rule** flyout panel on the right, in the **Conditions** section, under **Content contains** select **Add** > **Trainable classifiers**, and add the **Paystub** trainable classifier again.

   **Why are we doing this again?** When this was done previously we were setting conditions to automatically label files and emails. This goes the extra step to automatically label files in SharePoint and OneDrive.

1. At the bottom of the **New rule** panel, select **Save**.

1. Back on the **Define rules for content in all locations** page, select **Next**.

1. On the **Choose a label to auto-apply** page, ensure the **Internal/Payroll data** is displayed, then select **Next**.

1. On the Decide if you want to test out the policy now or later page, select **Run policy in simulation mode**, and select the option to **Automatically turn on policy if not modified for 7 days in simulation**.

1. Select **Next**, then **Create policy**.

1. On the **Your auto-labeling policy was created** page, select **Done**.

You have now configured an auto-labeling policy to automatically apply the Payroll data label to documents containing sensitive employee information.
