---
lab:
    title: 'Exercise 1 - Explore Compliance Manager'
    module: 'Module 4 - Monitor and investigate data and activities by using Microsoft Purview'
---

## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab: Explore the Microsoft Purview compliance portal & Compliance Manager

You are Joni Sherman, the Compliance Administrator for Contoso Ltd., responsible for configuring and maintaining compliance within the organization's Microsoft 365 tenant. Contoso Ltd. has offices that operate in the financial sector and is subject to various regulatory requirements, including the Gramm-Leach-Bliley Act (GLBA) in the United States.

As part of your responsibilities, you need to conduct a compliance assessment specifically focused on GLBA requirements within the Microsoft 365 environment. The assessment will involve evaluating the current compliance posture, identifying any potential compliance gaps, and implementing appropriate measures to address them.

## Task 1 - Assign Compliance manager permissions

In this task you will grant Joni the required permissions to create assessments using Compliance Manager. You will also grant Megan the necessary permissions to act on improvement actions if they are assigned to her.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account. The password should be provided by your lab hosting provider.

1. In **Microsoft Edge**, select the address bar, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview compliance portal center as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. On the left navigation pane, expand the dropdown for **Roles & scopes** and select **Permissions**.

1. On the **Permissions** page select **Roles** under **Microsoft Purview solutions**.

1. On the **Role groups for Microsoft Purview solutions** select **Compliance Manager Administrator**.

1. On the **Compliance Manager Administrators** flyout page on the right, select **Edit**.

1. In the **Compliance Manager Administrators** wizard, on the **Edit members of the role group** page, select **+ Choose users**.

1. On the **Choose users** page, enter *Joni* into the search and press Enter.

1. Select the check box next to **Joni Sherman** and select the **Select** button at the bottom of the page.

1. Back on the **Edit members of the role group** page select **Next**.

1. On the **Review the role group and finish** select **Save**.

1. You should now have a message displaying **You successfully updated the role group**. Select **Done**.

1. Back on the **Role groups for Microsoft Purview solutions** select **Compliance Manager Contributors**.

1. On the **Compliance Manager Contributors** flyout page on the right, select **Edit**.

1. In the **Compliance Manager Contributors** wizard, on the **Edit members of the role group** page, select **+ Choose users**.

1. On the **Choose users** page, enter *Megan* into the search and press Enter.

1. Select the check box next to **Megan Bowen** and select the **Select** button at the bottom of the page.

1. Back on the **Edit members of the role group** page select **Next**.

1. On the **Review the role group and finish** select **Save**.

1. You should now have a message displaying **You successfully updated the role group**. Select **Done**.

1. Log out of the MOD Administrator account and close all windows.

In this task, you granted Joni the necessary permissions to create assessments using Compliance Manager and also assigned Megan the appropriate permissions to act on improvement actions when assigned to her.

## Task 2 - Explore Compliance Manager

In this task, you will explore the functionalities of Compliance Manager within the Microsoft Purview compliance portal center. 

1. Open **Microsoft Edge** and navigate to **https://compliance.microsoft.com**. Log into the Microsoft Purview compliance portal center as **Joni Sherman**.

1. Select **Compliance Manager** from the left navigation pane.

1. From the top of the Compliance Manager page, ensure **Overview** is selected (underlined). Scroll down to see all the information available on the page. Information on this page includes your compliance score, your points achieved, and Microsoft managed points achieved. You'll see Key improvement actions, Solutions that affect your score and compliance score breakdown by categories.

1. From the top of the Overview page, select **Improvement actions**. These are actions that can improve the organization’s compliance score. Note that as improvement actions are taken, points may take up to 24 hours to update. Notice the available filters.

1. From the list of improvement actions, select **Enable self-service password reset**. Review the available information for the improvement action. The left side of the window provides a brief overview about the implementation, test status, and more. To the right of the overview is the details page from which you can select implementation, testing, the related standards and regulatory requirements, and documents. Each of these tabs provides more detailed information for the improvement action.

1. Exit out of this improvement action by selecting **Improvement Actions** from the breadcrumb on the top left of the page. You're now back on the improvement actions page.

1. From the top of the page, select **Solutions**. On this page, you'll see how solutions contribute to your score and their remaining opportunity for improvement.

1. From the top of the page, select **Assessments**. On this page, you'll see the **Data Protection Baseline for Microsoft 365**. This is a default baseline assessment Microsoft provides in Compliance Manager for Microsoft 365. This baseline assessment has a set of controls for key regulations and standards for data protection and general data governance. Compliance Manager becomes more helpful as you add your own assessments to meet your organization's particular needs.

1. Select the **Data Protection Baseline** assessment. On the left side of the page is the overview that includes details and about information. Expand the **About** section and review the description about the Microsoft 35 data protection baseline. On the right side of the page, notice the information available on the progress tab and for the improvement actions. On the top of the page are tabs you can select view more detailed information on the Controls, your improvement actions, and Microsoft actions. Explore these at will.

