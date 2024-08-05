---
lab:
    title: 'Exercise 2 - Configure Insider Risk Management'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

# Lab 5 - Exercise 2 - Configure Insider Risk Management

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. Your role involves ensuring regulatory compliance and protecting sensitive information within the organization. Recently, Contoso Ltd. has noticed unusual browsing activities that could potentially expose sensitive data. To proactively address this insider risk, you will implement Microsoft Purview Insider Risk Management, focusing on identifying, analyzing, and responding to potential insider threats effectively.

**Tasks**:

1. Assign insider risk management permissions
1. Configure insider risk settings
1. Create an insider risk policy
1. Create a notice template

## Task 1 – Assign insider risk management permissions

In this exercise, you will assign the Insider Risk Management role to Joni to grant access to perform insider risk tasks in the Microsoft Purview portal.

1. Log into the Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. In Microsoft Edge, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as MOD Administrator, **`admin@WWLxZZZZZZ.onmicrosoft.com`** (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Select **Settings** from the left sidebar.

1. Expand **Roles and Scopes** then select **Role groups**.

1. On the **Role groups for Microsoft Purview solutions** page select **Insider Risk Management**.

1. On the **Insider Risk Management** flyout panel on the right, select **Edit** .

1. On the **Edit members of the role group** page select **+ Choose users**.

1. On the **Choose users** flyout panel, search for `Joni` then select the checkbox for **Joni Sherman**.

1. Select the **Select** button at the bottom of the panel.

1. On the **Edit members of the role group** page select **Next**.

1. On the **Review the role group and finish** page select **Save**.

1. Once you have successfully added Joni to the role group, select **Done** on the **You successfully updated the role group** page.

1. Sign out of the Mod Administrator account by selecting the MA icon on the top right of the window, then selecting **Sign out**.

You have successfully assigned the Insider Risk Management role to Joni Sherman, granting her access to perform insider risk tasks in the Microsoft Purview portal.

## Task 2 – Configure insider risk settings

In this task, you will customize the insider risk management settings in the Microsoft Purview portal. This will allow Joni Sherman to effectively manage potential insider risks within the organization and ensure the security of sensitive information.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Settings** from the left sidebar.

1. On the **Settings** page, select **Insider risk management** from the left sidebar.

1. On the **Insider Risk Management settings** page, explore the available settings:

   - **Analytics**: Evaluate potential insider risks without configuring policies.
   - **Data sharing**: Export alert information to SIEM solutions or share user risk levels with Defender and DLP alerts.
   - **Detection groups**: Create detection groups to tailor indicators and reduce false positives.
   - **Global exclusions**: Specify global exclusions that won't be scored by policies.
   - **Inline alert customization**: Quickly adjust policy thresholds or remove activities from policies directly from the Alerts dashboard.
   - **Intelligent detection**s: Boost scores for unusual downloads, control alerts, filter Defender alerts, and specify domains for risk scoring.
   - **Microsoft Teams (preview)**: Enable Teams support for collaborating on insider risk management cases.
   - **Notifications**: Automatically send email notifications to selected role groups for alerts.
   - **Policy indicators**: Select specific indicators for insider risk management policies; all are disabled by default.
   - **Policy timeframes**: Define review periods triggered by policy matches based on events.
   - **Power Automate flows (preview)**: Automate tasks for cases and users using Power Automate flows.
   - **Priority physical assets (preview)**: Identify access to priority locations and correlate with user events.
   - **Priority user groups**: Define high-risk users for closer inspection and sensitive risk scoring.
   - **Privacy**: Choose to display usernames or anonymized versions for policy matches.

1. On the left panel of the **Insider Risk Management settings** page, select **Notifications**.

1. Review the users who will receive alerts for detected activities.

1. On the left panel of the **Insider Risk Management settings** page, select **Privacy**.

1. On the **Privacy** panel, select **Do not show anonymized versions of usernames**, then select **Save**.

1. On the left panel of the **Insider Risk Management settings** page, select **Policy indicators**.

1. On the **Policy indicators** settings panel, expand **Risky browsing indicators (preview)**, then select the checkbox for **Select all**.

1. Scroll to the bottom of the **Policy indicators** panel and select **Save**.

1. On the left panel of the **Insider Risk Management settings** page, select **Priority user groups**.

1. Select **+ Create priority user group** to open the **New priority user group** configuration.

1. On the **Name and describe the priority user group** page enter:

    - **Name**: `Finance team`
    - **Description**: `Team members that manage financial operations, budgeting, and reporting.`

1. Select **Next**.

1. On the **Choose members** page select **+ Choose members**.

1. On the **Choose members** flyout panel, select:

   - `Lynne Robbins`
   - `Debra Berger`
   - `Megan Bowen`

1. Select **Add** at the bottom of the flyout panel to add the 3 members.

1. Back on the **Choose members** page select **Next**.

1. On the **Choose who can view data involving users in this priority group** select **+ Choose users and role groups**.

1. On the **Choose users and role groups** flyout panel, select the checkbox for **Insider Risk Management** to add all members who have the Insider Risk Management role in Microsoft Purview then select **Add**.

1. Back on the **Choose who can view data involving users in this priority group** select **Next**.

1. On the **Review** page select **Submit**.

1. Once you have successfully created the priority group, select **Done** on the **Created priority user group** page.

You have successfully customized the Insider risk management settings. Now, Joni Sherman has the necessary tools and capabilities to proactively identify and mitigate insider risks, safeguarding valuable data in the Microsoft Purview portal.

## Task 3 – Create an insider risk policy

In this task, you will configure a policy named **Sensitive Data Protection** in Microsoft Purview to monitor and protect against risky browsing activities that could expose sensitive information within the organization.

1. You should still be logged into Microsoft Purview with Joni's account on the **Insider Risk Management settings** page.

1. Navigate to insider risk management by selecting **Solutions** from the left sidebar, then select **Insider Risk Management**.

1. On the **Insider Risk Management** page, select **Recommendations** from the left sidebar. Take some time to review this page before creating your first policy.

1. After reviewing the recommendations, select the **Policies** from the left sidebar, then select **+ Create policy**.

1. On the **Choose a policy template** page select **Risky browser usage (preview)** then select **Next**.

1. On the **Name your policy page** enter:

    - **Name**: `Sensitive Data Protection`
    - **Description**: `Monitor and protect against risky browsing activities.`

1. Select **Next**.

1. On the **Choose users, groups, & adaptive scope** page, select **All users, groups, and adaptive scopes**, then select **Next**.

1. On the **Exclude users and groups (optional) (preview)** page, select **Next**.

1. On the **Decide whether to prioritize content page**, select **I don't want to prioritize content right now**, then select **Next**.

1. On the **Choose triggering event for this policy** page, you'll see the indicators you enabled in a previous task. Leave the defaults selected, then select **Next**.

1. On the **Choose thresholds for triggering events** page, select **Apply built-in thresholds**, then select **Next**.

1. On the **Indicators** page, expand **Risky browsing indicators (preview)**, and ensure all indicators are selected. This ensures alerts are generated when these activities are detected.

1. Select **Next**.

1. On the **Choose threshold type for indicators** page, select **Apply thresholds provided by Microsoft**, then select **Next**.

1. On the **Review settings and finish** page, select **Submit**.

1. Once you have successfully created your insider risk policy, select **Done** on the **Your policy was created** page.

    >**Note:** As noted on this page, it may take up to 24 hours before policy matches will start showing up in the Alerts tab.

You have successfully created the **Sensitive Data Protection** policy, which will help detect and prevent risky browsing activities that could expose sensitive information. Keep in mind that it may take up to 24 hours for policy matches to appear in the Alerts tab.

## Task 4 – Create a notice template

In this task, you will create a notice template in Microsoft Purview's Insider Risk Management, which allows you to automatically send email messages to users when a case is generated for risky browsing activities, serving as reminders or providing information for compliance training.

1. You should still be logged in as Joni in Microsoft Purview in insider risk management.

1. Select **Notice templates** from the left sidebar.

1. On the **Notice templates** page, select **+ Create notice template**.

1. Fill out the necessary information in **Create a new notice template** flyout panel on the right.

    - **Template name**: `Risky Browsing Alert`
    - **Send from**: `Joni Sherman`
    - **Subject**: `Risky Browsing Activity Detected`
    - **Message body**:

        ````html
        <!DOCTYPE html>
        <html>
        <body>
        <h2>Alert: Risky Browsing Activity Detected</h2>
        <p>We detected potentially risky browsing activity associated with your account. As part of our Insider Risk Management policy, we are required to investigate any suspicious online behavior that could compromise data security.</p>
        <p>Please review your recent browsing activities, report any unusual behavior, and refer to the Contoso User Code of Conduct training at <a href='https://contoso.com'>https://contoso.com</a> for more information.</p>
        <p>Thank you for your cooperation,</p>
        <p><em>Human Resources</em></p>
        </body>
        </html>
        ````

1. Select **Create**.

1. Back on the **Notice templates** page you'll see the **Risky Browsing Alert** template you just created.

You have successfully created the **Risky Browsing Alert** notice template, enabling automated notifications to be sent to users when risky browsing activities are detected, reinforcing security measures and promoting adherence to the Contoso User Code of Conduct.
