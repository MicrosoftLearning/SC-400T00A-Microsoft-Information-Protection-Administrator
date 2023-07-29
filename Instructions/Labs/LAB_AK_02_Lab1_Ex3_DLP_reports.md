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

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. In the left navigation pane, expand **Roles & Scopes** then select **Permissions**.

1. On the **Permissions** page under **Microsoft Purview solutions** select **Roles**.

1. On the **Role groups for Microsoft Purview solutions** page select the field for **Information Protection Analysts**.

1. In the **Information Protection Analysts** flyout page select **Edit**.

1. On the **Edit members of the role group** page select **+ Choose users**.

1. On the **Choose users** select the check box next to **Megan Bowen**'s account then select **Select**.

1. Back on the **Edit members of the role group** page verify Megan's account is to be added, then select **Next**.

1. On the **Review the role group and finish** select **Save**.

1. On the **You successfully updated the role group** page select **Done**.

You have now granted the new compliance officer access to the DLP reports in the Microsoft 365 compliance portal.

## Task 2 - Review DLP data in the Activity explorer

In this task, you will test that the access to the DLP reports you granted in Task 1 is applied correctly.

1. Log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the left navigation pane, select the drop down for **Data loss prevention** then select **Activity explorer**.

1. On the **Activity explorer** page, select the dropdown for **Built-in filters**.

1. Explore the **DLP policies that detected activities** filter and the **DLP policy rules that detected activities** filter.

You now verified that the access has been configured and the new compliance officer can view reports in the Purview portal.

## Task 3 - Explore DLP data using PowerShell

In this task, you will review DLP activities via PowerShell.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

1. Enter the following to connect to the Information Protection PowerShell session:

   ``` powershell
   Connect-IPPSSession
   ```

1. Select **+ Use another account** then login with the account **Megan Bowen** MeganB@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Use the `Export-ActivityExplorerData` PowerShell cmdlet to explore the activity explorer from Powershell. The script below is an example that will display a grid view of activities from the most recent week:

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. Explore the data collected from previous labs then close the grid view window.

1. The script below is an example of using the Filter1 parameter to display Endpoint activities from the most recent week:

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -Filter1 @("Workload","Endpoint")-OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. Explore the data collected from previous labs then close the grid view window.

You have successfully reviewed DLP activities as the new compliance officer, Megan Bowen.
