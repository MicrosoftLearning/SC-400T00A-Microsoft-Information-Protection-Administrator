---
lab:
    title: 'Exercise 3 - Manage Trainable Classifiers'
    module: 'Module 1 - Implement Information Protection'
---

# Lab 1 - Exercise 3 - Manage Trainable Classifiers

Contoso Ltd. is engaged in research and development (R&D) for its Mark8 Project, which focuses on advanced drone technology. The company needs to ensure that sensitive information related to this project is properly classified to protect against unauthorized access or sharing. In this lab, you'll create a trainable classifier designed to identify and label documents associated with the Mark8 Project. Due to the current dataset's limitations, Contoso might not have sufficient examples of relevant documents to fully train the classifier. This exercise will highlight the importance of having diverse and comprehensive data samples to improve classifier accuracy.

>[!alert] Due to the limited data available in this training tenant, the trainable classifier creation process in this lab won't achieve successful classification results. This exercise is designed to provide an interactive experience in configuring trainable classifiers, allowing you to explore the setup and review processes. While the classifier won't fully train and classify the data as expected, the exercise offers insights into the workflow and considerations needed for effective classifier training. 

## Task 1 – Create a trainable classifier

In this task, you will set up a trainable classifier to identify and protect sensitive documents related to the Mark8 Project within Contoso Ltd.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **LON-CL1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**.

1. In **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`**.

1. From the left, navigation pane, expand **Data classification**, then select **Classifiers**.

1. On the **Classifiers** page, the tab for **Trainable classifiers** should already be selected.

2. Select **+ Create trainable classifier** to create a new classifier.

1. On the **Name and describe your trainable classifier** page, enter:

    - **Name**: `Mark8 Project Documents`
    - **Description**: `Classifier for identifying sensitive documents related to the Mark8 drone project's research and development efforts.`

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

## Task 2 - Review classifier results

Joni noticed that, despite configuring the trainable classifier, it didn't produce the expected results. In this task, you'll review the results of the trainable classifier to understand why it might not have successfully classified the intended content, focusing on potential issues such as insufficient or misaligned training samples.

1. You should still be logged into Microsoft Purview on the **Classifiers** page of the portal. You should be logged into Microsoft 365 as **Joni Sherman**.

1. Select the down arrow next to **Published** to collapse the published trainable classifiers, making the classifiers that are in training easier to identify.

1. The **Mark8 Project Documents** will show a status of **In progress** until the training is complete.

1. Once training is complete, the classifier updates to **Training unsuccessful**.

1. To understand why this classifier was unsuccessful, select the icon for the window with the arrow to **Open in a new window**.

1. In the **Mark8 Project Documents** classifier window, review the **Overview** and **Review test results** tabs to understand why this classifier failed.

1. In reviewing the test results, it appears there's a number of **False positives** and **False negatives** in the sample data.

1. To remove this classifier, select the **Delete** button in the top right of the **Mark8 Project Documents** page.

You have now completed the review of the trainable classifier results. This process highlighted the importance of sufficient and correctly aligned training samples to achieve successful classification. By understanding the causes of the classifier's failure, you can better prepare for future configurations, ensuring more accurate and reliable data classification.
