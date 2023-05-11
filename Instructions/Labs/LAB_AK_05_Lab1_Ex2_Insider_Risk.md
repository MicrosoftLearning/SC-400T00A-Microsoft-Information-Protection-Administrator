---
lab:
    title: 'Implement and manage Microsoft Purview Insider Risk Management'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

# Lab 5 - Exercise 2

As Joni Sherman, you are the Compliance Administrator at Contoso Ltd. One of your responsibilities is to configuring and managing Microsoft Insider Risk Management to ensure data privacy and prevent policy violations. Leveraging this solution, you proactively monitor user activities, detect anomalies, and mitigate insider threats. 

## Task 1: Insider Risk Settings Configuration

In this lab, you will focus on configuring the insider risk settings in Microsoft Insider Risk Management. These settings apply to all insider risk management policies and can be accessed using the Insider risk settings control located at the top of the insider risk management pages. By following the provided steps, you will fine-tune these settings to optimize your organization's risk management and strengthen security measures against potential insider threats.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. Select **Insider Risk Management** from the left navigation bar

1. Select the gear icon on the top right for **Settings**

1. On the **Settings** page review each of the settings available. Key settings are for **Privacy**, showing anonymized versions of usernames, **Policy indicators** to select indicators that trigger alerts for specific risk activities, and **Priority user groups** allowing for closer scrutiny of user activities based on factors such as their role, access level to sensitive information, or past risk history.

1. Select **Privacy** from the insider risk management settings bar under **General**

1. Select **Do not show anonymized versions of usernames**

1. Select **Save** to save this setting

1. Select **Policy indicators** from the insider risk management settings bar under **General**

1. On the **Policy indicators** settings pane, under **Office indicators** select the check box for **Select all**

1. Scroll down and select **Save**

1. Select **Priority user groups** from the insider risk management settings bar under **General**

1. Select **+Create priority user group** to open the **New priority user group wizard**

1. On the **Name and describe the priority user group** page in the **Name** field enter **Fiance team**. In the **Description** text box enter **Team members that manage financial operations, budgeting, and reporting** then select **Next**

1. On the **Choose members** page select **+Choose members**

1. On the **Choose members** pane select the check box next to **Lynne Robbins**, **Debra Berger**, and **Megan Bowen** then select **Add** to add 3 members

1. On the **Choose members** page select **Next**

1. On the **Choose who can view data involving users in this priority group** select **+Choose users and role groups**

1. On the **Choose users and role groups** page select the checkbox next to **Insider Risk Management** to add all members who have the Insider Risk Management role in Microsoft Purview the select **Add**

1. On the **Choose who can view data involving users in this priority group** select **Next**

1. On the **Review** page select **Submit**

1. On the **Created priority user group** page select **Done**. This will take you back to the insider risk management settings page.