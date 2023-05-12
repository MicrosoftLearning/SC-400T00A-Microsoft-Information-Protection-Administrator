---
lab:
    title: 'Exercise 2 - Configure Insider Risk Management'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

# Lab 5 - Exercise 2

As Joni Sherman, you are the Compliance Administrator at Contoso Ltd. One of your responsibilities is to configuring and managing Microsoft Insider Risk Management to ensure data privacy and prevent policy violations. Leveraging this solution, you proactively monitor user activities, detect anomalies, and mitigate insider threats. 

## Task 1: Insider Risk Settings Configuration

In this lab, you will focus on configuring the insider risk settings in Microsoft Insider Risk Management. These settings apply to all insider risk management policies and can be accessed using the Insider risk settings control located at the top of the insider risk management pages. By following the provided steps, you will fine-tune these settings to optimize your organization's risk management and strengthen security measures against potential insider threats.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. Select **Insider Risk Management** from the left navigation bar

1. Select the gear icon on the top right for **Settings**

1. On the **Settings** page review each of the settings available. Key settings are for **Privacy**, showing anonymized versions of usernames, **Policy indicators** to select indicators that trigger alerts for specific risk activities, and **Priority user groups** allowing for closer scrutiny of user activities based on factors such as their role, access level to sensitive information, or past risk history.

1. Select **Privacy** from the insider risk management settings bar under **General**

1. Select **Do not show anonymized versions of usernames**

1. Select **Save** to save this setting

1. Select **Policy indicators** from the insider risk management settings bar under **General**

1. On the **Policy indicators** settings pane, under **Office indicators** select the check box for **Select all**

1. Scroll down and select **Save**

1. Select **Priority user groups** from the insider risk management settings bar under **General**

1. Select **+Create priority user group** to open the **New priority user group wizard**

1. On the **Name and describe the priority user group** page in the **Name** field enter **Fiance team**. In the **Description** text box enter **Team members that manage financial operations, budgeting, and reporting** then select **Next**

1. On the **Choose members** page select **+Choose members**

1. On the **Choose members** pane select the check box next to **Lynne Robbins**, **Debra Berger**, and **Megan Bowen** then select **Add** to add 3 members

1. On the **Choose members** page select **Next**

1. On the **Choose who can view data involving users in this priority group** select **+Choose users and role groups**

1. On the **Choose users and role groups** page select the checkbox next to **Insider Risk Management** to add all members who have the Insider Risk Management role in Microsoft Purview the select **Add**

1. On the **Choose who can view data involving users in this priority group** select **Next**

1. On the **Review** page select **Submit**

1. On the **Created priority user group** page select **Done**. This will take you back to the insider risk management settings page.

1. Select **Insider risk management** to navigate back to the main Insider risk management page

## Task 2: Insider Risk Policy Creation

In this lab, you will learn how to create an insider risk policy using Microsoft Insider Risk Management. Insider risk management policies determine the scope of users and the configuration of risk indicators for generating alerts. By following the provided steps, you will be able to quickly create a security policy that applies to all users or define individual users or groups, prioritize policy conditions, and customize risk scores and alert thresholds to effectively manage and mitigate insider threats within your organization.

1. You should still be logged in as Joni in Microsoft Purview

1. Select **Insider risk management** from the left navigation bar

1. Select **Policies** from the top navigation bar then select **+Create policy**

1. On the **Choose a policy template** page select **Data leaks** then select **Next**

1. On the **Name your policy page**, in the **Name** field enter **Financial Data Protection** and enter **Sensitive financial data access monitoring** in the **Description** field

1. Select **Next**

1. On the **Choose users and groups** page leave **Include all users and groups** selected, then select **Next**

1. On the **Decide whether to prioritize content page**, leave only **Sharepoint sites** and **File extensions** selected

1. Select **Next**

1. On the **SharePoint sites to prioritize** page select **+Add or edit SharePoint sites**

1. On the Add or edit SharePoint sites pane, scroll down until you see the site for **U.s. Sales**, **https://wwlx420350.sharepoint.com/sites/USSales**, then select **Add**

1. On the **SharePoint sites to prioritize** page select **Next**

1. On the **File extensions to prioritize** page enter **pdf,xls,xlsx,doc,docx** in the field under **Enter up to 50 file extensions** then select **Next**

1. On the **Decide whether to score only activity with priority content** page leave **Get alerts for all activity** selected, then select **Next**

1. On the **Triggers for this policy** page select **User performs an exfiltration activity**

1. Under **Select which activities will trigger this policy** select:
   - **Downloading content from SharePoint**
   - **Sending email with attachments to recipients outside the organization**
   - **Sharing SharePoint files with people outside the organization**

    >**Note**: If you are unable to select policy triggers, you may have a tip to Turn on indicators. If this option is available, select **Turn on indicators**. On the **Choose indicators to turn on** pop up, click the check box next to **Select all** for **Office indicators** then select **Save**

1. Select **Next**

1. On the **Triggering thresholds for this policy** page select **Use default thresholds (Recommended)** then select **Next**

1. On the **Indicators** page, leave the **Total indicators** selected as is, then select **Next**

1. On the **Detection options** page select **Select all** from the **Sequence detection**, **Cumulative exfiltration detection**, and **Risk score boosters** sections, then select **Next**

1. On the **Decide whether to use default or custom indicator thresholds** page select **Default thresholds** then select Next

1. On the **Review settings and finish** page, select **Submit**

1. On the **Your policy was created** page select **Done**.

>**Note:** As noted on this page, it may take up to 24 hours before policy matches will start showing up in the Alerts tab.

