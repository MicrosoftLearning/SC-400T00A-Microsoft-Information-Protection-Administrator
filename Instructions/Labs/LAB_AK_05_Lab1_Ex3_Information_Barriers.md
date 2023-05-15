---
lab:
    title: 'Exercise 3 - Configure Information Barriers'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---

## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab 5 - Exercise 3

As Joni, the Compliance Administrator for Contoso Ltd., your responsibility is to configure and manage Information Barriers in Microsoft 365. Information Barriers play a critical role in maintaining clear boundaries and preventing unauthorized communication between specific groups or individuals within your organization. By implementing Information Barriers, you ensure compliance with regulations, protect sensitive information, and minimize conflicts of interest. This setup will create a secure work environment, safeguarding data confidentiality and supporting Contoso Ltd.'s commitment to compliance.

## Task 1: Verify search by name is enabled in Microsoft Teams

In this task, you'll verify the **Search by name** feature is enabled in Microsoft Teams. This feature allows users to search and find specific individuals within their organization easily. By following the steps provided, you will configure and activate this feature to enhance collaboration and streamline communication within your organization's Microsoft Teams environment.

1. If you're still signed in with Joni's account, sign out of this account and close all browser windows.

1. In **Microsoft Edge**, navigate to **https://admin.teams.microsoft.com** and log into the Microsoft Purview portal as the MOD Administrator, admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. In the left navigation pane, under the **Teams** drop down, select **Teams settings**

1. Scroll down to **Search by name** toggle this feature **On** to enable this feature

1. Select **Save** to save this setting

1. On the **Changes will take time to take effect** pop up select **Confirm**

## Task 2: Enable Admin Consent for Information Barriers in Microsoft Teams

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

    ```powershell
    Connect-AzureAD -Tenant "<WWLxZZZZZZ>"
    $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
    $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
    if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
    Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
    ```

    >**Note:** Be sure to update ZZZZZZ. ZZZZZZ is your unique tenant ID provided by your lab hosting provider.

1. When prompted, login with the MOD Administrator account

1. In the **Permissions requested** dialog box, review the information, and then select **Accept**.

1. Close the PowerShell window once complete

## Task 3: Segment users in your organization (Portal)

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. On the left navigation pane select **Information barriers** then select **Segments** from the drop down

1. On the **Segments** page select **+ New Segment**

1. On the **Provide a segment name** page enter **Finance** in the **Name** field then select **Next**

1. On the **Add user group filter** page, under **User group filter** select **+ Add** then select **Member of** from the drop down

1. In the **Department** field enter **Finance** then select **Next**

1. Review your settings on the **Summary** page, then select **Submit**

1. On the **Segment created** page select **Done**

1. Back on the **Segments** page select **Refresh** to see the newly created **Finance** segment. Leave this window open, as we will be reviewing the Segments page in an upcoming task.

## Task 4: Segment users in your organization (PowerShell)

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**

1. Confirm the **User Account Control** window with **Yes**

1. In the **PowerShell** window, enter to connect to the Security & Compliance PowerShell
	```powershell
	 Connect-IPPSSession
	 ```
	 and then sign in as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. Run the **New-OrganizationSegment** cmdlet with the **UserGroupFilter** parameter to create a **Legal** segment:

    ```powershell
    New-OrganizationSegment -Name "Legal" -UserGroupFilter "Department -eq 'Legal'"
    ```

1. Run the **New-OrganizationSegment** cmdlet again to create a **Marketing** segment:

    ```powershell
    New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"
    ```

1. Go back to **Microsoft Edge** with the openened **Segments** page and select **Refresh**. You should see the newly created **Legal** and **Marketing** segments on this page.

    >**Note**: If you signed out of the compliance portal, navigate back to **https://compliance.microsoft.com** in **Microsoft Edge** and log in with Joni's account. Navigate to **Information barriers** on the left navigation pane. Select **Segments** from the drop down, and  you should see the newly created **Legal** and **Marketing** segments on this page.

## Task 5: Create information barrier policies (Portal)

1. Ensure you're signed into the Microsoft Purview compliance portal with Joni's account. If not, in **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. In the compliance portal select **Information barriers** from the left navigation pane, then select **Policies**

1. On the **Policies** page select **+ Create Policy**

1. On the **Provide a policy name** page enter **Finance-Legal** then select **Next**

1. On the **Add assigned segment details** page select **+ Choose segment**. In the **Select assigned segment for this policy** pane select **Finance** then select **Add**

1. Back on the *Add assigned segment details** select **Next**

1. On the **Configure communication and collaboration details** select the drop down for **Communication and collaboration** and select the setting for **Blocked**

1. Select **+ Choose segment** and in the **Select segments to allow or block** pane select **+ Legal** then select **Add**

1. Back on the **Configure communication and collaboration details** page select **Next** 

1. On the **Configure policy status** page select the toggle to switch the policy **On** then select **Next**

1. On the **Summary** page review your settings then select **Submit**

1. On the **Policy created** page select **Done**. Leave this window open, as we will be reviewing the Policies page in an upcoming task.

## Task 5: Create information barrier policies (PowerShell)

1. Open an elevated PowerShell window by selecting the Windows button with the right mouse button and then select **Windows PowerShell (Admin)**

1. In the **PowerShell** window, enter to connect to the Security & Compliance PowerShell
	```powershell
	 Connect-IPPSSession
	 ```
	 and then sign in as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. Run the **New-InformationBarrierPolicy** cmdlet with the **SegmentsAllowed** parameter to create a new **Marketing-Legal** policy:

    ```powershell
    New-InformationBarrierPolicy -Name "Marketing-Legal" -AssignedSegment "Marketing" -SegmentsAllowed "Legal","Finance" -State Inactive
    ```

1. When the notice on information barriers policy warning is displayed in PowerShell type **Y** then press **Enter** to proceed with creating the policy

1. 