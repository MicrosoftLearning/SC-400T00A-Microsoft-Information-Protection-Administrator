# Exercise 6 - Create an Adaptive Protection Policy

Contoso has implemented DLP policies to prevent data from being copied into generative AI platforms. However, the company has identified a need for more dynamic control, ensuring that stricter measures are applied to users who engage in risky behaviors. To address this, Contoso will use Microsoft Purviews Adaptive Protection to automatically adjust the enforcement of DLP policies based on a user's insider risk level, ensuring that users with higher risk face more restrictions while maintaining flexibility for others.

**Tasks**:

1. Enable Adaptive Protection in Insider Risk Management

## Task 1 – Enable Adaptive Protection in Insider Risk Management

In this task, you'll configure Adaptive Protection by setting insider risk levels and enabling Adaptive Protection in Insider Risk Management. This ensures that your DLP policies dynamically adjust based on user behavior and risk levels.

1. In the Microsoft Purview portal, select **Solutions** > **Insider Risk Management**.

1. On the **Insider Risk Management** page, select **Adaptive Protection** from left sidebar.

1. On the **Adaptive Protection** page, select **Insider risk levels** tab on the left.

1. On the **Insider risk levels** page, under **Insider risk policy**, select the **Sensitive Data Protection** policy that was created in a previous task.

1. Use the built-in conditions for the **Conditions for insider risk levels**, and select **Save** at the bottom of the page.

1. Select the **Adaptive Protection settings** tab, and toggle the **Adaptive Protection** switch to **On**, then select **Save** at the bottom of the page.

You've successfully enabled Adaptive Protection in Insider Risk Management.
