---
lab:
    title: 'Exercise 2 - Configure Insider Risk Management'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

# Lab 5 - Exercise 2 - Configure Insider Risk Management

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. Your role involves ensuring regulatory compliance and protecting sensitive information within the organization. Recently, Contoso Ltd. has recognized the need to proactively address insider risks that could potentially harm the company's reputation, compromise data security, or lead to legal issues.

To effectively manage insider risks, you implement Microsoft Purview Insider Risk Management, a comprehensive solution designed to identify, analyze, and respond to potential insider threats.

## Task 1 – Assign Insider Risk Management Role

In this exercise, you will assign the Insider Risk Management role to Joni to grant access to perform insider risk tasks in the Microsoft Purview portal.

<!--
1. Sign in to the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In Microsoft Edge, navigate to **https://purview.microsoft.com** and sign in to the Microsoft Purview portal as MOD Administrator, **admin@WWLxZZZZZZ.onmicrosoft.com** (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin’s password should be provided by your lab hosting provider.
-->

1. From the same regular browser window signed in as **MOD Administrator**, go to your Purview tab. If closed, go to https://purview.microsoft.com in a new tab.

1. Select **Settings** from the left navigation.

1. Select **Roles and scopes**, then **Role groups** from the submenu.

1. Find and select **Insider Risk Management** from the list by searching or by sorting the **Name** column.

1. Select **Edit** from the **Insider Risk Management** flyout page on the right.

1. On the **Edit members of the role group** page select **+ Choose users**.

1. In the **Choose users** page select the check box next to Joni Sherman then select the **Select** button.

1. On the **Edit members of the role group** page select **Next**.

1. On the **Review the role group and finish** page select **Save**.

1. On the **You successfully updated the role group** page select **Done**.

1. Sign out of the **MOD Administrator** account and close all browser windows.

You have successfully assigned the Insider Risk Management role to Joni Sherman, granting her access to perform insider risk tasks in the Microsoft Purview portal.

## Task 2 – Insider Risk Settings Configuration

In this task, you will customize the Insider risk management settings in the Microsoft Purview portal. This will allow Joni Sherman to effectively manage potential insider risks within the organization and ensure the security of sensitive information.

1. In **Microsoft Edge**, navigate to **https://purview.microsoft.com** and sign in to the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Settings** from the left navigation bar.

1. Under **Solution settings**, select **Insider Risk Management**.

1. Explore the settings:

    - **Analytics**: Assesses potential insider risks without configuring policies to guide policy creation.
    - **Data sharing**: Exports risk alert information to SIEM solutions using Office 365 Management Activity APIs.
    - **Inline alert customization**: Allows policy tuning and threshold adjustment directly from the Alerts dashboard.
    - **Intelligent detections**: Controls alert volume, excludes certain entities from risk scoring and allows filtering of Microsoft Defender alerts.
    - **Microsoft Teams**: Enables Microsoft Teams for collaboration on insider risk management cases.
    - **Notifications**: Automatically sends email notifications to insider risk management role groups.
    - **Policy indicators**: Involves configuring the policy template using specific risk indicators.
    - **Policy timeframes**: Defines review periods triggered by policy matches based on events and activities.
    - **Power Automate flows (preview)**: Automates insider risk management tasks using Microsoft Power Automate flows.
    - **Priority physical assets**: Identifies and monitors access to priority physical assets correlating activity to user events.
    - **Priority user groups**: Determines high-risk users for closer inspection and more sensitive risk scoring.
    - **Privacy**: Allows you to select displaying usernames or anonymized versions in alerts and cases.

1. Select **Privacy** from the settings menu.

1. Select **Do not show pseudonymized versions of usernames**.

1. Select **Save** to save this setting.

1. Select **Policy indicators** from the settings menu.

1. Select **Office indicators**, then select the check box for **Select all**.

1. Scroll down and select **Save**.

1. Select **Priority user groups** from the settings menu.

1. Select **+ Create priority user group** to open the **New priority user group wizard**.

1. On the **Name and describe the priority user group** page enter:

    - **Name**: Finance team
    - **Description**: Team members that manage financial operations, budgeting, and reporting

1. Select **Next**.

1. On the **Members** page select **+ Members**.

1. On the **Members** pane select the check box next to **Debra Berger**, **Lynne Robbins**, and **Megan Bowen** then select **Add** to add 3 members.

1. Select **Next**.

1. On **Choose who can view data involving users in this priority group** select **+ Choose users and role groups**.

1. On the **Choose users and role groups** pane select the checkbox next to **Insider Risk Management** to add all members who have the Insider Risk Management role in Microsoft Purview the select **Add**.

1. Select **Next**.

1. On the **Review** page select **Submit**.

