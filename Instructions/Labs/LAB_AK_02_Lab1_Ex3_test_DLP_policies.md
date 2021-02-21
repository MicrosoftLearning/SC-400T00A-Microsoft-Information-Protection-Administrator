# Exercise 3 - Test DLP Policies

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you have configured DLP policies to make sure that sensitive customer information does not leave the organization. You decide to test your policies for correct functionality.

### Task 1 – Test a DLP policy

In this exercise, you will test the DLP policy that scans for credit card information to make sure that your users are informed about the block action and allowed to override it.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://outlook.office.com** and log into Outlook as **Joni Sherman**.

3. In the top-left corner, select **New message** and select **Megan Bowen** as the recipient in the **To** field.

4. In the **Subject** field, type **Credit card information** and in the **Body** type **Credit Card: MASTERCARD 5239681227023651**.

5. Above the **To** field you should now see a mail tip that reads **Policy tip: Your email message conflicts with a policy in your organization.**

6. Select **Send** and review the resulting message. It should allow you to override the block action.

You have successfully sent an e-mail including credit card information by providing a business justification.

### Task 2 - Test policy priority

In this exercise, you will test policy priority by sending an e-mail containing credit card information and driver's license numbers to make sure that the driver's license number DLP policy is applied and the block action without override is enforced.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Office 365 Compliance Center tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://outlook.office.com**.

3. In the top-left corner, select **New message** and select **Megan Bowen** as the recipient in the **To** field.

4. In the **Subject** field, type **The requested user information** and in the **Body** type **Credit Card: MASTERCARD 5239681227023651** and **Drivers License: 2515644**.

5. Above the **To** field you should now see a mail tip that reads **Policy tip: Your email message conflicts with a policy in your organization.**

6. Select **Send** and review the resulting message. It should not allow you to override the block action.

You have verified that the more restrictive policy action is enforced if multiple types of sensitive information are present.

### Task 3 - Test Endpoint DLP Policy

In this exercise, you will test the Endpoint DLP policy by trying to copy content out of a protected file on your Client.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In the start menu, select **Word** and sign in as **Joni Sherman**.
 
3. Create a **Blank document**.

4. In the blank document, type **Credit Card: MASTERCARD 5239681227023651** and select **File** in the top-left corner.

5. In the left navigation pane, select **Save As** and then select **Browse**.

6. In the **Save As** dialog, navigate to the Desktop.

7. Change the **File name** to **CC_info.docx** and select **Save**.

8. Copy the **Credit Card: MASTERCARD 5239681227023651** text in your word document into the clipboard.

9. In the start menu, select **Excel** and create a **Blank workbook.**

10. Try to paste the information into the table.

11. Review the **Data loss prevention** toast notification and close **Word**.

You have successfully verified that you are stopped from copying content out of a protected file on your Windows 10 Client.

### Task 4 - Test Endpoint DLP Settings

In this exercise, you will test if the configured file path exclusions are affecting your Endpoint DLP policy correctly.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. Open the **Windows Explorer** and navigate to **C:\**.

3. Create a **New folder** and name it **FilePathExclusionTest**. The path should read **C:\FilePathExclusionTest**.

2. In the start menu, select **Word** and create a **Blank document**.

3. In the blank document, type **Credit Card: MASTERCARD 5239681227023651** and select **File** in the top-left corner.

4. In the left navigation pane, select **Save As** and then select **Browse**.

5. In the **Save As** dialog, navigate to **C:\FilePathExclusionTest**.

6. Change the **File name** to **CC_info_ExcludedfromPolicy.docx** and select **Save**.

7. Copy the **Credit Card: MASTERCARD 5239681227023651** text in your word document into the clipboard.

8. The blank workbook should still be open, if you closed it open a new workbook.

9. Try to paste the information into the table.

You have successfully moved a file into an excluded folder and observed that the DLP policy does not affect the file anymore.

### Task 5 - Test PowerPlatform DLP Settings

In this exercise, you will create a PowerAutomate flow and test if you can use a connector of the non-business group in the same flow as a SharePoint online connector.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, navigate to **https://flow.microsoft.com** and log into the Power Automate portal as **Joni Sherman**.

3. In the Power Automate portal, in the left navigation pane select **+ Create** and in the **Start from blank** section, select **Automated cloud flow**.

4. In the **File name** field, type **Copy from SharePoint to OneDrive**.

5. In the **Choose your flow's trigger** select **When a file is created in a folder** from the **SharePoint** options, then select **Create**.

6. In the **Site Address** dropdown menu, select **Benefits @ Contoso** and in the **Folder ID** menu, select **/Shared Documents**.

7. Select **+ New step** and, under **All**, select the **OneDrive for Business** connector.

8. Under **Actions**, select **Create File**.

9. In the **Folder path** dropdown menu, select **Root**.

10. In the **File name** dropdown menu, select **x-ms-file-name-encoded** and in the **File content** dropdown menu, select **File Content**.

11. Select **Save**. You should see two Errors warning you about DLP violations in the **SharePoint Trigger** and the **OneDrive for Business Action**.

You have now verified that you cannot create a PowerAutomate flow that contains connectors of different groups.

# Proceed to Exercise 4