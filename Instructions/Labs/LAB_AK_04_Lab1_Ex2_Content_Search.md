---
lab:
    title: 'Exercise 2 - Perform a content search'
    module: 'Module 4 - Monitor and investigate data and activities by using Microsoft Purview'
---

# Lab 4 - Exercise 2 - Configure Records Management

In this exercise, you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Your organization is currently working on a top-secret project called Mark 8, and you have been tasked with ensuring that all project-related information is properly secured and protected. Your task is to use the Content search feature in the Microsoft Purview compliance portal to search for any emails, documents, or other files containing specific keywords and phrases related to the Mark 8 project. You will then review the search results to identify any potential security or compliance issues and take appropriate action to ensure that all project-related information is properly secured and protected.

## Task 1: Create a new content search

In this task, you will create a new Content search in the Microsoft Purview compliance portal to search for emails, documents, or other files containing specific keywords and phrases related to the Mark 8 project. 

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. In the left navigation pane, select **Content search**.

1. On the **Content search** page select **+ New Search**.

1. On the **Name and description** page enter **Mark 8 Project Search** in the **Name** field, and enter **This search will identify any Mark 8 project-related emails, documents, or files.** in the **Description** field.

1. Select **Next**.

1. On the **Locations** page select to search for content in **Exchange mailboxes**, **SharePoint Sites**, and **Exchange public folders**, then select **Next**.

1. On the **Define your search conditions** page select **Query builder**.

1. In the **Keywords** field enter **"Mark 8"**.

1. Under the **Keywords** field box, select the **+Add condition** drop down then select **Type**.

1. In the **Type** box select the checkbox for **E-mail messages** and **Documents**.

1. Select **Next**.

1. On the **Review your search and create it** page select **Submit**.

1. On the **New search created** page select **Done**.

## Task 2: Export search results

In this exercise, you will learn how to export content search results.

1. You should still be logged in with Joni's account. If not, in **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. Navigate to **Content search** from the left navigation pane. On the **Content search** page, if the Mark 8 Project Search has a status of **Starting**, refresh the searches until the status shows **Completed**.

1. Select **Mark 8 Project Search** to display the **Mark 8 Project Search** fly out page, then select **Search statistics**. Expand **Search content**, **Condition report**, and **Top locations** to view statistics on the content search.

1. Select the **Actions** button at the bottom of the page and select **Export results**.

1. In the **Export results** page under **Output options** select **All items, excluding one that have unrecognized format, are encrypted, or weren't indexed for other reasons**.

1. Under **Export Exchange content as** select **One PST file for each mailbox**.

1. Scroll down and select the check boxes for **Enable de-duplication for Exchange content** and **Include versions for SharePoint files**.

1. Review the estimation report at the bottom of the screen to get an idea of what types of items, the number of items, and the size of the items to be exported, then select **Export**.

1. A **compliance** pop up will appear letting you know **A job has been created**. Select **OK**.

1. Back on the **Content search** page select the **Export** tab from the top navigation bar. Select the job named **Mark 8 Project Search_Export**

    >**Note**: If the status of the export is marked **Scheduling...** select **Refresh** until the **Export key** is available.

1. On the **Mark 8 Project Search_Export** flyout page under **Export key** select to **Copy to clipboard** to copy the export key.

1. At the top of the **Mark 8 Project Search_Export** page select **Download report** to download the report.

1. If you're prompted to install the **eDiscovery Export Tool**, select **Install**.

1. In the eDiscovery Export Tool, in the **Paste the export key that will be used to connect to the source:** field, paste in the **Export key** that was copied in a previous step.

1. Select **Browse** under **Select the location that will be used to store the downloaded files:**

1. In the **Browse For Folder** window select **Documents** then select **OK**.

1. Back in the **eDiscovery Export Tool** select **Start** to export the files.

1. Once you get a green check mark for **Processing has completed.** your report has been downloaded. Select **Close** to close the window.

