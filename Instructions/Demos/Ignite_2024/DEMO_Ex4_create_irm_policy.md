# Exercise 4 - Create an Insider Risk Management Policy

Contoso wants to protect its sensitive data by monitoring risky employee activities, particularly around browsing potentially harmful websites. Recently, there have been concerns about risky browsing that might expose sensitive information. To address this, Contoso plans to set up Insider Risk Management with a focus on detecting unusual browsing activity. The team will start by testing these configurations on a small group before expanding it company-wide. After testing, they’ll activate the policy to monitor risky behavior in real time.

**Tasks**:

1. Assign insider risk management permissions
1. Configure insider risk settings
1. Create an insider risk policy

## Task 1 – Assign insider risk management permissions

In this task, you'll assign the Insider Risk Management role to Joni Sherman, giving her the permissions needed to manage insider risk tasks in Microsoft Purview.

1. In Microsoft Purview, sign out Joni's account by selecting the image for her user icon on the top right of the window, then select **Sign out**

1. Close all browser windows.

1. Reopen Microsoft Edge, and navigate to **`https://purview.microsoft.com`**.

1. Log into the Microsoft Purview portal as MOD Administrator, **`admin@WWLxZZZZZZ.onmicrosoft.com`** (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Select **Settings** from the left sidebar.

1. Expand **Roles and Scopes** then select **Role groups**.

1. On the **Role groups for Microsoft Purview solutions** page select **Insider Risk Management**.

1. On the **Insider Risk Management** flyout page on the right, select **Edit** .

1. On the **Edit members of the role group** page select **+ Choose users**.

1. On the **Choose users** flyout page, search for `Joni` then select the checkbox for **Joni Sherman**.

1. Select the **Select** button at the bottom of the panel.

1. On the **Edit members of the role group** page select **Next**.

1. On the **Review the role group and finish** page select **Save**.

1. Once you have successfully added Joni to the role group, select **Done** on the **You successfully updated the role group** page.

1. Sign out of the Mod Administrator account by selecting the MA icon on the top right of the window, then select **Sign out**.

1. Close all browser windows.

You've successfully assigned the Insider Risk Management role to Joni Sherman. She can now access insider risk tools to manage potential threats within Contoso.

## Task 2 – Configure insider risk settings

Now that Joni has access to Insider Risk Management, you'll configure the necessary settings to ensure that risky browsing activities are detected, and sensitive information stays protected.

1. Reopen **Microsoft Edge**, then navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Settings** from the left sidebar.

1. On the **Settings** page, select **Insider Risk Management** from the left sidebar.

1. On the left panel of the **Insider Risk Management settings** page, select **Policy indicators**.

1. On the **Policy indicators** settings panel, expand **Risky browsing indicators (preview)**, then select the checkbox for **Select all**.

1. Scroll to the bottom of the **Policy indicators** panel and select **Save**.

You've successfully configured the Insider Risk settings, enabling Contoso to monitor risky browsing activities.

## Task 3 – Create an insider risk policy

With the settings configured, you'll now create a policy that detects risky browsing activities. This policy will monitor and alert on actions that could expose sensitive data, such as visiting unauthorized websites.

1. Navigate to insider risk management by selecting **Solutions** from the left sidebar, then select **Insider Risk Management**.

1. Select the **Policies** from the left sidebar, then select **+ Create policy**.

1. On the **Choose a policy template** page select **Risky browser usage (preview)**, then select **Next**.

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

You've successfully created the Sensitive Data Protection policy. Contoso can now detect and manage risky browsing behaviors that may expose sensitive data.
