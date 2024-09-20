---
lab:
    title: 'Session 7 - Mitigate AI Threats with Insider Risk Management'
    module: 'Learning Objective - Create policies with the risky browser usage template'
---

# Part 2 Demo 7 - Create an Insider Risk Management policy using the risky browser usage template

Contoso Ltd. is expanding its use of AI technologies and has observed employees visiting potentially risky websites while researching AI projects. To address this, they are implementing a Risky Browser Usage policy in Microsoft Purview’s Insider Risk Management to monitor web activity, flag risky behavior, and prevent potential data breaches. As Compliance Administrator, Joni Sherman is responsible for configuring this policy to ensure sensitive data is protected while allowing employees to safely conduct AI research.

## Task 1 – Configure insider risk settings

In this task, you'll customize the insider risk management settings in the Microsoft Purview portal. These settings will help monitor risky browsing behavior, providing visibility into potential threats and helping prevent data breaches.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Settings** from the left sidebar.

1. On the **Settings** page, select **Insider risk management** from the left sidebar.

1. On the left panel of the **Insider Risk Management settings** page, select **Policy indicators**.

1. On the **Policy indicators** settings panel, expand **Risky browsing indicators (preview)**, then select the checkbox for **Select all**.

1. Scroll to the bottom of the **Policy indicators** panel and select **Save**.

You have successfully configured the Insider Risk Management settings to track risky browsing behavior related to AI research and other activities.

## Task 2 – Create an insider risk policy

In this task, you will create an Insider Risk Management policy to monitor and protect against risky browsing activities that could expose sensitive information. This policy will help detect potentially harmful web activity and prevent sensitive data from being compromised while allowing employees to continue using AI tools safely.

1. In the Microsoft Purview portal, select **Solutions** from the left sidebar, then select **Insider Risk Management**.

1. Select **Policies** from the left sidebar, then select **+ Create policy**.

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

    >**Note:** As noted on this page, it might take up to 24 hours before policy matches will start showing up in the Alerts tab.

you have successfully created the **Sensitive Data Protection** policy, which will monitor risky browsing activity related to AI projects. The policy will flag potential insider threats and help prevent sensitive data from being exposed to unauthorized platforms. Keep in mind that it might up to 24 hours for alerts to appear in the system.
