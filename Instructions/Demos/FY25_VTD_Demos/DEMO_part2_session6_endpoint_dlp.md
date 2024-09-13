---
lab:
    title: 'Exercise 2 - Manage Endpoint DLP'
    module: 'Module 2 - Implement Data Loss Prevention'
---

# Lab 2 - Exercise 2 - Manage Endpoint DLP

You are Joni Sherman, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you need to make sure that sensitive customer information does not leave the organization. For this reason, you decide to not only implement Microsoft 365 DLP policies but extend this protection to devices in your organization.

## Task 1 – Enable device onboarding

1. Log on to Client 1 VM (SC-400-CL1) as the SC-400-cl1\admin account.

1. You should still be at the **Devices** page in the Microsoft Purview portal, logged in as Joni Sherman. Select the **Home** button on the top left of the screen. If you're not logged in, navigate to `https://purview.microsoft.com` and login as Joni Sherman. Joni's password was set in a previous exercise.

1. In the Microsoft Purview portal, select **Solutions** from the left sidebar, then select **Data Loss Prevention**.

1. From the left, navigation pane, select **Policies** then select **+ Create policy**.

1. On the **Start with a template or create a custom policy** page, select **Custom** and **Custom policy**, then select **Next**.

1. On the **Name your DLP policy** page, enter:

    - **Name**: `Generative AI sharing DLP policy`
    - **Description**: `Prevent sharing of sensitive data with generative AI platforms.`

1. On the **Assign admin units** page, select **Next**.

1. On the **Choose locations to apply the policy** page, select only the **Devices** location. If any other location is selected, ensure they're deselected, then select **Next**.

1. On the **Define policy settings** page, select **Create or customize advanced DLP rules** then select **Next**.

1. On the **Customize advanced DLP rules** page, select **+ Create rule**.

1. On the **Create rule** page, enter:

    - **Name**: `Sensitive data protection rule`
    - **Description**: `Detect and restrict sharing of sensitive information with generative AI platforms.`

1. Under **Conditions** select **+ Add condition** then select **Content contains**.

1. In the newly opened **Content contains** area, select **Add** then select **Sensitive info types**.

1. On the **Sensitive info types** flyout panel on the right, search for `U.S.` then select all United States related sensitive info types. Select **Add** at the bottom of the flyout panel.

1. Scroll down to **Actions** and select the **+ Add an action** dropdown then select **Audit or restrict activities on devices**.

1. In the newly opened **Audit or restrict activities on devices** area, in the **Service domain and browser activities** section, select the checkbox for **Upload to a restricted cloud service domain or access from an unallowed browsers**, then select **+ Choose different restrictions for sensitive service domains** under this option.

1. In the **Sensitive service domain restrictions** flyout panel, select **+ Add group**.

1. In the **Choose sensitive service domain groups** select the checkbox for **Generative AI Websites**, then select **Add** at the bottom of the flyout panel.

1. Back on the **Sensitive service domain restrictions** page, ensure **Generative AI Websites** is listed, then select **Save** at the bottom of the flyout panel.

1. Back on the **Create rule**, select the checkbox for **Paste to supported browsers**, then select **+ Choose different restrictions for sensitive service domains** under this option.

1. In the **Sensitive service domain restrictions** flyout panel, select **+ Add group**.

1. In the **Choose sensitive service domain groups** select the checkbox for **Generative AI Websites**, then select **Add** at the bottom of the flyout panel.

1. Back on the **Create rule** in the **Service domain and browser activities** section, update the action for both **Upload to a restricted cloud service domain or access from an unallowed browsers** and **Paste to supported browsers** from **Audit only** to **Block**.

1. In the **File activities for all apps** section, leave the default action of **Audit only**.

1. In the **User notifications** section, set **Use notifications to inform your users and help educate them on the proper use of sensitive info.** to **On**.

1. Under **Endpoint devices** select the checkbox for **Show users a policy tip notification when an activity is restricted. This is turned on when you select Block for an activity in Windows. To turn off the notifications on Windows devices, disable the restrictions**.

1. Under **Microsoft 365 services** select the checkbox for **Notify users in Office 365 service with a policy tip**.

1. Select **Save** at the bottom of the flyout panel.

1. Back on the **Customize advanced DLP rules**, select **Next**.

1. On the **Policy mode** page select **Turn the policy on immediately** then select **Next**.

1. On the **Review and finish** page, review your policy settings then select **Submit** to create the policy.

1. Once the policy is created select **Done** on the **New policy created** page.

You have successfully activated the Endpoint DLP Policy. This policy will prevent the sharing of sensitive information with generative AI platforms, ensuring that sensitive data such as driver's license numbers and personal details are protected from unauthorized access or exposure.

## Task 2 – Configure endpoint DLP settings

In this task, you will configure a file path exclusion to a folder on your Windows 11 devices to make sure that the content of this folder is not monitored by the Endpoint DLP policy you created.

1. You should still be logged into Client 1 VM (SC-400-CL1) as the **SC-400-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open to the **Policies** page for data loss prevention. Select **Settings** from the left sidebar.

1. On the settings page, select **Data Loss Prevention** from the left sidebar.

1. The **Data Loss Prevention settings** page should open to the **Endpoint DLP settings**.

1. On the **Endpoint DLP settings** page, expand **File path exclusions for Windows**  then select **+ Add file path exclusion**.

1. On the **Exclude these file paths from Windows devices** flyout page in the **File path exclusion** field, enter `C:\FilePathExclusionTest` then select the **+** button to the right. Select **Save** to save this entry.

1. Back on the **Endpoint DLP settings** page, expand **Browser and domain restrictions to sensitive data** and select **+ Add or edit unallowed browsers**.

1. On the **Add unallowed browsers** flyout page select the checkbox for **Google Chrome** and select **Save**.

1. Back on the **Endpoint DLP settings** page, select the dropdown to for **Service domains** and change it from **Off** to **Block**.

1. In the **Update cloud app mode** dialogue select **Yes** to activate the block mode.

1. Under **Service domains** select **+ Add cloud service domain**.

1. On the **Add cloud service domain** flyout page in the **Domain** field enter `dropbox.com` then select the **+** to the right. Select **Save** to save this setting.

1. Close the browser window.

You have now configured custom settings for your Endpoint DLP policies. Every policy you create will ignore content in the folder you configured, and the Google Chrome browser has been added as unallowed browser to handle sensitive data.