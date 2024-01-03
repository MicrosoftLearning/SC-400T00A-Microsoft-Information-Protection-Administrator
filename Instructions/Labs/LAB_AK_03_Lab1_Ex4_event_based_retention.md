---
lab:
    title: 'Exercise 4 - Configure Event-based Retention'
    module: 'Module 3 - Implement Data Lifecycle and Records Management'
---

# Lab 3 - Exercise 4 - Configure Event-based Retention

In this exercise you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to retain content belonging to specific projects for 5 years after they close.

## Task 1 – Create event-driven retention label and event type

In this step, you will create a retention label and an event type. The event type will trigger the retention period. Any content that has the retention label applied to it for that specific event type will have the retention actions from the label enforced on it.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, on the left navigation pane, expand **Data lifecycle management** then select **Microsoft 365**.

1. On the  **Data lifecycle management** page select the **Labels** tab, then select the **+ Create a label** button.

1. On the **Name your retention label**, enter the following information:

    - **Name**: Project Asset
    - **Description for users**: Assign this label to project documents to ensure they are retained for the period of 5 years.
    - **Description for admins**: Project Asset for event-based retention.

1. Select the **Next** button.

1. On the **Define label settings** page, enable the **Retain items forever or for a specific period** setting, then select **Next**.

1. On the **Define the retention period** page select to **Retain items for** _5 years_.

1. Under the **Start the retention period based on** dropdown select **+ Create new event type**. This will start the event-based label wizard.

1. On the **Name your event type** flyout on the right, enter:

    - **Name**: Project Closure
    - **Description**: This event will be triggered when a project closes.

1. Select **Next**.

1. Review the **Summary** page then select **Submit**

1. On the **Your event type was created**, select **Done**.

1. Back on the **Define the retention period** under **Start the retention period based on** select the newly created **Product Closure** event type then select **Next**.

1. On the **Choose what happens after the retention period** page, select **Delete items automatically**, then select **Next**.

1. On the **Review and finish** page, select **Create label**.  

1. On the **Your retention label is created** page select **Do Nothing** then select **Done**.

You have successfully created the label and need to publish it.

## Task 2 – Publish event-driven retention label

Following from the previous task you will now publish the Project Asset retention label so that the published label will be available for users to apply to the documents in SharePoint documents.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **`https://compliance.microsoft.com`**.

1. In the **Microsoft Purview** portal, on the left navigation pane, expand **Data lifecycle management** then select **Microsoft 365**.

1. On the **Data lifecycle management** page, select the **Labels** tab.

1. Select the **Project Asset** label, then select the **Publish labels** button.

1. On the **Choose labels to publish** page, select **Next**.

1. On the **Policy Scope** page, select **Next**.

1. On the **Choose the type of retention policy to create** page, select **Static**, then select **Next**.

1. On the **Choose where to publish labels** page select **Let me choose specific locations** to display the location options.

1. Ensure only the following locations are toggled **On**:

    - **SharePoint classic and communication sites**
    - **OneDrive accounts**

    **Exchange mailboxes** and **Microsoft 365 Group mailboxes & sites** should be toggled **Off**.

1. Select the **Next** button.

1. On the **Name your policy** enter the following information:

    - **Name**: Project Asset Retention Label
    - **Description**: Project Assets Retention label, retention period 5 years, SharePoint site locations.

1. Select the **Next** button.

1. Review the **Finish** page, then select **Submit**.

1. On the **Your retention label was published** page select **Done**.

You have successfully published the retention label for project assets to your users.

## Task 3 – Apply label and add an Asset ID

Once the label is published the users need to apply the label and assign the correct Asset ID for the project to the documents they want to label. In this task you will test this functionality.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **`https://compliance.microsoft.com`**.

1. In the top left corner select the nine dots and under **Apps** select **SharePoint**.

1. Search for _Brand_ in the search bar on the top, then select the **Brand** SharePoint page from the search results.

1. On the top navigation pane, select **Documents**.

1. On the **Documents** page, select **Customer Product Survey.xlsx** by selecting the checkbox in left of it. Select the horizontal ellipses, **...**, button then select **Details**.

1. In the right-side menu, under **Properties** select **Apply label**, then select the **Project Asset** label.

    >**Note**: As it can take some time for retention labels to be published you may not have the option available immediately.

1. Set the newly appeared **Asset ID** field to **NewProductLaunch** and close the right-side menu by selecting **X** in the top right corner.

You've successfully assigned a label and an asset ID to a document. When the Project Closure event for Asset ID NewProductLaunch is triggered it will activate the retention period of 5 years.

## Task 4 – Create specific event

Once the event happens you need to trigger it so that the content you labeled will start the mandatory retention period.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the **Microsoft Purview** portal, on the left navigation pane, select **Records management** then select the **Events** tab.

1. Select **+ Create**.

1. On the **Name the event** page, set the following information:

    - **Name**: New Product Launch closed
    - **Description**: Assets with the Project Asset label and AssetID NewProductLaunch will enter their retention period.

1. Select **Next**.

1. On the **Event settings** page, select **Use event type** then select **Choose an event type**.

1. On the **Choose an event type** page, select **Project Closure**, then select **Add**.

1. Select **Next**.

1. On the **Event settings** page, set **Asset IDs for items in SharePoint and OneDrive** to **NewProductLaunch**.

1. Select today's date for **When did this event occur?**, then select **Next**.

1. Review the **Finish** page then select **Submit**.

1. On the **Your even has been created** page select **Done**.

You have successfully triggered an event and started the retention period for all documents with the Project Asset label and an Asset ID of NewProductLaunch.

## Task 5 – Observe results of event trigger

To verify that the retention period you specified started, you need to try to delete the file.

1. You should still be logged into Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **`https://compliance.microsoft.com`**.

1. In the top left corner select the nine dots and under **Apps** select **SharePoint**.

1. Search for _Brand_ in the search bar on the top, then select the **Brand** SharePoint page from the search results.

1. In the top navigation pane, select **Documents**.

1. On the **Documents** page, select **Customer Product Survey.xlsx** by selecting the checkbox to the left of it. Select the horizontal ellipses, **...**.

1. In the context menu select **Delete** and observe the results.

You have successfully confirmed that the retention period on the document has started. If you can still delete the document the synchronization period for the event has not been completed and the triggering of the retention policy is still in progress. As with other Retention Labels, this process can take up to 7 days to complete.
