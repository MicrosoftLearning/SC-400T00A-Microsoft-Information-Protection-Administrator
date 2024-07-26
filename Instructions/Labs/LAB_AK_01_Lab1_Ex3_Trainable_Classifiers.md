---
lab:
    title: 'Exercise 3 - Manage Trainable Classifiers'
    module: 'Module 1 - Implement Information Protection'
---

# Lab 1 - Exercise 3 - Manage Trainable Classifiers

Contoso Ltd. needs to ensure that financial documents and reports stored in the "Sales and Marketing" SharePoint site are properly classified. To achieve this, you need to create a trainable classifier to recognize and label these files.

## Task 1 – Create a trainable classifier

In this task, you'll activate trainable classifiers in the tenant to enable the creation of custom classifiers.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **LON-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`**.

1. From the left, navigation pane, expand **Data classification**, then select **Classifiers**.

1. On the **Classifiers** page, the tab for **Trainable classifiers** should already be selected.

2. Select **+ Create trainable classifier** to create a new classifier.

1. On the **Name and describe your trainable classifier** page, enter:

    - **Name**: `Contoso Company Data`
    - **Description**: `Trainable classifier for company data produced and stored by Contoso Ltd.`

1. Select **Next**.

1. On the **Source of the positive sample content**, select **+ Choose sites**.

1. On the **Add SharePoint sites** fly-out page on the right, select these SharePoint sites:

    - Mark8ProjectTeam

1. Select **Add** at the bottom of the fly-out page.

1. Back on the **Source of the positive sample content** page, select **Next**.

1. On the **Source of the negative sample content** page, select these SharePoint sites:

    - HR

1. Select **Add** at the bottom of the fly-out page.

1. Back on the **Source of the negative sample content** page, select **Next**.

1. On the **Review and create classifier to start processing your sample content**, select **Create trainable classifier**

1. On the **Your classifier is being trained** page, select **Done**.

The documents and files in the chosen SharePoint site are now being analyzed, which can take up to 48 hours.

<!---
## Task 3 – Publish a trainable classifier (optional lab task)

After the new trainable classifier was created and the initial analysis of the documents and files is done, the manual training process needs to be performed. In this task, Joni will start the calibration of the classifier to achieve the required accuracy for publishing.

1. You should still be logged into your Client 1 VM (SC-400-CL1) as the **SC-400-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In your browser window, you are in the Microsoft Purview portal at **Data classification** in the **Trainable classifiers** tab.

1. Select the trainable classifier with the name **Contoso Company Data** of the type **Custom** to open the detailed settings.

1. Review the **Details** tab on the right side, including the source site for the classifier, the number of processed items and the **Status**, which is in **Need test items**.

1. To add items for training the classifier, select **Add items to test** to open the right side selection pane.

1. In the **Choose sites with items to test** pane, select **+ Choose sites**.

1. Select the following SharePoint sites:

    - **Communication site**
    - **News @ Contoso**
    - **Contoso Web 1**
    - **Brand**
    - **Digital Initiative Public Relations**
    - **Work @ Contoso**
    - **Sales and Marketing**
    - **Contoso Landings**
    - **Mark 8 Project Team**
    - **HR**
    - **Operations**
    - **Retail**
    - **PointPublishing Hub Site**
    - **Team Site**
    - **Leadership Team**
    - **Community**
    - **Give @ Contoso**
    - **Benefits @ Contoso**
    - **Learn @ Contoso**
    - **Campaigns - Events**

1. Select **Add**.

1. Wait until the sites are shown in the list and select **Add**.

1. When the **Overview** section is updated, a new tab is shown in the top of the window.

1. Select **Tested items to review** from the top pane.

1. It will take between 15 to 30 minutes until first results are ready for review. Refresh the browser window if no files are shown in the list, until data is available.

1. Select the name of the first file from the list to open the preview window.

1. When the **Prediction** row is equal to **Match**, the file was identified as a match for the classifier. Below the preview window, a message **We predict this item "matched" this classifier.** is shown. Select **Match** to approve the automatic classification.

1. When the **Prediction** row is equal to **Not a match**, the file was identified not as a match for the classifier. Below the preview window, a message **We predict this item "does not match" this classifier.** is shown. Select **Not a match** to approve the automatic classification.

1. Proceed with all items in the list and approve the automatic classification. After all items have been reviewed, select **Overview** from the top pane and **Tested items to review** again, to load the next set of items for review.

1. For each 30 reviewed items an **Auto-retrain performed** window is shown. Select **OK** and proceed with the previous steps, until no items for review are left.

1. After sufficient items are reviewed, the **Publish** button in the upper right gets available. Select it as soon it is available.

1. In the **Publish classifier** window, select **Yes** to publish the classifier.

1. When the right side pane with **Your trainable classifier has been published** is displayed, the trainable classifier was successfully published.

1. Close the right side pane with the **X** in the upper right.

1. Back at the main site, the custom classifier was moved to **Published** and the **Status** has been changed to **Ready to use**.

1. Leave the browser window open.

You have successfully created, trained, and published a custom trainable classifier that matches the files stored on the existing SharePoint sites of Contoso Ltd.
