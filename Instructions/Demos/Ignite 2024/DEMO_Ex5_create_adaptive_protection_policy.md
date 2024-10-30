---
lab:
    title: 'Session 4 - Microsoft Purview Adaptive Protection'
    module: 'Learning Objective - Implement Adaptive Protection in Insider Risk Management'
---

# Exercise 5 - Create an Adaptive Protection Policy

Contoso has implemented DLP policies to prevent data from being copied into generative AI platforms. However, the company has identified a need for more dynamic control, ensuring that stricter measures are applied to users who engage in risky behaviors. To address this, Contoso will use Microsoft Purviews Adaptive Protection to automatically adjust the enforcement of DLP policies based on a user's insider risk level, ensuring that users with higher risk face more restrictions while maintaining flexibility for others.

**Tasks**:

- Add the Adaptive Protection condition to a DLP policy
- Enable Adaptive Protection in Insider Risk Management

## Task 1 – Add the Adaptive Protection condition to a DLP policy

Now that Contoso is ready to use Adaptive Protection, you'll begin by adding an adaptive condition to the existing DLP policy. This condition will dynamically adjust the policy's restrictions based on the insider risk levels identified by Insider Risk Management.

1. In **Microsoft Edge**, navigate to DLP by selecting **Solutions** > **Data Loss Prevention**.

1. Select **Policies** from the left sidebar.

1. Select the **Generative AI sharing DLP policy** policy created in a previous exercise, then select the **Edit policy** button.

1. On the **Name your DLP policy** page, select **Next** until you reach the **Customize advanced DLP rules** page.

On the **Customize advanced DLP rules** page, select the pencil icon to edit the **Sensitive data protection rule**.

1. On the **Edit rule** flyout page, in the **Conditions** section, select the dropdown for **+ Add condition**, then select the condition for **Insider risk level for Adaptive Protection is** condition.

   ![Screenshot showing the policy published successfully notification.](/Instructions/Media/dlp-adaptive-protection-condition.png)

1. In the **Insider risk level for Adaptive Protection** is section, select the checkbox for **Elevated risk level**.

1. Select **Save** at the bottom of the **Edit rule** page.

1. On the **Customize advanced DLP rules** page, select **Next** until you reach the **Review and finish** page.

1. On the **Review and finish** select **Submit**, then select **Done** on the **Policy updated** page.

You've successfully configured the DLP policy with Adaptive Protection, allowing it to automatically adjust the enforcement based on a user's risk level, improving data protection without affecting the productivity of low-risk employees.

## Task 2 – Enable Adaptive Protection in Insider Risk Management

In this task, you'll configure Adaptive Protection by setting insider risk levels and enabling Adaptive Protection in Insider Risk Management. This ensures that your DLP policies dynamically adjust based on user behavior and risk levels.

1. In the Microsoft Purview portal, select **Solutions** > **Insider Risk Management**.

1. On the **Insider Risk Management** page, select **Adaptive Protection** from left sidebar.

1. On the **Adaptive Protection** page, select **Insider risk levels** tab on the left.

1. On the **Insider risk levels** page, under **Insider risk policy**, select the **Sensitive Data Protection** policy that was created in a previous task.

1. Use the built-in conditions for the **Conditions for insider risk levels**, and select **Save** at the bottom of the page.

1. Select the **Data Loss Prevention** tab on the left and verify the **Generative AI sharing DLP policy** is available.

1. Select the **Adaptive Protection settings** tab, and toggle the **Adaptive Protection** switch to **On**, then select **Save** at the bottom of the page.

You've successfully enabled Adaptive Protection in Insider Risk Management, ensuring that DLP policies are now dynamically applied based on the risk levels of individual users, enhancing data protection while minimizing interruptions to everyday business operations.
