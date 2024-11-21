# Exercise 5 - Create an Insider Risk Management Policy

Contoso wants to protect its sensitive data by keeping track of risky employee activities, particularly around browsing potentially harmful websites. Recently, there have been concerns about potential risky browsing that might expose sensitive information. To address this, Contoso plans to set up Insider Risk Management with a focus on detecting unusual browsing activity. The team will start by testing these configurations on a small group before expanding it company-wide. After testing, they’ll activate the policy to track risky behavior in real time.

**Tasks**:

1. Configure insider risk settings
1. Create an insider risk policy

## Task 1 – Configure insider risk settings

To help track risky activities that could expose sensitive information, you'll configure the policy indicators used in Insider Risk Management. These settings allow Microsoft Purview to identify potential risky browsing behavior, ensuring sensitive data remains protected.

1. In the Microsoft Purview Portal, select **Settings** from the left sidebar.

1. On the **Settings** page, select **Insider Risk Management** from the left sidebar.

1. On the left panel of the **Insider Risk Management settings** page, select **Policy indicators**.

1. On the **Policy indicators** settings panel, expand **Risky browsing indicators (preview)**, then select the checkbox for **Select all**.

1. Scroll to the bottom of the **Policy indicators** panel and select **Save**.

You've successfully configured the Insider Risk settings, enabling Contoso to track risky browsing activities.

## Task 2 – Create an insider risk policy

With the settings configured, you'll now create a policy that detects potential risky browsing activities. This policy will track and alert on actions that could expose sensitive data, such as visiting unauthorized websites.

1. Navigate to insider risk management by selecting **Solutions** from the left sidebar, then select **Insider Risk Management**.

1. Select the **Policies** from the left sidebar, then select **+ Create policy**.

1. On the **Choose a policy template** page select **Risky browser usage (preview)**, then select **Next**.

1. On the **Name your policy page** enter:

    - **Name**: `Sensitive Data Protection`
    - **Description**: `Track and protect against risky browsing activities.`

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

You've successfully created the Sensitive Data Protection policy. Contoso can now detect and address risky browsing behaviors that may expose sensitive data.
