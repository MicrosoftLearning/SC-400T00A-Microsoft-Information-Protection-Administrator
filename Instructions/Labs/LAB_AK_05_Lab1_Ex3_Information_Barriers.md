---
lab:
    title: 'Exercise 3 - Configure Information Barriers'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

# Lab 5 - Exercise 3

As Joni, the Compliance Administrator for Contoso Ltd., your responsibility is to configure and manage Information Barriers in Microsoft 365. Information Barriers play a critical role in maintaining clear boundaries and preventing unauthorized communication between specific groups or individuals within your organization. By implementing Information Barriers, you ensure compliance with regulations, protect sensitive information, and minimize conflicts of interest. This setup will create a secure work environment, safeguarding data confidentiality and supporting Contoso Ltd.'s commitment to compliance.

## Task 1: Verify search by name is enabled in Microsoft Teams

In this task, you'll verify the **Search by name** feature is enabled in Microsoft Teams. This feature allows users to search and find specific individuals within their organization easily. By following the steps provided, you will configure and activate this feature to enhance collaboration and streamline communication within your organization's Microsoft Teams environment.

1. If you're still signed in with Joni's account, sign out of this account and close all browser windows.

1. In **Microsoft Edge**, navigate to **https://admin.teams.microsoft.com** and log into the Microsoft Purview portal as the MOD Administrator, admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. In the left navigation pane, under the **Teams** drop down, select **Teams settings**

1. Scroll down to **Search by name**. If this feature is set to Off, toggle this feature **On**, then select **Save** to save this setting.

1. On the **Changes will take time to take effect** pop up select **Confirm**

    >**Note:** It may take a few hours for this change to take effect.

## Task 2: Enable Admin Consent for Information barriers in Microsoft Teams

In this task, you'll enable Admin Consent for Information Barriers (IB) in Microsoft Teams. This configuration ensures compliance by allowing the removal of non-IB compliant users from groups like Teams channels.

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**.

1. Confirm the **User Account Control** window with **Yes**.

1. Enter the following cmdlet to install the latest version of the Azure AD module:

    ```powershell
    Install-Module AzureAD
    ```

1. Confirm the NuGet provider security dialog with **Y** for Yes and press **Enter**. This process may take some seconds to complete.

1. Confirm the Untrusted repository security dialog with **Y** for Yes and press **Enter**.  This process may take some seconds to complete.

1. Run the following PowerShell cmdlets:

    ````powershell
    Connect-AzureAD -Tenant "<WWLxZZZZZZ>"
    $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
    $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
    if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
    Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
    ````

    >**Note:** Be sure to update ZZZZZZ. ZZZZZZ is your unique tenant ID provided by your lab hosting provider.

1. When prompted, login with the MOD Administrator account

1. In the **Permissions requested** dialog box, review the information, and then select **Accept**.

## Task 3: Segment users in your organization

In this task, you'll use PowerShell to segment users in your organization. By following the provided steps, you'll create segments named **Legal** and **Marketing** based on specific department criteria. PowerShell enables efficient and scalable user management, allowing you to customize and organize your user base effectively.

1. The elevated powershell window should still be open.

1. In the **PowerShell** window, enter the cmdlet to connect to the Security & Compliance PowerShell

    ````powershell
    Connect-IPPSSession
    ````

    and sign in as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

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

## Task 4: Create Information barrier policies

In this task, you'll use PowerShell to create information barrier policies. By following the provided steps, you'll create a policy named **Marketing-LegalFinance** and define the allowed and blocked segments. PowerShell provides a flexible and efficient way to manage policies, allowing you to customize information flow within your organization.

1. The elevated powershell window should still be open.

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

## Task 5: Apply Information barrier policies

1. The elevated powershell window should still be open.

1. Run the **Start-InformationBarrierPoliciesApplication** cmdlet to apply the active Information barrier policies:

    ````powershell
    Start-InformationBarrierPoliciesApplication
    ````

1. Run the **Get-InformationBarrierPoliciesApplicationStatus** cmdlet to view the applied policies.

    ````powershell
    Get-InformationBarrierPoliciesApplicationStatus
    ````

>**Note:** Allow 30 minutes for the system to start applying the policies.