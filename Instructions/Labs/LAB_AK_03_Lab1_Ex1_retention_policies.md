---
lab:
    title: 'Exercise 1 - Configure Retention Policies'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab 3 - Exercise 1 - Configure retention policies

In this lab, you are Joni Sherman, a Compliance Administrator at Contoso Ltd. in Texas. Your task is to implement retention policies to comply with state regulations, which allow records to be deleted after three years. You'll configure various retention policies across the organization to ensure data is managed and retained according to these legal requirements.

**Tasks**:

1. Create a company-wide retention policy
1. Create a Teams retention policy with specific user selection
1. Create a retention policy with PowerShell
1. Create an adaptive retention policy for legal and retail documents
1. Test the adaptive scope policy

## Task 1 – Create a company-wide retention policy

In this task, you'll set up a company-wide retention policy that covers key Microsoft 365 locations, ensuring that all items are retained for three years in compliance with state laws.

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in a previous exercise.

1. Select **Solutions** then select **Data Lifecycle Management**.

1. On the **Data Lifecycle Management** page, on the left sidebar, expand **Policies** then select **Retention policies**.

1. On the **Retention policies** page, select **+ New retention policy**.

1. On the **Name your retention policy** page, enter:

    - **Name**: `Company wide`
    - **Description**: `All locations except for teams`

1. Select the **Next** button.  

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page, select **Static** then select **Next**.

1. In the **Choose where to apply this policy** these locations:

   - Exchange mailboxes
   - SharePoint classic and communication sites
   - OneDrive accounts
   - Microsoft 365 Group mailboxes & sites

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **Custom** from the dropdown list
   - Change the years field to **3**
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Delete items automatically

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created select **Done** on the **You successfully created a retention policy** page.

You have successfully created a retention policy that retains items across key Microsoft 365 locations for three years from the date of last modification. This policy can take up to 24 hours to be applied in your tenant, but you can proceed to the next step.

## Task 2 – Create a Teams retention policy with specific user selection

Next, you'll create a retention policy specifically for Microsoft Teams, applying it to channel messages and select user chats to manage their retention separately from other data. Your organization has decided that a limited number of users are required to have their Team chats require a retention period.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft Purview as **Joni Sherman**.

1. In Microsoft Edge, you should still be on the **Retention policies** page in the Microsoft Purview portal. If not, navigate to **`https://purview.microsoft.com`**, then select **Solutions** and select **Data Lifecycle Management**. Select **Policies** > **Retention policies** from the left sidebar.

1. On the **Retention policies** page, select **+ New retention policy**.

1. On the **Name your retention policy** page, enter:

   - **Name**: `Teams Retention`
   - **Description**: `Retention for Teams locations`

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page, select **Static** then select **Next**.

1. On the **Choose locations to apply the policy** page enable these locations:

   - Teams channel messages
   - Teams chats and Copilot interactions
   - Leave all other locations disabled.

1. For the **Teams chats and Copilot interactions** location, select the **Edit** text link under **All users**

1. On the **Teams chats and Copilot interactions** flyout panel add users:

    - Adele Vance
    - Pradeep Gupta

    >**Note**: By adding these two users the setting for **Included** in **Teams chats** changes from *All teams* to *2 users*.

1. Select **Done** at the bottom of the flyout panel.

1. Back on the **Choose where to apply this policy** page select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **Custom** from the dropdown list
   - Change the years field to **3**
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Delete items automatically

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created select **Done** on the **You successfully created a retention policy** page.

1. Close the browser window.

You have successfully configured a retention policy for Microsoft Teams, ensuring that channel messages and specific user chats are retained for three years.

## Task 3 – Create retention policy with PowerShell

In this task, you'll create the same retention policies using PowerShell, demonstrating how to automate the policy setup process.

1. Log into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**. Select **Yes** if the **User Account Control** dialogue pops up.

1. Run the **Connect-IPPSSession** cmdlet to connect to the Security & Compliance Center in your tenant:

    ```powershell
    Connect-IPPSSession
    ```

1. When prompted with a sign in dialog box, sign in as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.

