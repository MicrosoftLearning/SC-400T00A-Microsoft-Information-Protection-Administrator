---
lab:
    title: 'Exercise 2 - Configure Insider Risk Management'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

<!--
# Exercise 5 - Configure Insider Risk Management
-->
# Exercise 6 – Adaptive Protection

<!-- Need a proper description -->

## Task 1 – Explore Adaptive Protection

In this task, you'll explore Adaptive Protection in Microsoft Purview Insider Risk Management. You'll explore Quick and Custom setup options, customizable risk levels, settings for past activity detection, and risk level timeframes. You'll also review tabs that display user-specific risk levels and DLP policies and learn where in the portal to enable or disable the Adaptive Protection feature.

1. You should still be signed in as **Joni Sherman** in Microsoft Purview in Insider Risk Management.

1. In the left navigation of **Insider Risk Management** select **Adaptive Protection**.

1. You'll see two options to turn on Adaptive protection: **Quick setup** or **Custom setup**.

    ![Screenshot of options to get started with Adaptive protection.](../Media/turn-on-adaptive-protection.png)

    >Quick setup is the fastest way to get started. You don't need any pre-existing DLP or insider risk management policies. Custom setup gives you more control over your policies and is recommended if you have existing DLP and insider risk management policies. Quick setup takes about 72 hours to get started, while custom setup takes about 36 hours.

1. In Adaptive Protection, select the **Insider risk levels** tab.

1. Explore the customizable risk levels in Adaptive protection:

    - **Elevated risk level**: Flags users with high-severity alerts or multiple high-risk activities.
    - **Moderate risk level**: Focuses on users with medium-severity alerts or at least two high-risk data exfiltrations.
    - **Minor risk level**: Addresses users with low-severity alerts or a single high-risk data exfiltration.

1. Notice that each risk level has customization options accessible by selecting the **Edit** button next to it.

    ![Screenshot of Define conditions for risk levels in Adaptive protection](../Media/adaptive-protection-navigation-risk-level-edit.png)

1. Explore the options for **Past activity detection** and **Risk level timeframe**:

    - **Past activity detection**: Specifies the look-back period, between 5 and 30 days, to evaluate if a user's daily actions meet risk level conditions.
    - **Risk level timeframe**: Determines the duration, between 5 and 30 days, a risk level stays assigned to a user before automatic reset.

1. Once you're finished reviewing the options in the **Risk levels for Adaptive Protection** tab, select the **Users assigned insider risk levels** tab from the left navigation pane.

1. When active, this will show you each user's name or an anonymized version, their current risk level, time since assignment, and days until auto-reset. You can manually expire a risk level without removing existing alerts or cases. The tab also shows the number of current alerts and confirmed cases for each user.

1. Once you're finished exploring the **Users assigned insider risk levels** tab, select the **Conditional Access** tab.

    >This page will show each policy's name, current state, location, included risk levels, status, creation date, and last modified date.

1. Once you're finished exploring the **Conditional Access** tab, select the **Adaptive Protection settings** tab.

    ![Screenshot of Adaptive Protection settings selected in Adaptive protection.](../Media/adaptive-protection-settings-selected.png)

1. In the **Adaptive Protection settings** tab, you can toggle the feature on or off. Turning it off stops assigning risk levels and resets existing ones, taking up to 6 hours for complete deactivation. Policies aren't automatically deleted.

You have successfully explored Adaptive Protection in Insider Risk Management.
