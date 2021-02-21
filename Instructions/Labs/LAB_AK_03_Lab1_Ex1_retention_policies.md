# Exercise 1 - Configure Retention Policies

Within the following tasks in these exercise labs, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to adhere to state laws, which stipulates that records may be deleted after three years without constituting an offense. 

In order to adhere to this law your organization has created a retention plan to retain all items in the organization for three years.


### Task 1 – Create company-wide Retention Policy

In this exercise you will create a company-wide retention policy, apply a retention period and set the locations that the policy will be applied to.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Compliance Center as **Joni Sherman**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

6. On the **Information Governance** page, in the **Retention** tab, select **+ New retention policy**.

8. On the **Name your policy page**, for the **Name** and **Description** enter the following information:

	- Name: Company Wide
	- Description: All locations except for teams

9. Select the **Next** button.

10. On the **Settings** page, for the **Do you want to retain content** section, enter the following information:

	- **Yes, I want to retain it**: Set to enable
	- For this long... – 3 – Years
	- **Retain the content based on**: When it was last modified

11. Select the **Next** button.

12. On the **Choose locations** page enable the following setting:

	- Apply policy only to content in Exchange email, public folders, Office 365 groups, OneDrive, and SharePoint documents.

13. Select the **Next** button.

14. On the **Review your settings** page, select the **Create this policy** button

You have successfully created a retention policy for the Exchange email, public folders, Office 365 groups, OneDrive, and SharePoint documents locations. This retention policy will retain items in these locations for three years from when the item was last modified date. This can take up to 24 hours to be apply.

### Task 2 – Create location-based Retention Policies with Filter

You will now create a retention policy for the Teams locations. As Teams channels can contain documents, they will all be retained. Your organization has decided that a limited number of users are required to have their Team chats require a retention period.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

3. In the **Compliance Center**, in the left navigation pane, select **Policies** and under **Data** select **Retention**.

4. On the **Information Governance** page, in the **Retention** tab, select **+ New retention policy**.

5. On the **Name your policy** page, for the **Name** and **Description** enter the following information:

	- **Name**: Teams Retention
	- **Description**: Retention for Teams locations

6. Select the **Next** button.

7. On the **Settings** page, for the **Do you want to retain content** section, enter the following information:

	- **Yes, I want to retain it**: Set to enable
	- [For this long] – 3 – [Years]
	- **Retain the content based on**: When it was last modified

8. Select the **Next** button.

9. On the **Choose locations** page enable the following setting:

	- **Let me choose specific locations**

10. Enter the following information

	- **Exchange email** location - **Status**: Disable
	- **SharePoint sites** location - **Status**: Disable
	- **OneDrive accounts** location - **Status**: Disable
	- **Office 365 groups** location - **Status**: Disable
	- **Skype for Business** location - **Status**: Disable
	- **Exchange public folders** location - **Status**: Disable
	- **Teams channel messages** location – **Status**: Enable 
	- **Teams chats location** – **Status**: Enable

11. For the Teams chat location, select the **Choose users** text link

12. On the **Edit locations** page, select the **Chooser users** button

13. In search bar, enter the user: Adele Vance

14. Select the following user that will be display in the results: **Adele Vance**

15. In search bar, enter the user: Pradeep Gupta

16. Select the following user that will be display in the results: **Pradeep Gupta**

17. Select the **Choose** button

18. On the Edit locations page,** a notification will display: **2 users added**

19. Select the **Done** button.

20. On the **Choose locations** page, select the **Next** button

21. On the **Review your settings** page, select the **Create this policy** button

You have successfully created a retention policy for the Teams locations. You set a retention period of three years for all Teams channel locations. You have set a filter for Teams Chat locations to apply only to specific users.

### Task 3 – Create Retention Policy via PowerShell

You will create the same retention policies with PowerShell

1. Log into the Client 2 VM (LON-CL2) as the **lon-cl2\admin** account.

2. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

3. Connect to the Security & Compliance Center in your tenant with the following cmdlet:

    Connect-IPPSSession

4. If prompted with a sign in dialog box, sign in as **MOD Administrator**.

5. Run the following cmdlet to create the first retention policy for all locations except teams:

    New-RetentionCompliancePolicy -Name "Company Wide PS" -ExchangeLocation All -ModernGroupLocation All -PublicFolderLocation All -SharePointLocation All -OneDriveLocation All

6. Run the following cmdlet to set the retention period, using days as units based the on the date modified:
	
    New-RetentionComplianceRule -Name "Company Wide PS Rule" -Policy "Company Wide PS" -RetentionDuration 1095 -ExpirationDateOption ModificationAgeInDays -RetentionComplianceAction Keep

7. Run the following cmdlet to create the second retention policy for Teams locations:

    New-RetentionCompliancePolicy -Name "Teams Retention PS" -TeamsChannelLocation All -TeamsChatLocation "Adele Vance", "Pradeep Gupta"

8. Run the following cmdlet to set the retention period, using days as units:

    New-RetentionComplianceRule -Name "Teams Retention PS Rule" -Policy "Teams Retention PS" -RetentionDuration 1095 -RetentionComplianceAction Keep

You have successfully created retention policies through PowerShell with a retention period of three years.

# Proceed to Exercise 2
