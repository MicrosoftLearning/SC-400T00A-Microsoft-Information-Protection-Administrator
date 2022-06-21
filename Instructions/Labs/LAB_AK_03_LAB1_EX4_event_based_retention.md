# Lab 3 - Exercise 4 - Configure event-based retention

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

1. On the Information governance page, select **Labels** tab.

1. Select the **+ Create a label** button.

1. On the **Name your retention label page** for the **Name**, **Description for users**, and **Description for admins**, enter the following information:

	- **Name**: Project Asset
	- **Description for users**: Assign this label to project documents to ensure they are retained for the period of 5 years.
	- **Description for admins**: Project Asset for event-based retention.

1. Select the **Next** button.

1. On the **Define retention settings** page, enable the **Retain items for a specific period** setting.

1. For the **Define retention settings** section set the following information:
	- **Retention period**: 5 years.
	- **Start the retention period based on**: Project Closure

1. Select the **Next** button.

1. On the **Choose what happens after the retention period** page, select **Delete items automatically**, then select **Next**.

1. On the **Review and finish** page, select the **Create label** button.  On the *Your retention label is created* page select **Do Nothing** option and select **Done**.

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

1. On the **Review your Settings** page, select the **Submit** button.  When your policy is created select **Done**.

You have successfully published the retention label for project assets to your users.

### Task 4 – Apply label and add AssetID

### Task 5 – Create specific event

### Task 6 – Observe results of event trigger


# Proceed to Lab 3 - Exercise 5
