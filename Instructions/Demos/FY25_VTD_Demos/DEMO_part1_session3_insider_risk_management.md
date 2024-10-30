---
lab:
    title: 'Session 3 - Insider Risk Management in Microsoft Purview'
    module: 'Learning Objective - Implement Insider Risk Management in Microsoft Purview'
---

# Part 1 Demo 3 - Create an Insider Risk Management policy

After discovering several incidents of inadvertent data sharing and potential insider threats, Contoso Ltd. is using Insider Risk Management in Microsoft Purview. By configuring policies to track and address risky employee behaviors, they aim to watch for risky behaviors and prevent data leaks while staying compliant with security rules.

## Task 1 – Configure insider risk settings

In this task, we will configure key settings in Microsoft Purview's Insider Risk Management module. By adjusting these settings, we ensure Contoso Ltd. can effectively monitor and address insider risks, such as data leaks or unauthorized access to sensitive information.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Settings** from the left sidebar.

1. On the **Settings** page, select **Insider risk management** from the left sidebar.

1. On the left panel of the **Insider Risk Management settings** page, select **Policy indicators**.

1. On the **Policy indicators** settings panel, expand **Office indicators**, then select the checkbox for **Select all**.

1. Next, expand **Device indicators**, then select the checkbox for **Select all**.

1. Scroll to the bottom of the **Policy indicators** panel and select **Save**.

You have successfully configured the Insider Risk Management settings, enabling Microsoft Purview to track and report on risky user behaviors involving Office applications and devices. This setup ensures that Contoso Ltd. can monitor for potential insider threats across common data access points and activities.

## Task 2 – Create an insider risk policy

Now, we will create a policy to detect and respond to risky behaviors, such as exfiltration of financial data. This policy will monitor for sensitive data handling and help Contoso Ltd. prevent data leaks from insider threats.

1. You should still be logged into Microsoft Purview with MOD Admin's account on the **Insider Risk Management settings** page.

1. Navigate to insider risk management by selecting **Solutions** from the left sidebar, then select **Insider Risk Management**.

1. On the **Insider Risk Management** page, select **Policies** from the left sidebar, then select **+ Create policy**.

1. On the **Choose a policy template** page select **Data leaks** then select **Next**.

1. On the **Name your policy page** enter:

    - **Name**: `Financial Data Protection`
    - **Description**: `Sensitive financial data access monitoring.`

1. Select **Next**.

1. On the **Choose users, groups, & adaptive scope** page, select **All users, groups, and adaptive scopes**, then select **Next**.

1. On the **Exclude users and groups (optional) (preview)** page, select **Next**.

1. On the **Decide whether to prioritize content page**, select only **Sensitive info type** and **Trainable classifiers**. Deselect any other options, then select **Next**.

1. On the **Sensitive info types to prioritize** page select **+ Add or edit sensitive info type**.

1. In the **Add or edit sensitive info types** flyout panel search for `bank` and select the checkbox next to **Name** to select all sensitive info types related to banks. Next search for `credit` and select the check box next to **Credit Card Number** then select **Add** to add the sensitive info types.

1. Back on the **Sensitive info types to prioritize** page, select **Next**.

1. On the **Trainable classifiers to prioritize** page, select **Add or edit trainable classifiers**.

1. On the **Add or edit trainable classifiers** fly out panel, search for `fin` and select the trainable classifiers for **Finance**, **Financial statement**, and **Financial Audit Reports**, then select **Add** at the bottom of the flyout panel.

1. Back on the **Trainable classifiers to prioritize** page, select **Next**.

1. On the **Decide whether to score only activity with priority content** page, select the radio button for **Get alerts only for activity that includes priority content**, then select **Next**.

1. On the **Choose triggering event for this policy** page, leave the default selected for **User performs an exfiltration activity**, then select **Next**.

1. On the **Choose thresholds for triggering events** page, leave the default selected, then select **Next**.

1. On the **Indicators** page, leave the default selected, then select **Next**.

1. On the **Detection options** page, leave the default selected, then select **Next**.

1. On the **Choose threshold type for indicators** page, leave the default selected, then select **Next**.

1. On the **Review settings and finish** page, select **Submit**.

1. On the **Your policy was created** page, select **Done**.

    >**Note:** As noted on this page, it may take up to 24 hours before policy matches will start showing up in the Alerts tab.

You have successfully created the Financial Data Protection policy, which will help monitor and prevent unauthorized access to sensitive financial data. This policy will track exfiltration activities and generate alerts for risky behaviors related to financial information handling.