1. On the **Created priority user group** page select **Done**. This will take you back to the insider risk management settings page.

You have successfully customized the Insider risk management settings. Now, Joni Sherman has the necessary tools and capabilities to proactively identify and mitigate insider risks, safeguarding valuable data in the Microsoft Purview portal.

## Task 3 – Insider Risk Policy Creation

In this task, you will configure a policy named 'Financial Data Protection' in Microsoft Purview to monitor and protect sensitive financial data access within the organization.

1. You should still be signed in as Joni in Microsoft Purview.

1. Select **Solutions** from the left navigation bar, then select **Insider Risk Management**.

1. Select the **Policies** tab from the left-hand pane.

1. Select **+ Create policy**.

1. On the **Choose a policy template** page select **Data leaks** then select **Next**.

1. On the **Name your policy** page enter:

    - **Name**: Financial Data Protection
    - **Description**: Sensitive financial data access monitoring

1. Select **Next**.

1. On the **Choose users and groups** page, leave **All users, groups, and adaptive scopes** selected, then select **Next**.

1. On the **Exclude users and groups (optional)** page, select **Next**.

1. On the **Decide whether to prioritize content** page, leave only **Sensitive info types** selected then select **Next**.

1. On the **Sensitive info types to prioritize** page select **+ Add or edit sensitive info type**.

1. In the **Add or edit sensitive info types** pane search for _bank_ and select the check box next to **U.S. Bank Account Number** and **International Banking Account Number (IBAN)**. 

1. Search for _credit_ and select the check box next to **Credit Card Number** then select **Add** to add the 3 sensitive info types.

1. On the **Sensitive info types to prioritize** page select **Next**.

1. On the **Decide whether to score only activity with priority content** page leave **Get alerts for all activity** selected, then select **Next**.

1. On the **Triggers for this policy** page select **User performs an exfiltration activity**.

1. Under **Select which activities will trigger this policy** select:

   - **Downloading content from SharePoint**
   - **Sending email with attachments to recipients outside the organization**
   - **Sharing SharePoint files with people outside the organization**
   - **Download from Microsoft 365 location the exfiltrate**

    >**Note**: If you are unable to select policy triggers, you may have a tip to Turn on indicators. If this option is available, select **Turn on indicators**. On the **Choose indicators to turn on** pop up, click the check box next to **Select all** for **Office indicators** then select **Save**.

1. Select **Next**.

1. On the **Choose thresholds for triggering events** page select **Apply built-in thresholds** then select **Next**.

1. On the **Indicators** page, select the drop down for **Physical access indicators** and deselect **Physical access after termination or failed access to sensitive asset** if selected then select **Next**.

1. On the **Detection options** page select **Select all** from the **Sequence detection**, **Cumulative exfiltration detection**, and **Risk score boosters** sections, then select **Next**.

1. On the **Choose threshold type for indicators** page select **Apply thresholds provided by Microsoft** then select **Next**.

1. On the **Review settings and finish** page select **Submit**.

1. On the **Your policy was created** page select **Done**.

    >**Note:** As noted on this page, it may take up to 24 hours before policy matches will start showing up in the Alerts tab.

You have successfully created the 'Financial Data Protection' policy, which will help detect and prevent unauthorized access to sensitive financial information. Keep in mind that it may take up to 24 hours for policy matches to appear in the Alerts tab.

## Task 4 – Create a Notice template

In this task, you will create a notice template in Microsoft Purview's Insider Risk Management, which allows you to automatically send email messages to users when a case is generated for risk activities, serving as reminders or providing information for compliance training.

1. You should still be signed in as Joni in Microsoft Purview in Insider risk management.

1. In the left-hand pane, select **Notice templates**.

1. Select **Create notice template**.

1. Fill out the necessary information in **Create a new notice template** flyout page on the right.

    - **Template name**: Data Leak Policy Alert
    - **Send from**: Joni Sherman
    - **Subject**: Potential Data Leak Detected
    - **Message body**:

        ````html
        <!DOCTYPE html>
        <html>
        <body>
        <h2>Alert: Potential Data Leak Detected</h2>
        <p>We detected a potential data leak associated with your account. As part of our Insider Risk Management policy, we are required to investigate any suspicious activity related to data breaches.</p>
        <p>Please review your recent actions, report any unusual behavior, and refer to the Contoso User Code of Conduct training at <a href='https://contoso.com'>https://contoso.com</a> for more information.</p>
        <p>Thank you for your cooperation,</p>
        <p><em>Human Resources</em></p>
        </body>
        </html>
        ````

1. Select **Create**.

You have successfully created the **Data Leak Policy Alert** notice template, enabling automated notifications to be sent to users when potential data leaks are detected, reinforcing security measures and promoting adherence to the Contoso User Code of Conduct.
