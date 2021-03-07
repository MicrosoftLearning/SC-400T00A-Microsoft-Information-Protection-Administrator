# Exercise 4 - Manage Trainable Classifiers

The Contoso Ltd. tenant contains a SharePoint site collection with the name "Sales and Marketing" that will be used in the future to store several financial related documents and reports. Because of the nature of these documents, you need to create a trainable classifier to recognize and label these files. For this purpose, you will activate custom trainable classifiers and create a new one.

**Important!**: After activating trainable classifiers in a tenant, it takes between **7 and 14 days** before any custom trainable classifiers can be created. The button to create a new trainable classifier will not be available until the whole activation process is finished.  Therefore, **you will only be able to perform task 1 now** and will need to wait until the trainable classifiers are available later within your tenant.  These lab instructions are available online and your tenant should still be active.

### Task 1 – Activate trainable classifiers

Before you can create custom trainable classifiers, you need to activate the feature in a tenant. To activate the Global Admin permissions are required, you will sign out of Joni Sherman's account and use the MOD Administrator to activate the feature first.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. Sign out of Joni Sherman's account by selecting the image in the upper right corner and select **Sign out**.

3. Close the browser window and open a new browser window.

4. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com**.

5. When the **Pick an account** page is displayed, select **Use another account** and sign in as **MOD Administrator**  admin@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Admin's password should be provided by your lab hosting provider.

6. Navigate to **Data Classification** from the left side navigation pane.

7. Select **Trainable classifiers** from the top pane.

8. When you see the **Get started with trainable classifiers** window, select **Start scanning process**.

9. Refresh the browser window.

10. Read the banner at the top part of the window with the message **To set you up for creating trainable classifiers, we're currently scanning your content locations to generate analytics that will help us learn what type of content is in your organization. This process will take 7 to 14 days to complete**

11. Leave the client open.

You have successfully activated trainable classifiers in your tenant. You will now need to wait between 7 and 14 days until the **Create trainable classifiers** button becomes available.  If you are in a classroom setting and do not have 7 to 14 days to wait for Trainable Classifiers to complete processing, you may perform the remainder of the tasks in this exercise by logging into the tenant you were provided later when the Trainable Classifiers processing is complete.  Your tenant should still be active.

### Task 2 – Create a trainable classifier

After trainable classifiers have been activated successfully, the **Create trainable classifiers** button becomes available and it is possible to create a new custom classifier. In this task, Joni will create a new trainable classifier and select different SharePoint sites for identifying typical data created and stored by Contoso Ltd.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **MOD Administrator**. 

2. Sign out of the MOD Administrator account by selecting the MA in the upper right corner and select **Sign out**.

3. Close the browser window and open a new browser window.

4. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com**.

5. When the **Pick an account** page is displayed, select **Use another account** and sign in as **Joni Sherman**. JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

6. Navigate to **Data Classification** from the left side navigation pane.

7. Select **Trainable classifiers** from the top pane.

8. Select **+ Create trainable classifier** to create a new classifier.

9. Enter the following information on the **Name and describe your trainable classifier** page:

    - **Name**: Contoso Company Data
    - **Description**: Trainable classifier for company data produced and stored by Contoso Ltd.

10. Select **Next**.

11. Select **Choose sites** to open the right side pane.

12. Select the following SharePoint sites:

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

13. Wait until the chosen site is shown in the list and select **Next**.

14. Review the settings and select **Create trainable classifier**.

15. When the message **Your trainable classifier was created** is shown, select **Done**.

16. Now you have to wait between 1 hour up to 24 hours to proceed forward. Leave the browser open.

The documents and files in the chosen SharePoint site are now being analyzed, which can take up to 24 hours.

### Task 3 – Publish a trainable classifier 
After the new trainable classifier was created and the initial analysis of the documents and files is done, the manual training process needs to be performed. In this task, Joni will start the calibration of the classifier to achieve the required accuracy for publishing.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In your browser window, you are in the Microsoft 365 compliance center at **Data classification** in the **Trainable classifiers** tab.

3.  Select the trainable classifier with the name **Contoso Company Data** of the type **Custom** to open the detailed settings.

4. Review the **Details** tab on the right side, including the source site for the classifier, the number of processed items and the **Status**, which is in **Need test items**.

5. To add items for training the classifier, select **Add items to test** to open the right side selection pane.

6. In the **Choose sites with items to test** pane, select **+ Choose sites**.

7. Select the following SharePoint sites:

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

8. Select **Add**.

8. Wait until the sites are shown in the list and select **Add**.

9. When the **Overview** section is updated, a new tab is shown in the top of the window.

10. Select **Tested items to review** from the top pane.

11. It will take between 15 to 30 minutes until first results are ready for review. Refresh the browser window if no files are shown in the list, until data is available.

12. Select the name of the first file from the list to open the preview window.

13. When the **Prediction** row is equal to **Match**, the file was identified as a match for the classifier. Below the preview window, a message **We predict this item "matched" this classifier.** is shown. Select **Match** to approve the automatic classification.

14. When the **Prediction** row is equal to **Not a match**, the file was identified not as a match for the classifier. Below the preview window, a message **We predict this item "does not match" this classifier.** is shown. Select **Not a match** to approve the automatic classification.

15. Proceed with all items in the list and approve the automatic classification. After all items have been reviewed, select **Overview** from the top pane and **Tested items to review** again, to load the next set of items for review.

16. For each 30 reviewed items an **Auto-retrain performed** window is shown. Select **OK** and proceed with the previous steps, until no items for review are left.

17. After sufficient items are reviewed, the **Publish** button in the upper right gets available. Select it as soon it is available.

18. In the **Publish classifier** window, select **Yes** to publish the classifier.

19. When the right side pane with **Your trainable classifier has been published** is displayed, the trainable classifier was successfully published.

20. Close the right side pane with the **X** in the upper right.

21. Back at the main site, the custom classifier was moved to **Published** and the **Status** has been changed to **Ready to use**.

22. Leave the browser window open.

You have successfully created, trained, and published a custom trainable classifier that matches the files stored on the existing SharePoint sites of Contoso Ltd.

# Proceed to Exercise 5 