1. From the top left of the page, above where it says Data Protection Baseline for Microsoft 365 (the breadcrumb), select **Assessment** to return to the assessments tab in Compliance Manager.

In this task, you explored the functionalities of Compliance Manager within the Microsoft Purview compliance portal center, including reviewing the compliance overview, improvement actions, solutions, and assessments, gaining insights into key features and capabilities.

## Task 3 - Create an assessment

1. You should still be logged in with Joni's account and logged into the **Compliance Manager** within the Microsoft Purview compliance portal.

1. Select **Assessments** from the top navigation breadcrumb.

1. Select **+ Add assessments** to launch the assessment creation wizard.

1. On the **Base your assessment on a regulation** page, select **Select regulation**.

1. On the **Select regulation** fly out page, search for *Gramm*.

1. Select the checkbox next to **GGramm-Leach-Bliley Act, Title V, Subtitle A, Financial Privacy**  then select **Save**.

1. Back on the **Base your assessment on a regulation** select **Next**.

1. On the **Add name and group** page under **Assessment name** enter *GLBA Compliance Assessment*.

1. Under **Assessment group** select **Use existing group**, and select the *Default Group*.

1. Select **Next**

1. On the **Select services** page, select **Select services**.

1. On the **Select services** fly out page, select the checkbox next to **Microsoft 365** then select **Add** at the bottom of the page.

1. Back on the **Select services** page select **Next.**

1. On the **Review and finish** page, review your selections then select **Create assessment** at the bottom of the screen.

1. On the **New assessment created** page select **Done** to view your new assessment.

You have successfully created the GLBA Compliance Assessment within Compliance Manager, enabling you to assess Contoso Ltd.'s compliance with the Gramm-Leach-Bliley Act (GLBA) in Microsoft 365.

## Task 4 - Assign improvement action

In this task, you will create a new assessment within Compliance Manager to evaluate Contoso Ltd.'s compliance with the Gramm-Leach-Bliley Act (GLBA). 

1. You should still be logged in with Joni's account and logged into the **Compliance Manager** within the Microsoft Purview compliance portal. You should be on the **GLBA Compliance Assessment** that was created in the previous task.

1. Expand the **Details** and **About** panes on the left to view more information about the assessment that was just created.

1. Select **Your improvement actions** from the top breadcrumb under **GLBA Compliance Assessment**.

1. Explore the **Improvement actions** available to comply with the Gramm-Leach-Bliley Act regulation.

1. In the search bar on the top right of the list of improvement actions search for *DLP*.

1. Select the improvement action for **Use default DLP policies for US Gramm Leach Bliley Act**.

1. On the **Use default DLP policies for US Gramm Leach Bliley Act** page, on the **Overview** pane on the left, select **Assign action** to assign this improvement action to another compliance administrator.

1. On the **Assign to user** fly out page on the right, enter *Megan* in the search field then press enter.

1. Select the check box for **Megan Bowen** then select **Assign** at the bottom of the page to assign this improvement action to Megan Bowen.

1. Back on the **Use default DLP policies for US Gramm Leach Bliley Act** page, you should see this improvement action has been assigned to Megan Bowen.

## Task 5 - Act on improvement action

In this task, you will log into the Client 2 VM (LON-CL2) and navigate to Outlook to access Megan Bowen's email. You will then review and act upon the assigned improvement action in Compliance Manager.

1. Leave Client 1 VM (LON-CL1) open as it is, and log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

1. Open **Microsoft Edge** and navigate to **https://outlook.office.com/**.

1. Log in with Megan Bowen's account, MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Megan's password should be provided by your lab hosting provider.

1. Megan should have an email with the subject **Compliance Manager** in their inbox.

1. Select this message, and click **View Action Item Assigned to you** to open the assigned improvement action.

1. Explore the improvement action. 
    - **Overview**: Contains a **Summary** of basic information such as the implementation and test status, points achieved, and associated assessments; and a **Testing source** section for viewing and changing how the action is tested.

    - **Implementation** tab: Contains implementation status, date, notes, detailed instructions, and for technical actions, a **Launch now** link taking you to the appropriate solution or service for implementation.

    - **Testing** tab: Contains testing status, date, notes, and a link to download a testing history report.

    - **Related controls** tab: Lists the controls associated with the improvement action, including the control ID and the associated regulation. Select a control name to view a flyout pane with a detailed description.

    - **Evidence** tab: Location where you can upload and view files and links related to implementation and testing work.

1. Select the **Implementation** tab, and review the suggested implementation. Scroll down to the bottom of the page, and select **Launch now** under **Prerequisites and licensing requirements**.

1. This will open directly to the **Data loss prevention** page as suggested by the improvement action. Select the **Policies** tab at the top of the page.

1. On the **Policies** page select **+ Create policy**.

