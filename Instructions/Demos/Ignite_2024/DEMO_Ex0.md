## WWL Tenants - Terms of use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab Setup: Prepare Your Environment for Compliance Administration

In this exercise, you'll configure and prepare your environment for compliance administration. You'll activate key features, set up administrative permissions, and ensure proper configuration of core elements.

**Tasks:**

1. Enable Audit in the Microsoft Purview portal
1. Enable device onboarding
1. Onboard a device to endpoint DLP
1. Set user passwords for lab exercises
1. Explore the Microsoft Purview portal

## Task 1 – Enable Audit in the Microsoft Purview portal

In this task, you'll enable audit logging to track activities across Microsoft 365 services.

1. Sign into Client 1 VM (SC-400-CL1) with the **Admin** account. The password should be provided by your lab hosting provider.

1. Open Microsoft Edge and navigate to the Microsoft Purview portal at `https://purview.microsoft.com`.

1. Sign into the Microsoft Purview portal as the MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin's password can be found in the **Resources** tab of the lab hosting window.

1. In the **Welcome to the new Microsoft Purview Portal!** window, select the checkbox to agree with the terms and conditions, then select **Get started** access the portal.

    ![Screenshot showing the Welcome to the new Microsoft Purview portal screen.](../Media/new-purview-portal-get-started.png)

1. Select **Solutions** from the left sidebar, then select **Audit**.

1. On the **Search** page, select the **Start recording user and admin activity** bar to enable audit logging.

    ![Screenshot showing the Start recording user and admin activity button.](../Media/enable-audit-button.png)

1. Once you select this option, the blue bar will disappear.

You have successfully enabled auditing in Microsoft Purview.

## Task 2 – Enable device onboarding

To support Endpoint DLP policies later in the lab, you need to enable device onboarding in Microsoft Purview. This step ensures devices are ready to track and protect sensitive information.

1. In the Microsoft Purview portal, select **Settings** > **Device onboarding** > **Devices**.

1. On the **Devices** page, select **Turn on device onboarding**.

1. Accept the **Turn on device onboarding** dialog by selecting **OK**.

1. Accept the **Device monitoring is being turned on** dialog by selecting **OK**.

1. Wait for the process to complete. Refresh the page until device onboarding is active.

>[!note]
>This process might take about 5 minutes to complete.

You've successfully enabled device onboarding, preparing the environment to onboard devices and apply endpoint DLP policies.

## Task 3 – Onboard a device to endpoint DLP

With device onboarding enabled, the next step is to onboard a Windows 11 device to apply Endpoint DLP policies. This ensures the device is monitored and protected against data loss.

1. From the **Devices** page, on the left sidebar, expand **Device onboarding**, then select **Onboarding**.

1. On the **Onboarding** page, ensure **Windows 10** is selected as the operating system and **Local Script (for up to 10 machines)** is selected as the deployment method.

1. Select **Download package**.

1. In the **Downloads** dialog, hover over the download, then select the folder icon to **Show in folder**.

   ![Screenshot showing the Show in folder icon.](../Media/show-in-folder.png)

1. Extract the **DeviceComplianceOnboardingPackage** zip-file, then open the extracted folder.

1. Right click the **DeviceComplianceLocalOnboardingScript.cmd** file, select **Show more options**, then select **Properties**.

1. Towards the bottom of the **General** tab of the properties window, in the **Security** section, select **Unblock**, then select **OK** to save this setting.

   ![Screenshot showing the Show in folder icon.](../Media/unblock-file.png)

1. Right click **DeviceComplianceLocalOnboardingScript.cmd**, then select **Run as administrator**.

1. On the **User Account Control** dialogue, select **Yes**.

1. In the **Command Prompt** screen, enter **Y** to confirm.

1. When the script is complete, you'll get a success message and a prompt to **Press any key to continue**. Press any key to close the command line window. It can take a minute to complete the onboarding.

You've successfully onboarded a Windows 11 device, allowing it to be protected by the endpoint DLP policy.

## Task 4 – Set user passwords for lab exercises

In this task, you'll set passwords for the user accounts used in the lab.

1. In Microsoft Edge, navigate to the **Microsoft 365 admin center** at **`https://admin.microsoft.com`**.

1. From the left navigation pane, expand **Users** then select **Active users**.

1. Find the account for **Megan Bowen** and select the key icon to reset her password.

   You'll use Megan's account in the next exercises.

   ![Screenshot showing user accounts that need to be reset.](../Media/reset-password-button-megan.png)

1. In the **Reset Password** flyout page on the right, make sure all options are unchecked, then enter a password you'll remember in the **Password** field.

1. Select **Reset password** at the bottom of the page, then **Close** on the confirmation page.

You have successfully reset Megan's password for the lab exercises.

## Task 5 – Explore the Microsoft Purview portal

In this task, you'll switch to Megan Bowen's account and explore the Microsoft Purview portal.

1. In **Microsoft Edge**, navigate to the Microsoft Purview portal at **`https://purview.microsoft.com`**.

1. When the **Pick an account** window appears, select **Use another account**.

1. Sign in as `MeganB@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Megan's password was set in a previous exercise.

1. Explore the Microsoft Purview portal to familiarize yourself with its interface.

You have successfully switched to Megan Bowen's account and are ready to continue with the lab.
