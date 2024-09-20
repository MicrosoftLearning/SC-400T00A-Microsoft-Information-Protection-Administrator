---
lab:
    title: 'Session 8 - AI Hub Insights and Management'
    module: 'Learning Objective - Manage AI Hub policies in Microsoft Purview'
---

# Part 2 - Demo Lab 8 - Activate policies in AI Hub

> Note: There isn't much to do in this demo aside from enabling policies in AH Hub. In this demo you'll be explaining some elements of what you see in the Microsoft Purview portal for AI Hub and enabling policies.

## Task 1 – Activate policies in AI Hub

In this task, you'll explore Adaptive Protection in Microsoft Purview Insider Risk Management. You'll explore Quick and Custom setup options, customizable risk levels, settings for past activity detection, and risk level timeframes. You'll also review tabs that display user-specific risk levels and DLP policies and learn where in the portal to enable or disable the Adaptive Protection feature.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select **Solutions** from the left sidebar, then select **AI Hub (preview)**.

1. Review the **Get started** prerequisites in the portal.

1. From the left sidebar, select **Policies**.

1. On the **Policies** page under **Recommendations**, review the cards to **Fortify your data security for AI** and **Control unethical behavior in AI**.

1. In the **Fortify your data security for AI** card, select **Get started**.

1. Review the **Data security for AI** flyout panel on the right. This panel describes what happens when you create policies for this AI Hub recommendation.

   After selecting **Get started**, a panel outlines the setup of Adaptive Protection and sensitivity label policies. The setup will create an Adaptive Protection policy to block or warn users who attempt to paste or upload sensitive data to third-party AI applications, and apply sensitivity labels to protect content in apps like Outlook and Word. It also explains that existing policies will remain unchanged, and DLP rule matches will be visible in the Activity Explorer.

1. After reviewing this panel, select **Create policies**.

1. Once your policies are created, you'll receive a message displaying **Your policies have been created** with a description of the policies that were created.

1. Close the right flyout panel by selecting the **X** in the top right.

1. Back on the policies page, in the **Control unethical behavior in AI** card, select **Get started**.

1. Review the **Control unethical behavior in AI** flyout panel on the right. This panel describes what happens when you create policies for this AI Hub recommendation.

   This panel provides details about setting up a policy to detect potentially unethical behavior in Microsoft 365 Copilot interactions. The policy will monitor prompts and responses for sensitive information, generating alerts in Communication Compliance for review without affecting end users. You'll be assigned as the reviewer of flagged interactions.

1. After reviewing this panel, select **Create policy**.

1. Once your policies are created, you'll receive a message displaying **Your policy has been created** with a description of the policy that was created.

1. Select **Close** at the bottom of the panel to go back to the **Policies** screen.