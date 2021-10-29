# Lab 3 Exercise 5 - Configure Records Management

In this exercise, you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Regulatory requirements for your organization include having a definitive copy of the employee provided health insurance information available when your company discusses the insurance costs. You are tasked with making sure the records are kept.

### Task 1 – Create File Plan Labels

In this task, you will create a file plan label that allows your HR department to label content containing health insurance information that your employees are required to be provided when they are hired.

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Microsoft 365 compliance portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com/**. 

3. In the **Microsoft 365 compliance** portal, in the left navigation pane, select **Records management**.

4. On the **Records management** page, select **File plan**.

5. Select **+** to create a label.

6. Enter the following information, then select **next**:
    - **Name**: Employee Data
    - **Description for users**: Content marked with this label contains sensitive employee data.
    - **Description for admins**: The label was created on request of the HR department and will be automatically applied to Employee Data.

7. Enter the following information on the **File plan descriptors** for this label, then select **Next**:

    - **Reference ID**: HR_EmployeeData
    - **Business function/department**: Human resources
    - **Category**: Recruiting and hiring
    - **Provision/citation**: Health Insurance Portability and Accountability Act of 1996

8. On the **Retention settings** page, select the following options, then select **Next**:
    - **Retain items for a specific period**
    - **Retention period**: 7 years
    - **Start the retention period based on**: When items were created
    - **During the retention period**: Mark items as a record
    - **At the end of a retention period**: Trigger a disposition review

9. In the **Add disposition reviewers** window, add a disposition stage and assign **Lynne Robbins** to it, then select **Next**

10. Review the configuration of the label, then select **Create label**.

11. On the **Your retention label is created** page, select **Do Nothing**, then select **Done**.

You successfully created a retention label using file plan that keeps all labeled documents from being deleted for seven years and at the end of the retention period Lynne Robbins has to decide if the data can be disposed of or has to be retained further.

### Task 2 – Publish Labels

In this task, you will publish the label so users of the HR department can apply it to content containing health insurance information.  

1. You should still be logged into your Client 1 VM (LON-CL1) as the **lon-cl1\admin** account, and you should be logged into Microsoft 365 as **Joni Sherman**. 

2. In **Microsoft Edge**, the Microsoft 365 compliance penter tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to **https://compliance.microsoft.com/**. 

3. In the **Microsoft 365 compliance** portal, in the left navigation pane, select **Records management**.

4. On the **Records management** page, select **File plan**.

5. Select **Publish labels** icon/button.

6. On the **Choose labels to publish** page, select **Choose labels to publish**.

7. Select the **Employee Data** label and select **Add**, then select **Next**.  Select **Next**.

8. On the **Choose locations** page, select **All locations. Includes content in Exchange email, Office 365 groups, OneDrive, and SharePoint documents.**, then select **Next**.

9. On the **Name your policy** page, enter the following information, then select **Next**:
    - **Name**: Employee Health Insurance label policy
    - **Description**: This policy contains the record label for health insurance information.

10. Review the configuration of your policy and select **Submit**.  When your label is published, select **Done**.

You successfully started the process of publishing a retention label including a record. The publishing of labels may take up to 24 hours. After the label is published the HR department can use it to label files containing the health insurance information, they are required to keep a record of.  You can proceed immediately to the next task.

### Task 3 – Work with Records

In this task, you will assign the published record label to an email in Outlook and observe the results of applying the record. You might need to wait for the 24-hour publishing delay.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. On the taskbar at the bottom of the page, select the Start button, scroll down and then select **Outlook**. If necessary, sign in as **Megan Bowen**.
 
3. In the Outlook application, select **Inbox**

4. With the right mouse button select the first email item in the center pane, and in the menu, select **Assign Policy**.

5. A list of retention policies will be displayed.

6. Select the **Employee Data** label to apply the record label.  

7. With the right mouse button, select the email item you labeled with **Employee Data**, and select **Delete**.

8. Review the message you receive.

You have successfully applied a retention label with a record to an email and observed that it now cannot be deleted. 

## You have completed the lab.
