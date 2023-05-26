---
lab:
    title: 'Exercise 2 - Perform a content search'
    module: 'Module 4 - Monitor and investigate data and activities by using Microsoft Purview'
---

# Lab 4 - Exercise 2 - Configure Records Management

In this exercise, you will assume the role of Joni Sherman, a Compliance Administrator for Contoso Ltd. Your organization is currently working on a top-secret project called Mark 8, and you have been tasked with ensuring that all project-related information is properly secured and protected. Your task is to use the Content search feature in the Microsoft Purview compliance portal to search for any emails, documents, or other files containing specific keywords and phrases related to the Mark 8 project. You will then review the search results to identify any potential security or compliance issues and take appropriate action to ensure that all project-related information is properly secured and protected.

## Task 1: Create a new content search

In this exercise, you will create a new Content search in the Microsoft Purview compliance portal to search for emails, documents, or other files containing specific keywords and phrases related to the Mark 8 project. 

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

## Task 2: Review search results

After the search is complete, review the search results to identify any potential security or compliance issues related to the Mark 8 project.

1. Back on the **Content search** page, review the search that was just created. The Mark 8 Project Search may have a status of **Starting**. Refresh the searches until the status shows **Completed**.

1. Select **Mark 8 Project Search** from the **Content search** page, and the **Mark 8 Project Search** pane should appear on the right.

1. In the **Mark 8 Project Search** pane select **Search statistics** and expand **Search content**, **Condition report**, and **Top locations** to view statistics on the content search.

1. Select the **Actions** button at the bottom of the pane and select **Export report**.

1. In the **Export report** pane under **Output options** select **All items, excluding one that have unrecognized format, are encrypted, or weren't indexed for other reasons**.

1. Select **Generate report**.

1. A **compliance** pop up will appear letting you know **A job has been created**. Select **OK**.

1. Back on the **Content search** page select the **Export** tab from the top navigation bar. You should have a report named **Mark 8 Project Search_ReportsOnly**.

1. Select the **Mark 8 Project Search_ReportsOnly** report, and **Mark 8 Project Search_ReportsOnly** flyout page should appear on the right.

1. On the **Mark 8 Project Search_ReportsOnly** flyout page under **Export key** select to **Copy to clipboard** to copy the export key.

1. At the top of the **Mark 8 Project Search_ReportsOnly** page select **Download report** to download the report.

1. If you're prompted to install the **eDiscovery Export Tool**, select **Install**.

1. In the eDiscovery Export Tool, in the **Paste the export key that will be used to connect to the source:** field, paste in the **Export key** that was copied in a previous step.

1. Select **Browse** under **Select the location that will be used to store the downloaded files:**

1. In the **Browse For Folder** window select **Documents** then select **OK**.

1. Back in the **eDiscovery Export Tool** select **Start** to download the report.

1. Once you get a green check mark for **Processing has completed.** your report has been downloaded. Select **Close** to close the window.

1. In file explorer, navigate to your **Documents** folder. Within your documents, you will have a new folder named **Mark 8 Project Search_ReportsOnly**.

1. Explore the contents of the report:

    **Included in the report:**
    - **Export summary:** Excel document summarizing the export, including the number of content sources searched, search results from each location, estimated and actual numbers and sizes of exported items. It also includes the number of unindexed items if included in the export.
    - **Manifest:** XML file listing information about each item in the search results, excluding duplicate messages if de-duplication is enabled.
    - **Results:** Excel document providing details about each indexed item in the search results. For emails, it includes message location, date, subject, sender, and recipients. For SharePoint and OneDrive for Business documents, it includes document URL, site collection URL, modification date, and document name.

1. 