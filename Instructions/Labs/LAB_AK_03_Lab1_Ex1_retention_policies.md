---
lab:
    title: 'Exercise 1 - Configure Retention Policies'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 1 - Configure Retention Policies

In this exercise, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to adhere to state laws, which stipulates that records may be deleted after three years without constituting an offense. 

In order to adhere to this law your organization has created a retention plan to retain all items in the organization for three years.


### Task 1 – Create company-wide Retention Policy

In this exercise you will create a company-wide retention policy, apply a retention period, and set the locations that the policy will be applied to.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In the **Microsoft Purview** portal, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, in the **Retention policies** tab, select **+ New retention policy**.

1. On the **Name your retention policy** page, for the **Name** and **Description** enter the following information:

	- **Name**: Company wide
	- **Description**: All locations except for teams

1. Select the **Next** button.  

1. In the **Choose the type of retention policy to create** area, choose **Static** and select **Next**.

1. In the **Choose locations to apply the policy** area make sure **Exchange mailboxes**, **SharePoint classic and communication sites**, **OneDrive accounts**, and **Microsoft 365 Group mailboxes & sites** are selected and then select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, for the **Retain items for a specific period** section, enter the following information:

	- **Retain items for a specific period**: Choose **Custom** from the drop down list
	- Change the years field to **3**
	- **Start the retention period based on**: When items were last modified
	- **At the end of the retention period**: Delete items automatically

1. Select the **Next** button.

1. On the **Review and finish** page, select the **Submit** button.

1. Once your policy is created, select the **Done** button.

You have successfully created a retention policy for the Exchange email, Microsoft 365 groups, OneDrive, and SharePoint sites locations. This retention policy will retain items in these locations for three years from when the item was last modified date. This policy can take up to 24 hours to be apply in your tenant, but you can proceed to the next step.

### Task 2 – Create location-based Retention Policies with Filter

You will now create a retention policy for the Teams locations. As Teams channels can contain documents, they will all be retained. Your organization has decided that a limited number of users are required to have their Team chats require a retention period.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, in the **Retention policies** tab, select **+ New retention policy**.

1. On the **Name your retention policy** page, for the **Name** and **Description** enter the following information:

	- **Name**: Teams Retention
	- **Description**: Retention for Teams locations

1. Select the **Next** button.

1. In the **Choose the type of retention policy to create** area, choose **Static** and then select **Next**.

1. On the **Choose locations to apply the policy** page, enter the following settings:

	- **Teams channel messages** location – **Status**: On 
	- **Teams chats** location – **Status**: On
	- All other locations should be turned **Off** automatically.
	

1. For the **Teams chat** location, select the **Edit** text link under **All users**

1. On the **Teams chats** pane, add the users: 
    - Adele Vance
    - Pradeep Gupta

    Note: By adding those two users the setting for included in Teams chats changed from "All teams" to just the two users you added.

1. Select **Done**, then select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, for the **Retain items for a specific period** section, enter the following information:

	- **Retain items for a specific period**: Choose **Custom** from the drop down list
	- Change the years field to **3**
	- **Start the retention period based on**: When items were last modified
	- **At the end of the retention period**: Delete items automatically


1. Select the **Next** button.

1. On the **Review and finish** page, select the **Submit** button.

1. When the policy is successfully created, select **Done**.

You have successfully created a retention policy for the Teams locations. You set a retention period of three years for all Teams channel locations. You have set a filter for Teams Chat locations to apply only to specific users.

### Task 3 – Create Retention Policy via PowerShell

You will create the same retention policies with PowerShell

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)** select **Yes** if confronted with a User Account Control window.

1. Connect to the Security & Compliance Center in your tenant with the following cmdlet:

    ```powershell
	Connect-IPPSSession
	```

1. If prompted with a sign in dialog box, sign in as **MOD Administrator** admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

1. Run the following cmdlet to create the first retention policy for all locations except teams:

    ```powershell
	New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -SharePointLocation All -OneDriveLocation All
	```

1. Run the following cmdlet to set the retention period, using days as units based on the date modified:
	
    ```powershell
	New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep
	```

