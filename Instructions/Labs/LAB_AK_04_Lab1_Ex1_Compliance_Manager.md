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

## Task 1 - Assign Compliance manager permissions

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

1. Log out of the MOD Administrator account and close all windows.

## Task 2 - Explore Compliance Manager

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

## Task 3 - Create an assessment

1. You should still be logged in with Joni's account and logged into the **Compliance Manager** within the Microsoft Purview compliance portal.

1. Select **Assessments** from the top navigation breadcrumb.

1. Select **+ Add assessments** to launch the assessment creation wizard.

1. On the **Base your assessment on a regulation** page, select **Select regulation**.

1. On the **Select regulation** fly out page, search for *Gramm*

<!--Sure, here's another example scenario:


Your organization is a financial services provider that handles sensitive financial data. You want to ensure that you are compliant with the Gramm-Leach-Bliley Act (GLBA) regulations.


To create an assessment for GLBA, you can use the Compliance Manager templates provided by Microsoft. You can then customize the assessment to fit the specific needs of your organization.


For example, you can create an assessment for the Safeguards Rule, which requires financial institutions to develop, implement, and maintain a comprehensive information security program to protect customer information. You can then create improvement actions for each control in the assessment and test them to ensure compliance.


Remember to regularly review and update your assessment to ensure ongoing compliance with GLBA regulations.>