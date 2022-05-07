# Lab 2 - Exercise 3 - Manage DLP reports

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. You are informed that a new compliance officer will help you review DLP reports.

### Task 1 - Grant access to DLP reports

In this exercise, you will grant the new compliance officer access to the DLP reports. As a non-technical user this compliance officer will only read reports and not change the DLP configuration.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft 365 compliance portal as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

3. In the left navigation pane, select **Permissions** and then under **Microsoft Purview solutions** select **Roles**.  Mark the box next to the **Security Reader** role.

4. In the *Security Reader* pane, select **Edit** in the **Members** area.

5. Select **Choose members** and then select **+ Add**.

6. Search for **Megan Bowen** and select the checkbox in front of their name, then select **Add**.

7. Review the changes to the member list and then select **Done**.

8. Select **Save**. Close the **Security Reader** role pane.

You have now granted the new compliance officer access to the DLP reports in the Microsoft 365 compliance portal.

### Task 2 - Test access to DLP reports

In this task, you will test that the access to the DLP reports you granted in Task 1 is applied correctly.

1. Log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft 365 compliance portal as **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Megan's password should be provided by your lab hosting provider.

3. In the left navigation pane, select **Reports** and observe your access to the Reports Dashboard.

You now verified that the access has been configured and the new compliance officer can view reports in the Compliance center.

## You have completed the Lab 2. Proceed to Lab 3 - Exercise 1.
