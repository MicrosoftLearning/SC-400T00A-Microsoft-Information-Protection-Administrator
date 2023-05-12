---
lab:
    title: 'Exercise 1 - Configure Communication Compliance'
    module: 'Module 5 - Manage insider and privacy risk in Microsoft 365'
---
## WWL Tenants - Terms of use
If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training.

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension.

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time.

# Lab 5 - Exercise 1

As the Compliance Administrator for your organization, you are responsible for configuring Microsoft Communication Compliance to help ensure that your organization meets its compliance requirements. Microsoft Communication Compliance allows you to monitor communication activities in various channels, such as email, Microsoft Teams, and other chat and collaboration tools, to help detect and mitigate policy violations and other inappropriate behaviors.

## Task 1: Assign Compliance Administrator Role

In this exercise, you will assign the Compliance Administrator role to a user to grant them access to perform compliance-related tasks in the Microsoft Purview portal. Follow the steps to assign Joni Sherman to the role and ensure she has the necessary permissions to perform the tasks described in this lab.

1. In Microsoft Edge, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as MOD Administrator, `admin@WWLxZZZZZZ.onmicrosoft.com` (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Admin’s password should be provided by your lab hosting provider.

1. Navigate to **Roles & scope**, then select **Permissions** from the dropdown 

1. On the **Permissions** page select Roles

1. On the **Role groups for Microsoft Purview solutions** page select **Compliance Administrator**

1. Select **Edit** from the **Compliance Administrator** pane

1. On the **Edit members of the role group** page select **+ Choose users**

1. In the **Choose users** pane select the check box next to Joni Sherman then select **Select**

1. On the **Edit members of the role group** page select **Next**

1. On the **Review the role group and finish** page select **Save**

1. On the **You successfully updated the role group** page select **Done**

1. Sign out of the **MOD Administrator** account

## Task 2 – Configure a Custom Policy

In this exercise, you will configure a custom policy in Microsoft Communication Compliance to monitor communications for sensitive financial information. Follow the steps to configure the policy:

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. Click on **Communication Compliance** from the left navigation

1. Click on **Policies**

1. Click on **+ Create policy** then select **Custom policy** from the drop down

1. On the **Name and describe your policy** page, in the **Name** field enter **Detect Financial Secrets**

1. In the **Description** field enter **Detection of sharing financial secrets**

1. Select **Next**

1. On the **Choose users and reviews** page, under **Choose users and groups**, leave **All users** selected.

1. In the **Reviewers** field select **Joni Sherman** and **MOD Administrator**

1. Select **Next**

1. On the **Choose locations to detect communications** page select **Exchange**

1. Select **Next**

1. On the **Choose conditions and review percentage** page under **Communication direct** leave the default selected.

1. Under **Condition** select **+ Add condition**

1. Select **Message contains any of these words**

1. In the field under **Message contains any of these words** enter *secret,secrets*

    >**Note:** To apply the policy based on specific words or phrases in a message, enter them separated by commas. No spaces between comma-separated items. Use quotation marks for phrases of two or more words. Each word or phrase is applied independently (only one word is needed to trigger the policy).

1. Under **Review percentage** adjust the slider to **100%**

1. Select **Next**

1. On the **Review and finish** page select **Create policy**

1. The **Your policy was created** page will be displayed. If the **Name and describe your policy** window appears to create a new communication compliance policy appears, select **Cancel** in the bottom right to close this prompt.

1. Your communication compliance policy has been created.

    >**Note:** Make sure you give your policies time to activate before testing the policy. Email messages can take approximately 24 hours to fully process in a policy. Communications in Microsoft Teams, Yammer, and third-party platforms can take approximately 48 hours to fully process in a policy.

## Task 3 – Test your custom policy

In this task, you will verify the effectiveness of your configured custom policy. Through a series of tests using different scenarios, you will assess the policy's ability to identify and flag sensitive financial information. These tests provide valuable real-world insights into the policy's behavior.

>**Note:** Make sure you give your policies time to activate before testing the policy. Email messages can take approximately 24 hours to fully process in a policy. Communications in Microsoft Teams, Yammer, and third-party platforms can take approximately 48 hours to fully process in a policy.

1. Log out of Joni's account and close all browser windows.

1. In **Microsoft Edge**, navigate to **https://outlook.office.com** and log into Outlook on the web as LynneR@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Lynne Robin's password should be provided by your lab hosting provider. Hint: usually it's the same as the MOD admin's password in your lab tenant.

1. Select **New mail** from the upper left side part of Outlook on the web.

1. In the **To** line enter your personal or other third-party email address that is not in the tenant domain. Enter **New Secret Message** to the subject line and **My super-secret message.** to the body.

1. Select **Send** to send the message.

1. Once that message is sent, select **New mail** again from the upper left side part of Outlook on the web.

1. In the **To** line enter **Megan Bowen** and select the suggested email address. Enter **Big secret!** in the subject line, and **We have a surprise baby shower coming for Debra! Keep it secret!** in the body of the email.

1. Select **Send**

1. In the **To** line enter **Joni Sherman** and select the suggested email address. Enter **Surprise party!** in the subject line, and **Joni! We're planning a couple of big secrets around the office! Don't forget Debra's baby shower and Megan's surprise birthday parties this month!** in the body of the email.

1. Select **Send**

1. Lynne wants to send one last email. In the **To** line enter **Debra Berger** and select the suggested email address. Enter **Debra! I just heard a HUGE financial secret about Northwind's acquisition! Let's get together at lunch to discuss.** in the body of the email.

1. Select **Send**

1. Logout of Lynne's account, and close all browser windows.

## Task 4 - Manage communication compliance policy

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider). Joni's password should be provided by your lab hosting provider.

1. Navigate to **Communication Copmliance** from the left navigation bar.

1. Select **Policies**

1. Review the **Items pending review** for the Detect Financial Secrets policy

    >**Note:** Please note that if the **Items pending review** count is 0, it might require additional time for your tests to be completely processed by the policy. Keep in mind that email messages can take approximately 24 hours to fully process within a policy.

1. 
