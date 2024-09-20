---
lab:
    title: 'Session 4 - Microsoft Purview Adaptive Protection'
    module: 'Learning Objective - Implement Adaptive Protection in Insider Risk Management'
---

# Part 1 Demo 4 - Enable Adaptive Protection

> Note: There isn't much to do in this demo aside from enabling Quick setup. Quick setup takes 72 hours to set up, but after it's set up the option disappears from the portal. In this demo you'll be explaining some elements of Adaptive Protection in the portal and explaining what happens when you use quick setup.

## Task 1 – Explore Adaptive Protection

In this task, you'll explore Adaptive Protection in Microsoft Purview Insider Risk Management. You'll explore Quick and Custom setup options, customizable risk levels, settings for past activity detection, and risk level timeframes. You'll also review tabs that display user-specific risk levels and DLP policies and learn where in the portal to enable or disable the Adaptive Protection feature.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Navigate to insider risk management by selecting **Solutions** from the left sidebar, then select **Insider Risk Management**.

1. When you first select the **Adaptive protection (preview)** button from insider risk management, you'll see two options to turn on Adaptive protection:

    ![Screenshot of options to get started with Adaptive protection.](../Media/turn-on-adaptive-protection.png)

1. There are two options to get started: **Quick setup** or **Custom setup**. Quick setup is the fastest way to get started. You don't need any pre-existing DLP or insider risk management policies to get started. Custom setup gives you more control over your policies and is recommended if you have existing DLP and insider risk management policies. Quick setup takes about 72 hours to get started while custom setup takes about 36 hours.

1. From the left navigation pane within the **Adaptive protection** window select **Risk levels for Adaptive Protection**.

1. Explore the customizable risk levels in Adaptive protection:

    - **Elevated risk level**: Flags users with high-severity alerts or multiple high-risk activities.
    - **Moderate risk level**: Focuses on users with medium-severity alerts or at least two high-risk data exfiltrations.
    - **Minor risk level**: Addresses users with low-severity alerts or a single high-risk data exfiltration.

1. Notice that each risk level has customization options accessible by selecting the **Edit** button next to it.

1. Explore the options for **Past activity detection**, **Risk level timeframe**, and **Insider risk level timeframe**:

    - **Past activity detection**: Specifies the look-back period, between 5 and 30 days, to evaluate if a user's daily actions meet risk level conditions.
    - **Risk level timeframe**: Determines the duration, between 5 and 30 days, a risk level stays assigned to a user before automatic reset.
    - **Insider risk level expiration**: By default, Adaptive Protection risk levels for a user automatically expire when the associated alert is dismissed or the case is closed. If you want to prevent this automatic expiration and keep the risk levels active, you can disable this option.

1. Once you're finished reviewing the options in the **Risk levels for Adaptive Protection** tab, select the **Users assigned risk levels** tab from the left navigation pane.

1. When active, the **Users assigned risk levels** tab will show you each user's name or an anonymized version, their current risk level, time since assignment, and days until auto-reset. You can manually expire a risk level without removing existing alerts or cases. The tab also shows the number of current alerts and confirmed cases for each user.

1. Once you're finished exploring the **Users assigned risk levels** tab, select the **Conditional Access** tab from the left navigation pane.

   Adaptive Protection in Microsoft Purview integrates with Conditional Access to dynamically apply security policies based on a user's risk level. In the **Conditional Access** tab, you'll see policies that enforce specific controls, such as blocking high-risk users from accessing certain applications or requiring low-risk users to acknowledge terms of use before proceeding.

1. Once you're finished exploring the **Conditional Access** tab, select the **Data Loss Prevention** tab from the left navigation pane.

   Adaptive Protection integrates with Data Loss Prevention (DLP) to automatically apply DLP policies based on a user's risk level, such as blocking high-risk users from sharing sensitive data. In the **Data Loss Prevention** tab, you'll see policies that dynamically adjust protection controls based on the insider risk levels assigned to users.

1. Once you're finished exploring the **DLP policies** tab, select the **Adaptive Protection settings** tab from the left navigation pane.

1. In the **Adaptive Protection settings** tab, you can toggle the feature on or off. Turning it off stops assigning risk levels and resets existing ones, taking up to 6 hours for complete deactivation. Policies aren't automatically deleted.

1. Navigate back to the **Dashboard**.

1. Select **Quick setup** to turn Adaptive Protection **On**. This process will take 72, during which analytics are processed, and insider risk levels, DLP, Conditional Access, and data lifecycle management policies are created and applied to user activities. After a few moments you should get a message stating **We're getting things set up...**

You have successfully explored Adaptive Protection and used Quick setup to enable Adaptive Protection.