1. In the **eDiscovery Export Tool**, select the link for the **Export Location:** to open the locally exported files.

1. Explore the contents of the export:

    **Included in the export:**
    - **Export Summary:** An Excel document that contains a summary of the export, including the number of content sources searched, the estimated and downloaded sizes of the search results, and the estimated and downloaded number of items exported.
    - **Manifest:** A manifest file (in XML format) that contains information about each item included in the search results.
    - **Results:** An Excel document providing details about each indexed item in the search results. For emails, it includes message location, date, subject, sender, and recipients. For SharePoint and OneDrive for Business documents, it includes document URL, site collection URL, modification date, and document name.
    - **Skipped Items:** An Excel document that contains information about items that won't be downloaded, such as a folder or a document set.
    - **Trace.log:** Contains detailed logging information about the export process and can help uncover issues during export.
    - All search results and the export reports are included in a folder that has the same name as the Content search. The email messages that were exported are located in a folder named **Exchange**. Documents are located in a folder named **SharePoint**.

1. Once you're finished reviewing the exported results, close the eDiscovery Export Tool and the file explorer windows then navigate back to Internet Explorer.

## Task 3: Review search results

After the search is complete, review the search results to identify any potential security or compliance issues related to the Mark 8 project.

1. You should still be logged in with Joni's account. If not, in **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. Navigate to **Content search** from the left navigation pane.

1. Select **Mark 8 Project Search** from the **Content search** page, and the **Mark 8 Project Search** flyout page should appear on the right.

1. In the **Mark 8 Project Search** flyout page select **Search statistics** and expand **Search content**, **Condition report**, and **Top locations** to view statistics on the content search.

1. Select the **Actions** button at the bottom of the pane and select **Export report**.

1. In the **Export report** pane under **Output options** select **All items, excluding one that have unrecognized format, are encrypted, or weren't indexed for other reasons**.

1. Select **Generate report**.

1. A **compliance** pop up will appear letting you know **A job has been created**. Select **OK**.

1. Back on the **Content search** page select the **Export** tab from the top navigation bar. You should have a report named **Mark 8 Project Search_ReportsOnly**.

1. Select the **Mark 8 Project Search_ReportsOnly** report, and **Mark 8 Project Search_ReportsOnly** flyout page should appear on the right.

1. On the **Mark 8 Project Search_ReportsOnly** flyout page under **Export key** select to **Copy to clipboard** to copy the export key.

1. At the top of the **Mark 8 Project Search_ReportsOnly** page select **Download report** to download the report.

1. If you're prompted to install the **eDiscovery Export Tool**, select **Install**. If the tool is already installed, select **Open**.

1. In the eDiscovery Export Tool, in the **Paste the export key that will be used to connect to the source:** field, paste in the **Export key** that was copied in a previous step.

1. Select **Browse** under **Select the location that will be used to store the downloaded files:**

1. In the **Browse For Folder** window select **Documents** then select **OK**.

1. Back in the **eDiscovery Export Tool** select **Start** to download the report.

1. Once you get a green check mark for **Processing has completed.** your report has been downloaded. Select **Close** to close the window.

1. In the **eDiscovery Export Tool**, select the link for the **Export Location:** to open the locally downloaded report.

1. Explore the contents of the report:

    **Included in the report:**
    - **Export Summary:** An Excel document that contains a summary of the export, including the number of content sources searched, the estimated and downloaded sizes of the search results, and the estimated and downloaded number of items exported.
    - **Manifest:** A manifest file (in XML format) that contains information about each item included in the search results.
    - **Results:** An Excel document providing details about each indexed item in the search results. For emails, it includes message location, date, subject, sender, and recipients. For SharePoint and OneDrive for Business documents, it includes document URL, site collection URL, modification date, and document name.
    - **Trace.log:** Contains detailed logging information about the export process and can help uncover issues during export.

1. Once you're finished reviewing the exported results, close the eDiscovery Export Tool and the file explorer windows then navigate back to Internet Explorer.
