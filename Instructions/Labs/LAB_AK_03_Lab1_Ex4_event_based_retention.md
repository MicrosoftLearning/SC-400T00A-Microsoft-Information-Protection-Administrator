---
lab:
    title: 'Exercise 4 - Configure Event-based Retention'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 4 - Configure Event-based Retention

In this exercise you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to retain content belonging to specific projects for 5 years after they close.

### Task 1 - Create event type

First you need to create an event type that can be triggered when a specific condition occurs. In this case you will create an event type that can be triggered on Project Closure.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider. 

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Records Management** and navigate to the **Events** tab.

1. Select **Manage event types** and select **+ Create**.

1. On the **Name your event type** dialog, set the following information:
    - **Name**: Project Closure
    - **Description**: This event will be triggered when a project closes.

1. Review the **Summary** and select **Submit**, then select **Done**.

You have successfully created a new event type.

### Task 2 – Create event-driven retention label

Once you created an event type you need to create a label that triggers its retention period when the event occurs.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider. 

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** page, select the **Labels** tab.

1. Select the **+ Create a label** button.

1. On the **Name your retention label page** for the **Name**, **Description for users**, and **Description for admins**, enter the following information:

	- **Name**: Project Asset
	- **Description for users**: Assign this label to project documents to ensure they are retained for the period of 5 years.
	- **Description for admins**: Project Asset for event-based retention.

1. Select the **Next** button.

1. On the **Define label settings** page, enable the **Retain items forever or for a specific period** setting.

1. On the **Define the period** page set the following information:
	- **How long is the period**: 5 years.
	- **When should the period begin?**: Project Closure

1. Select the **Next** button.

1. On the **Choose what happens after the retention period** page, select **Delete items automatically**, then select **Next**.

1. On the **Review and finish** page, select the **Create label** button.  On the **Your retention label is created** page select **Do Nothing** option and select **Done**.

You have successfully created the label and need to publish it.

### Task 3 – Publish event-driven retention label

Following from Task 2 you will now publish the Project Asset retention label so that the published label will be available for users to apply to the documents in Sharepoint documents.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Policies** and under **Data** select **Retention**.

1. On the **Data lifecycle management** Page, select the tab **Labels**.

1. Select the label **Project Asset**, that you created in Task 1.

1. Select the **Publish labels** icon button.

1. On the **Choose labels to publish** page, select the **Next** button.

1. On the **Choose the type of retention policy to create** page, select the **Static** item.

1. Select the **Next** button.

1. On the **Choose locations** page enable the option **Let me choose specific locations**.

1. Enter the following information:
	- **Exchange email** location - **Status**: Off
	- **SharePoint sites** location - **Status**: On
	- **OneDrive accounts** location - **Status**: On
	- **Microsoft 365 groups** location - **Status**: Off  

1. Select the **Next** button.

1. On the **Name your policy** page for **Name** and **Description** enter the following information:

	- **Name**: Project Asset Retention Label
	- **Description**: Project Assets Retention label, retention period 5 years, SharePoint site locations.

1. Select the **Next** button.

1. On the **Finish** page, select the **Submit** button.  When your policy is created select **Done**.

You have successfully published the retention label for project assets to your users.

### Task 4 – Apply label and add AssetID

Once the label is published the users need to apply the label and assign the correct Asset ID for the project to the documents they want to label. In this task you will test this functionality.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the top left corner select the nine dots and under **Apps** select **SharePoint**.

1. On the left side navigation pane, select **My sites** and under **Frequent Sites** on the right select **Brand**.

1. On the top navigation pane, select **Documents**.

1. On the **Documents** page, select **Customer Product Survey.xlsx** by selecting the checkbox in front of it and then select the three vertical dots.

1. In the context menu select **Details**.

1. In the right-side menu, under **Properties** select **Apply label** and then select the **Project Asset** label.

	Note: As it can take some time for retention labels to be published you may not have the option available immediately.

1. Set the newly appeared **Asset ID** field to **NewProductLaunch** and close the right-side menu by selecting **X** in the top right corner.

You've successfully assigned a label and an asset ID to a document. When the Project Closure event for Asset ID NewProductLaunch is triggered it will activate the retention period of 5 years.

### Task 5 – Create specific event

Once the event happened you need to trigger it so that the content you labeled will start the mandatory retention period.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider. 

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Records Management** and navigate to the **Events** tab.

1. Select **+ Create**.

1. On the **Name the event** page, set the following information:
	- **Name**: New Product Launch closed
	- **Description**: Assets with the Project Asset label and AssetID NewProductLaunch will enter their retention period.

1. Select **Next**.

1. On the **Event settings** page, select **Use event type** and then **Choose an event type**.

1. On the **Choose an event type** page, select **Project Closure** and then **Add**.

1. Select **Next**.

1. On the **Event settings** page, set **Asset IDs for items in SharePoint and OneDrive** to **NewProductLaunch** and select todays date.

1. Select **Next**, select **Submit** and then select **Done**.

You have successfully triggered an event and started the retention period for all documents with the Project Asset label and an Asset ID of NewProductLaunch.

### Task 6 – Observe results of event trigger

To verify that the retention period you specified started, you need to try to delete the file.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com**.

1. In the top left corner select the nine dots and under **Apps** select **SharePoint**.

1. On the left side navigation pane, select **My sites** and under **Followed** select **Operations**.

1. In the left-side navigation pane, select **Documents**.

1. On the **Documents** page, select **Customer Product Survey.xlsx** by selecting the checkbox in front of it and then select the three vertical dots.

1. In the context menu select **Delete** and observe the results.

You have successfully confirmed that the retention period on the document started. If you can still delete the document the synchronization period for the event has not been completed and the triggering of the retention policy is still in progress. As with other Retention Labels this process can take up to 7 days to complete.
