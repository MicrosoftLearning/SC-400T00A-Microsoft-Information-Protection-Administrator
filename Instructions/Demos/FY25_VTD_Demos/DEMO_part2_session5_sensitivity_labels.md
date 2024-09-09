---
lab:
    title: 'Session 3 - Insider Risk Management in Microsoft Purview'
    module: 'Learning Objective - Implement Insider Risk Management in Microsoft Purview'
---

# Demo Lab 4 - Configure Insider Risk Management

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. Your role involves ensuring regulatory compliance and protecting sensitive information within the organization. Recently, Contoso Ltd. has recognized the need to proactively address insider risks that could potentially harm the company's reputation, compromise data security, or lead to legal issues.

To effectively manage insider risks, you implement Microsoft Purview Insider Risk Management, a comprehensive solution designed to identify, analyze, and respond to potential insider threats.

## Task 1: Insider Risk Settings Configuration

In this task, you will customize the Insider risk management settings in the Microsoft Purview portal. This will allow Joni Sherman to effectively manage potential insider risks within the organization and ensure the security of sensitive information.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Insider risk management** from the left navigation bar.

1. Select the gear icon on the top right for **Settings**.

1. Explore the settings:

    - **Privacy**: Allows you to select displaying usernames or anonymized versions in alerts and cases.
    - **Policy indicators**: Involves configuring the policy template using specific risk indicators.
    - **Policy timeframes**: Defines review periods triggered by policy matches based on events and activities.
    - **Intelligent detections**: Controls alert volume, excludes certain entities from risk scoring and allows filtering of Microsoft Defender alerts.
    - **Export alerts**: Exports risk alert information to SIEM and SOAR solutions using Office 365 Management Activity APIs.
    - **Priority user groups**: Determines high-risk users for closer inspection and more sensitive risk scoring.
    - **Priority physical assets (preview)**: Identifies and monitors access to priority physical assets correlating activity to user events.
    - **Power Automate flows (preview)**: Automates insider risk management tasks using Microsoft Power Automate flows.
    - **Microsoft Teams (preview)**: Enables Microsoft Teams for collaboration on insider risk management cases.
    - **Analytics**: Assesses potential insider risks without configuring policies to guide policy creation.
    - **Admin notifications**: Automatically sends email notifications to insider risk management role groups.
    - **Inline alert customization**: Allows policy tuning and threshold adjustment directly from the Alerts dashboard.

1. Select **Privacy** from the Insider risk management settings bar under **General**.

1. Select **Do not show anonymized versions of usernames**.

1. Select **Save** to save this setting.

1. Select **Policy indicators** from the Insider risk management settings bar under **General**.

1. On the **Policy indicators** settings pane, under **Office indicators** select the check box for **Select all**.

1. Scroll down and select **Save**.

1. Select **Priority user groups** from the insider risk management settings bar under **General**.

1. Select **+ Create priority user group** to open the **New priority user group wizard**.

1. On the **Name and describe the priority user group** page enter:

    - **Name**: Finance team
    - **Description**: Team members that manage financial operations, budgeting, and reporting

1. Select **Next**.

1. On the **Choose members** page select **+ Choose members**.

1. On the **Choose members** pane select the check box next to **Lynne Robbins**, **Debra Berger**, and **Megan Bowen** then select **Add** to add 3 members.

1. On the **Choose members** page select **Next**.

1. On the **Choose who can view data involving users in this priority group** select **+ Choose users and role groups**.

1. On the **Choose users and role groups** page select the checkbox next to **Insider Risk Management** to add all members who have the Insider Risk Management role in Microsoft Purview the select **Add**.

1. On the **Choose who can view data involving users in this priority group** select **Next**.

1. On the **Review** page select **Submit**.

1. On the **Created priority user group** page select **Done**. This will take you back to the insider risk management settings page.

1. Select **Insider risk management** to navigate back to the main Insider risk management page.

## Task 2: Insider Risk Policy Creation

In this task, you will configure a policy named 'Financial Data Protection' in Microsoft Purview to monitor and protect sensitive financial data access within the organization.

1. You should still be logged in as MOD Admin in Microsoft Purview.

1. Select **Insider risk management** from the left navigation bar.

1. Select the **Policies** tab from the top navigation bar then select **+ Create policy**.

1. On the **Choose a policy template** page select **Data leaks** then select **Next**.

1. On the **Name your policy page** enter:

    - **Name**: Financial Data Protection
    - **Description**: Sensitive financial data access monitoring

1. Select **Next**.

1. On the **Choose users and groups** page, leave **Include all users and groups** selected, then select **Next**.

1. On the **Decide whether to prioritize content page**, leave only **Sensitive info type** selected then select **Next**.

1. On the **Sensitive info types to prioritize** page select **+ Add or edit sensitive info type**.

1. In the **Add or edit sensitive info types** pane search for _bank_ and select the check box next to **U.S. Bank Account Number** and **International Banking Account Number (IBAN)**. Next search for _credit_ and select the check box next to **Credit Card Number** then select **Add** to add the 3 sensitive info types.

1. Back on the **Sensitive info types to prioritize** select **Next**.

1. On the **Decide whether to score only activity with priority content** page leave **Get alerts for all activity** selected, then select **Next**.

1. On the **Triggers for this policy** page select **User performs an exfiltration activity**.

1. Under **Select which activities will trigger this policy** select:

   - **Downloading content from SharePoint**
   - **Sending email with attachments to recipients outside the organization**
   - **Using a browser to upload files to the web**
   - **Sharing SharePoint files with people outside the organization**
   - **File copied to remote desktop session**

    >**Note**: If you are unable to select policy triggers, you may have a tip to Turn on indicators. If this option is available, select **Turn on indicators**. On the **Choose indicators to turn on** pop up, click the check box next to **Select all** for **Office indicators** then select **Save**.

1. Select **Next**.

1. On the **Triggering thresholds for this policy** page select **Use default thresholds (Recommended)** then select **Next**.

1. On the **Indicators** page, select the drop down for **Physical access indicators** and deselect **Physical access after termination or failed access to sensitive asset** if selected then select **Next**.

1. On the **Detection options** page select **Select all** from the **Sequence detection**, **Cumulative exfiltration detection**, and **Risk score boosters** sections, then select **Next**.

1. On the **Decide whether to use default or custom indicator thresholds** page select **Default thresholds** then select **Next**.

1. On the **Review settings and finish** page, select **Submit**.

1. On the **Your policy was created** page select **Done**.

    >**Note:** As noted on this page, it may take up to 24 hours before policy matches will start showing up in the Alerts tab.

You have successfully created the 'Financial Data Protection' policy, which will help detect and prevent unauthorized access to sensitive financial information. Keep in mind that it may take up to 24 hours for policy matches to appear in the Alerts tab.