1. Run the following cmdlet to create the second retention policy for Teams locations:

    ```powershell
	New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"
	```

1. Run the following cmdlet to set the retention period, using days as units:

    ```powershell
	New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep
	```

You have successfully created retention policies through PowerShell with a retention period of three years.

### Task 4 – Create Retention Policy with adaptive scope

In this exercise you will create a retention policy for the finance and legal department. The purpose of the policy is to comply with the law, retaining all legal related documents for 5 years. First you will create an adaptive scope including the legal and the retail department, then you will create a retention policy using this scope.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, in the left navigation pane, select **Data lifecycle management**.
1. On the **Data lifecycle management**, in the **Adaptive scopes** tab, select **+ Create scope**.
1. On the **Name your adaptive policy scope** page, for the **Name** and **Description** enter the following information:

	- **Name**: Legal Documents Retention
	- **Description**: Retention for legal related documents

1. Select the **Next** button.
1. On the **What type of scope do you want to create?** page, select **Users**.
1. Select the **Next** button.
1. On the **Create the query to define users** page, under **User attributes** open the drop-down menu for the attribute and select **Department**.
1. Directly next to the attribute field, select **is equal to** as operator.
1. As value enter **Legal**
1. To add a second attribute, select **+ Add attribute** on the **Create the query to define users** page.
1. For the **query operator**, **attribute**, **operator** and **value**, enter following information:
	- **Query operator**: Or
	- **Attribute**: Department
	- **Operator**: is equal to
	- **Value**: Retail
1. Ensure checkboxes are selected next to each value.
1. Select the **Next** button.
1. On the **Review and finish** page, select the **Submit** button.
1. After successful submission, close the page by clicking the **Done** button.

1. In the **Microsoft Purview** portal, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, in the **Retention policies** tab, select **+ New retention policy**.

1. On the **Name your retention policy** page, for the **Name** and **Description** enter the following information:

	- **Name**: Legal Data Retention
	- **Description**: Retention of all documents within the legal and retail departments.

1. Select the **Next** button.

1. In the **Choose the type of retention policy to create** area, choose **Adaptive** and then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page, select **+ Add scopes**.
2. On the new **Choose adaptive policy scopes** page, select **Legal Documents Retention** and then select the **Add** button.

1. Under **Choose locations to apply the policy** enter the following information:

	- **Exchange mailboxes** – **Status**: On
	- **OneDrive accounts** – **Status**: On
	- All other locations should be turned **Off** automatically.
	
1. Select the **Next** button.
1. On the **Decide if you want to retain content, delete it, or both** page, for the **Retain items for a specific period** section, enter the following information:

	- **Retain items for a specific period**: 5 years
	- **Start the retention period based on**: When items were created
	- **At the end of the retention period**: Do nothing

1. Select the **Next** button.

1. On the **Review and finish** page, select the **Submit** button.

1. Once your policy is created, select the **Done** button.
### Task 5 – Test adaptive scope policy

In this exercise you will verify the users affected by the adaptive scope and test the new adaptive retention policy.

Note: When you create and submit a retention policy, it can take up to seven days for the retention policy to be applied.

 1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, in the **Adaptive scopes** tab, select **Legal Documents Retention**.

1. On the new **Legal Documents Retention** page, select the **Scope details**.
1. On the **Legal Documents Retention**  page, you should be able to see all locations affected by the scope.

[//]: <> (Error in Lab tenant: Failed to load data. Please try again)

1. To review the details of the adaptive scope retention policy, open PowerShell window by selecting the Windows button with the right mouse button and then select Windows PowerShell.

1. Connect to the Security & Compliance Center in your tenant with the following cmdlet:

	```powershell
	Connect-IPPSSession
	```
1. If prompted with a sign in dialog box, sign in as MOD Administrator admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password should be provided by your lab hosting provider.
1. Run the following cmdlet to view all details of the adaptive scope policy:
	```powershell
	Get-RetentionCompliancePolicy -Identity "Legal Data Retention" -DistributionDetail | Format-List
	```
1. Review the details. Certain parameters should have following statuses:

	- **Enabled**: True
	- **Mode**: Enforce
	- **DistributionStatus**: Success
