---
lab:
    title: 'Session 6 - DLP Strategies for AI Security'
    module: 'Learning Objective - Create a DLP policy for generative AI sites'
---

# Part 2 Demo 6 - Create an endpoint DLP policy for generative AI sites

With the growing use of generative AI tools at Contoso Ltd., the company's IT team has identified a risk of employees accidentally sharing sensitive customer and employee data through AI platforms. To mitigate this risk, Contoso's IT team is implementing Endpoint DLP in Microsoft Purview. This DLP policy will prevent sensitive information, such as customer details, employee records, or other confidential data, from being uploaded to generative AI websites, while still allowing employees to benefit from AI tools for their work.

## Task 1 – Create an endpoint DLP policy

In this task, we'll create a Data Loss Prevention (DLP) policy that protects against sensitive customer and employee data being uploaded to generative AI platforms. By implementing this policy, Contoso Ltd. ensures that confidential information remains secure while still allowing employees to leverage AI tools productively.

1. Log on to Client 1 VM (SC-400-CL1) as the SC-400-cl1\admin account.

1. Navigate to `https://purview.microsoft.com` and login as MOD Administrator. MOD Admin's password is provided by your lab hosting provider.

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

You have successfully created and activated an Endpoint DLP policy. This policy ensures that sensitive data at Contoso Ltd. is protected from unauthorized uploads to generative AI platforms, balancing security with the need for employees to use AI tools in their daily work.
