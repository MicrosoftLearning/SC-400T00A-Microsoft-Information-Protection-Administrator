---
lab:
    title: 'Exercise 3 - Manage DLP Reports'
    module: 'Module 2 - Implement Data Loss Prevention'
---

# Lab 2 - Exercise 3 - Manage DLP Reports

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. You are informed that a new compliance officer will help you review DLP reports.

### Task 1 - Grant access to DLP reports

In this exercise, you will grant the new compliance officer Megan Bowen access to the DLP reports. As a non-technical user this compliance officer will only read reports and not change the DLP configuration.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

1. In the left navigation pane, select **Permissions** and then under **Microsoft Purview solutions** select **Roles**.   Select the field for the **Security Reader** role.

1. In the *Security Reader* pane, select **Edit** in the **Members** area.

1. Select **Choose members** and then select **+ Add**.

1. Search for **Megan Bowen** and select the checkbox in front of their name, then select **Add**.

1. Review the changes to the member list and then select **Done**.

1. Select **Save**. Close the **Security Reader** role pane.

You have now granted the new compliance officer access to the DLP reports in the Microsoft 365 compliance portal.

### Task 2 - Test access to DLP reports

In this task, you will test that the access to the DLP reports you granted in Task 1 is applied correctly.

1. Log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Megan's password should be provided by your lab hosting provider.

1. In the left navigation pane, select **Reports** and observe your access to the Reports Dashboard.

    **Warning**: If you get a message displayed with an error, come back at a later point of the lab to view the reporting section. You can also perform these steps in a trial or your personal developers tenant.

    [//]: <> (An error message is displayed in the lab tenants when accessing the reports section. The task works in our lab tenants though.)

1. Scroll down to the **Organizational data** section and select **DLP Policy Matches** to review the matches of the DLP policies in the lab tenant.

1. Select **Reports** again, scroll down to the **Organizational data** section and select **DLP Incidents** and **DLP false positives and overrides** one after another and review the reports data. 

1. After reviewing the reports, select **Data loss prevention** from the left side navigation pane and select **Activity explorer**.

1. Work with the filters to display the DLP related activities in your tenant.

1. Leave the client open to finish this last exercise.

You now verified that the access has been configured and the new compliance officer can view reports in the Purview portal.

## You have completed the Lab 2. Proceed to Lab 3 - Exercise 1.
