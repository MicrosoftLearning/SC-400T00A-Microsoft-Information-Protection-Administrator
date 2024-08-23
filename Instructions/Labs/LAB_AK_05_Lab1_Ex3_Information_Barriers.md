---
lab:
    title: 'Exercise 3 - Configure Information Barriers'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

# Lab 5 - Exercise 3 - Configure Information Barriers

As Joni, the Compliance Administrator for Contoso Ltd., your responsibility is to configure and manage Information Barriers in Microsoft 365. Information Barriers play a critical role in maintaining clear boundaries and preventing unauthorized communication between specific groups or individuals within your organization. By implementing Information Barriers, you ensure compliance with regulations, protect sensitive information, and minimize conflicts of interest. This setup will create a secure work environment, safeguarding data confidentiality and supporting Contoso Ltd.'s commitment to compliance.

1. Verify search by name is enabled in Microsoft Teams
1. Segment users in your organization
1. Create information barrier policies
1. Apply Information barrier policies

## Task 1 – Verify search by name is enabled in Microsoft Teams

In this task, you'll verify the **Search by name** feature is enabled in Microsoft Teams. This feature allows users to search and find specific individuals within their organization easily. By following the steps provided, you will configure and activate this feature to enhance collaboration and streamline communication within your organization's Microsoft Teams environment.

1. Log into the Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account.

1. If you're still signed in with Joni's account, sign out of this account and close all browser windows.

1. In **Microsoft Edge**, navigate to **`https://admin.teams.microsoft.com`** and log into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. In the left navigation pane, under the **Teams** dropdown, select **Teams settings**

1. Scroll down to **Search by name**. If this feature is set to Off, toggle this feature **On**, then select **Save** to save this setting.

1. On the **Changes will take time to take effect** pop up select **Confirm**

    >**Note:** It may take a few hours for this change to take effect.

## Task 2 – Segment users in your organization

In this task, you will use PowerShell to connect to the Security & Compliance module and create organization segments for the **Legal** and **Marketing** departments.

1. Open an elevated PowerShell window by right clicking the Windows button in the task bar, then select **Terminal (Admin)**.

1. In the terminal window, enter the cmdlet to connect to the Security & Compliance PowerShell.

    ````powershell
    Connect-IPPSSession
    ````

    Sign in as **Joni Sherman** `JoniS@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password was set in a previous exercise.

1. Run the **New-OrganizationSegment** cmdlet with the **UserGroupFilter** parameter to create a **Legal** segment:

    ````powershell
    New-OrganizationSegment -Name "Legal" -UserGroupFilter "Department -eq 'Legal'"
    ````

1. Run the **New-OrganizationSegment** cmdlet again to create a **Marketing** segment:

    ````powershell
    New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"
    ````

1. Run the **Get-OrganizationSegment** cmdlet to view the segments that were created.

    ````powershell
    Get-OrganizationSegment
    ````

You have successfully connected to the Security & Compliance PowerShell, created organization segments for the Legal and Marketing departments, and viewed the segments using the Get-OrganizationSegment cmdlet.

## Task 3 – Create information barrier policies

In this task, you will use PowerShell to create Information barrier policies to block communication between the Legal and Marketing departments.

1. The elevated PowerShell window should still be open.

1. Run the **New-InformationBarrierPolicy** cmdlet with the **SegmentsBlocked** parameter to create a new **Legal-Marketing** policy:

    ````powershell
    New-InformationBarrierPolicy -Name "Legal-Marketing" -AssignedSegment "Legal" -SegmentsBlocked "Marketing" -State Active
    ````

1. When the notice on Information barriers policy warning is displayed in PowerShell type **Y** then press **Enter** to proceed with creating the policy.

1. Now an information barrier policy must be created to block in the opposite direction. Run the **New-InformationBarrierPolicy** cmdlet with the **SegmentsBlocked** parameter to create a new **Marketing-Legal** policy:

    ````powershell
    New-InformationBarrierPolicy -Name "Marketing-Legal" -AssignedSegment "Marketing" -SegmentsBlocked "Legal" -State Active
    ````

1. Run the **Get-InformationBarrierPolicy** cmdlet to view the policies that were created.

    ````powershell
    Get-InformationBarrierPolicy
    ````

    >**Note:** Ensure the policies are marked as **Active** when reviewing the policies that were created. Information barrier policies must be active before they are applied.

You have successfully created the Legal-Marketing and Marketing-Legal information barrier policies using PowerShell and verified their status as active by running the Get-InformationBarrierPolicy cmdlet.

## Task 4 – Apply Information barrier policies

In this task, you will use PowerShell to apply the active Information barrier policies and check their application status.

1. The elevated PowerShell window should still be open.

1. Run the **Start-InformationBarrierPoliciesApplication** cmdlet to apply the active Information barrier policies:

    ````powershell
    Start-InformationBarrierPoliciesApplication
    ````

1. Run the **Get-InformationBarrierPoliciesApplicationStatus** cmdlet to view the applied policies.

    ````powershell
    Get-InformationBarrierPoliciesApplicationStatus
    ````

    >**Note:** Allow 30 minutes for the system to start applying the policies.

1. Once the policy is applied, the **Status** will update from **NotStarted** to **Completed**.

You have successfully applied the Information barrier policies by running the Start-InformationBarrierPoliciesApplication cmdlet and verified their application status using the Get-InformationBarrierPoliciesApplicationStatus cmdlet.
