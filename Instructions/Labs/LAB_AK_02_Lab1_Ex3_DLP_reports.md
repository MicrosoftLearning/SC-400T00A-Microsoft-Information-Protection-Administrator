---
lab:
    title: 'Exercise 3 - Manage DLP Reports'
    module: 'Module 2 - Implement Data Loss Prevention'
---

# Lab 2 - Exercise 3 – Manage DLP reports

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. You are informed that a new compliance officer will help you review DLP reports.

**Tasks**:

1. Grant access to DLP reports
1. Review DLP data in the activity explorer
1. Explore DLP data using PowerShell

## Task 1 – Grant access to DLP reports

In this exercise, you will grant the new compliance officer Megan Bowen access to the DLP reports. As a non-technical user this compliance officer will only read reports and not change the DLP configuration.

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **MOD Administrator** `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Select **Settings** from the left sidebar.

1. On the **Settings** page, expand **Roles and scopes** on the left sidebar, then select **Role groups**.

1. On the **Role groups for Microsoft Purview solutions** page select the checkbox for **Information Protection Analysts**, then select the **Edit** tab from the top navigation bar.

1. On the **Edit members of the role group** page select **+ Choose users**.

1. On the **Choose users** flyout panel, search for `Megan` to find Megan Bowen's account. Select the checkbox for **Megan Bowen**'s account then select the **Select** button at the bottom of the panel.

1. Back on the **Edit members of the role group** page verify Megan's account is displayed, then select **Next**.

1. On the **Review the role group and finish** page select **Save**.

1. On the **You successfully updated the role group** page select **Done**.

1. Sign out of the MOD Administrator account by selecting the **MA** icon in the top right, then selecting **Sign out**.

You have now granted the new compliance officer access to the DLP reports in the Microsoft 365 compliance portal.

## Task 2 – Review DLP data in the activity explorer

In this task, you will test that the access to the DLP reports you granted in Task 1 is applied correctly.

1. Log into the Client 1 VM (SC-400-CL1) as the **SC-400-cl2\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **Megan Bowen** `MeganB@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Megan's password was set in a previous exercise.

1. Select **Solutions** from the left sidebar, then select **Data Loss Prevention**.

1. In the left sidebar, select **Activity explorer**.

1. On the **Activity explorer** page, select the dropdown for **Built-in filters**.

1. Explore the **DLP policies that detected activities** filter and the **DLP policy rules that detected activities** filter.

1. Sign out of Megan's account by selecting the **MB** icon in the top right, then selecting **Sign out**.

You now verified that the access has been configured and the new compliance officer can view reports in the Purview portal.

## Task 3 – Explore DLP data using PowerShell

In this task, you will review DLP activities via PowerShell.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**.

1. Run the **Connect-IPPSSession** cmdlet to connect to the Information Protection PowerShell session:

   ``` powershell
   Connect-IPPSSession
   ```

1. In the **Sign in to your account** dialogue, select **+ Use another account** then login with the account **Megan Bowen** `MeganB@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Run the **Export-ActivityExplorerData** PowerShell cmdlet to explore the activity explorer from PowerShell. The script below is an example that will display a grid view of activities from the most recent week:

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. Explore the data collected from previous labs then close the grid view window.

1. The script below is an example of using the **Filter1** parameter to display endpoint activities from the most recent week:

   ``` powershell
   $StartTime = (Get-Date).AddDays(-7)
   $EndTime = (Get-Date).AddDays(1)
   $Results = Export-ActivityExplorerData -StartTime $StartTime -EndTime $EndTime -Filter1 @("Workload","Endpoint")-OutputFormat JSON
   ($Results.ResultData) | ConvertFrom-Json | select -ExpandProperty SyncRoot | ogv
   ```

1. Explore the data collected from previous labs then close the grid view window.

You have successfully reviewed DLP activities as the new compliance officer, Megan Bowen.
