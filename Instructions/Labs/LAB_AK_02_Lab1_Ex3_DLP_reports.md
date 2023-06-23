---
lab:
    title: 'Exercise 3 - Manage DLP Reports'
    module: 'Module 2 - Implement Data Loss Prevention'
---

# Lab 2 - Exercise 3 - Manage DLP Reports

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. You are informed that a new compliance officer will help you review DLP reports.

## Task 1 - Grant access to DLP reports

In this exercise, you will grant the new compliance officer Megan Bowen access to the DLP reports. As a non-technical user this compliance officer will only read reports and not change the DLP configuration.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

1. In the left navigation pane, expand **Roles & Scopes** then select **Permissions**. Under **Microsoft Purview solutions** select **Roles**.   Select the field for the **Information Protection Analysts** role.

1. In the *Information Protection Analysts* pane, select **Edit** in the **Members** area.

1. On the **Edit members of the role group** page select **+ Choose users**.

1. On the **Choose users** select the check box next to **Megan Bowen**'s account then select **Select**.

1. Back on the **Edit members of the role group** page verify Megan's account is to be added, then select **Next**.

1. On the **Review the role group and finish** select **Save**.

1. On the **You successfully updated the role group** page select **Done**.

You have now granted the new compliance officer access to the DLP reports in the Microsoft 365 compliance portal.

## Task 2 - Test access to DLP reports

In this task, you will test that the access to the DLP reports you granted in Task 1 is applied correctly.

1. Log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Megan's password should be provided by your lab hosting provider.

1. In the left navigation pane, select the drop down for **Data loss prevention** then select **Activity explorer**.

1. On the **Activity explorer** page, select the dropdown for **Built-in filters**.

1. Explore the **DLP policies that detected activities** filter and the **DLP policy rules that detected activities** filter.

1. Leave the client open to finish this last exercise.

You now verified that the access has been configured and the new compliance officer can view reports in the Purview portal.