1. On the **Start with a template or create a custom policy** page, under **Categories** select **Financial** to open the list of financial DLP policy templates.

1. Under **Templates** select the **U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced** template, then select **Next**.

1. On the **Name your DLP policy** page, leave the default name in the **Name** field, then select **Next**.

1. On the **Assign admin units (preview)** page select **Next**.

1. On the **Choose locations to apply the policy** select **Exchange email**, **SharePoint sites**, **OneDrive accounts**, **Teams chat and channel messages**, and **Devices** then select **Next**.

1. On the **Define policy settings** page, leave the default selected, then select **Next**.

1. On the **Info to protect** page review the information protected then select **Next**.

1. On the **Protection actions** page leave the default selected then select **Next**.

1. On the **Customize access and override settings** page leave the default selected, then select **Next**.

1. On the **Policy mode** page select **Turn it on right away** then select **Next**.

1. On the **Review your policy and create it** page, select **Submit** to create and activate the new DLP policy.

1. On the **New policy created** page select **Done**.

1. Back on the **Data loss prevention** page, you will see a new DLP policy for **U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced** that satisfies the assigned improvement action.

Upon completing the creation and activation of the new DLP policy for **U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced**, you will have satisfied the requirements of the assigned improvement action.

## Task 6 - Update improvement action

In this final task, you will log back into Client 1 VM (LON-CL1) and make necessary updates to the assigned improvement action within Compliance Manager. 

1. Log back into Client 1 VM (LON-CL1). You should still be logged in with Joni's account, viewing the **Use default DLP policies for US Gramm Leach Bliley Act** page.

1. On the **Overview** pane under **Testing source**, select the dropdown for **Select source type** and change the source to **Manual**.

1. Select **Save** in the top right hand corner.

1. From the **Compliance Manager > Improvement actions > Use default DLP policies for US Gramm Leach Bliley Act** bread crumb at the top of the page, select **Improvement actions** to navigate back to the list of improvement actions.

1. Under **Filters** select **Regulations** then select **Gramm-Leach-Bliley Act**. Select **Solutions** then select **Data loss prevention**.

1. With the filters selected, it should be easier to find the improvement action for **Use default DLP policies for US Gramm Leach Bliley Act**. Select the checkbox next to **Use default DLP policies for US Gramm Leach Bliley Act** then select **Export actions** above the filter selections.

1. Open a new Microsoft Edge window or tab and navigate to **https://onedrive.com** and sign in with Joni's account.

1. Select **Upload** from the top navigation buttons, then select **Files**.

1. Select **Downloads** from the explorer window that opens, then select the **ExportActions.xlsx** file that was downloaded in a previous step then select **Open**.

1. Select the **ExportActions.xlsx** file in OneDrive to edit the document.

1. Review the **How to update Actions** tab in the Excel document.

1. In the **Action Update** tab:
    - Update the **implementationStatus** from **NotImplemented** to **Implemented**
    - Update the **Implementation Date** to today's date with a time of 0:0:00
    - Update the **Implementation Notes** to *Action implemented by Megan Bowen*
    - Update the **Test Status** to *InProgress*
    - Update the **Test Date** to a blank value

1. From the top navigation ribbon in Excel, select **File**, then select **Save As**. In the **Save As** pane, select **Download a Copy**. The file will save in the **Downloads** folder of your VM.

1. Navigate back to your Microsoft Purview compliance portal tab or window.

1. You should still have the **Compliance Manager** window open displaying the **Improvement actions** tab with the filters set to easily display the improvement action for **Use default DLP policies for US Gramm Leach Bliley Act**.

1. Select the checkbox next to **Use default DLP policies for US Gramm Leach Bliley Act** then select **Update actions**.

1. In the **Update improvement actions** wizard on the **Complete prerequisites** page, select the checkboxes for **Make sure your improvement actions are associated with at least one assessment.** and **Export improvement actions that need updating in a specifically formatted Excel file.** then select **Next**.

1. On the **Import updated improvement actions** page under **Upload Excel file** select **Browse**.

1. In the explorer window that opens, select **Downloads** from the left navigation pane. Select the **ExportActions** file that was downloaded in a previous step.

    >**Note:** The default download location for Excel 365 is the Downloads folder. The name will likely have a number appended to the end of the file name. For example, your ExportActions file might be named **ExportActions (1).xlsx**. If multiple attempts were made at saving the Excel file, it may have a different number at the end of the file name.

1. Your ExportActions file will be uploaded. If there are no errors with the file, select **Next**. If there are any issues with the file, address the errors stated on this page.

1. On the **Review and finish** page select **Update actions**.

1. On the **Actions updated** page select **Finish**.

1. Back on the **Compliance Manager** page under the **Improvement actions** tab, select **U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced**. Review the changes made in the previous step under the **Implementation** and **Testing** tabs.

You have successfully updated the improvement action.