1. Run the **New-RetentionCompliancePolicy** cmdlet to create the first retention policy for all locations except teams:

    ```powershell
    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
    ```

1. Run the **New-RetentionComplianceRule** cmdlet to set the retention period to 3 years, using days as units based on the date modified:

    ```powershell
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
    ```

1. Run the **New-RetentionCompliancePolicy** cmdlet to create the second retention policy for Teams locations:

    ```powershell
    New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"
    ```

1. Run the **New-RetentionComplianceRule** cmdlet to set the retention period to 3 years, using days as units:

    ```powershell
    New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep
    ```

1. Close the terminal window.

You have successfully created retention policies using PowerShell, mirroring the policies set up through the Microsoft Purview portal.

## Task 4 – Create an adaptive retention policy for legal and retail documents

Now, you'll create an adaptive retention policy for the finance and legal departments, ensuring that all legal-related documents are retained for five years.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. Open Microsoft Edge and navigate to **`https://purview.microsoft.com`**. Verify you're still logged in with Joni's account, then select **Settings** from the left sidebar.

1. On the **Settings** page, expand **Roles and scopes** from the left sidebar, then select **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

1. On the **Name your adaptive policy scope** page enter:

    - **Name**: `Legal Documents Retention`
    - **Description**: `Retention for legal related documents`

1. Select **Next**.

1. On the **Assign admin unit** page select **Next**.

1. On the **What type of scope do you want to create?** page select **Users** then select **Next**.

1. On the **Create the query to define users** page, in the **User attributes** section, ensure these values are selected for the user attribute configuration:

   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Legal` as the **Value**

1. Add a second attribute by selecting **+ Add attribute** on the **Create the query to define users** page. In the new field under the one we just configured, configure these values:

   - Select the dropdown for the query operator and update it from And to **Or**
   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Retail` as the **Value**

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your adaptive scope is created select **Done** on the **Your scope was created** page.

1. Back on the **Adaptive scopes** page, select **Solutions** from the bottom of the left sidebar.

1. Select the tab for **Data Governance** from the top filter buttons.

1. Select the **Data Lifecycle Management** card.

1. On the **Data Lifecycle Management** page, expand **Policies** then select **Retention policies**.

1. On the **Retention policies** page, select **+ New retention policy**.

1. On the **Name your retention policy** page enter:

    - **Name**: `Legal Data Retention`
    - **Description**: `Retention of all documents within the legal and retail departments.`

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

1. On the **Choose adaptive policy scopes** flyout panel select the checkbox for **Legal Documents Retention** then select **Add** at the bottom of the panel.

1. Back on the **Choose locations to apply the policy** enable:

    - Exchange mailboxes
    - OneDrive accounts
    - Leave all other locations disabled.

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **5 years** from the dropdown list
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Do nothing

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your policy is created, select the **Done** button.

1. Once your policy is created select **Done** on the **You successfully created a retention policy** page.

You have successfully applied an adaptive scope to a retention policy, covering legal and retail department documents for five years.

## Task 5 – Test the adaptive scope policy

In this final task, you'll verify the users affected by the adaptive scope and test the new retention policy to ensure it is functioning as expected.

>**Note**: When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**. Select **Yes** if the **User Account Control** dialogue pops up.

1. Run the **Connect-IPPSSession** cmdlet to the Security & Compliance Center in your tenant:

    ```powershell
    Connect-IPPSSession
    ```

1. When prompted with a sign in dialog box, sign in with Joni Sherman's account, JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's account was set in a previous exercise.

1. Run the **Get-RetentionCompliancePolicy** cmdlet to view all details of the adaptive scope policy:

    ```powershell
    Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
    ```

1. Review the results and search for these details:

    - **Enabled**: True
    - **Mode**: Enforce
    - **DistributionStatus**: Success

    ![Screenshot of the results of the Get-RetentionCompliancePolicy cmdlet.](../Media/results-getretentioncompliancepolicy.png)

You have verified the successful implementation of the adaptive scope retention policy, confirming that it is correctly applied and operational.
