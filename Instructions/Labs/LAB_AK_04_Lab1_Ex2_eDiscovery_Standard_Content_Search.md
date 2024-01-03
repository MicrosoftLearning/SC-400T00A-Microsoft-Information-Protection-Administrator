---
lab:
    title: 'Exercise 2 - Case investigation with eDiscovery (Standard) and content search'
    module: 'Module 4 - Monitor and investigate data and activities by using Microsoft Purview'
---

# Lab 4 - Exercise 2 - eDiscovery (Standard) and Content search

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. Currently, Contoso Ltd. is dealing with a wrongful termination lawsuit filed by a former employee. As part of your responsibility, you are entrusted with the task of preserving the necessary electronic data relevant to the case. To accomplish this, you will use eDiscovery (Standard) to identify and secure the relevant information. By using eDiscovery techniques, you'll make sure that Contoso Ltd. can meet its legal obligations by preserving and accessing the necessary electronic evidence for the lawsuit.

## Task 1 - Create an eDiscovery (Standard) Case

In this task, you will create an eDiscovery (Standard) case as Joni Sherman.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).

1. Select the drop down for **eDiscovery** from the left navigation pane, then select **Standard**.

1. On the **eDiscovery (Standard)** select **+ Create a case**.

1. From the **New case** flyout page, in the **Name** field enter **Wrongful Termination Case**.

1. In the **Description** field enter **This eDiscovery case is related to a wrongful termination lawsuit filed against Contoso Ltd. by a former employee.** then select **Save**.

1. Back on the **eDiscovery (Standard)** page, select the newly created **Wrongful Termination Case**.

1. On the page for the Wrongful Termination Case select **Settings** from the top navigation bar, then select the **Select** button under **Access & permissions**.

1. On the **Access & permissions** flyout page, under **Users** select **+ Add**.

1. On the **Add members** flyout page search for _Diego_, select the checkbox to the left of _Diego Siciliani_, then select **Add** at the bottom of the page to grant Diego access to the eDiscovery case.

1. Back on the **Access & permissions** page, select **Close** to go back to the case settings page.

You have now successfully created an eDiscovery (Standard) case titled "Wrongful Termination Case" and added Diego Siciliani as a member to manage access and permissions.

## Task 2 - Create an eDiscovery (Standard) hold

In Task 2 you will create an eDiscovery (Standard) hold as part of the "Wrongful Termination Case" previously created. This hold preserves all relevant electronic data related to the Contoso Ltd. wrongful termination lawsuit.

1. You should still be logged in with Joni's account. If not, open **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the left navigation pane, navigate to **eDiscovery**, then select **Standard**.

1. Select the **Wrongful Termination Case** created in the previous task, then select **Hold**.

1. On the **Hold** page of the Wrongful Termination Case, select **+ Create**.

1. From the **New Hold** flyout page on the right, under **Name your hold** in the **Name** field, enter _Wrongful Termination Hold_. In the **Description** field enter _This legal hold is related to the Contoso Ltd. wrongful termination lawsuit and is designed to preserve all relevant electronic data related to the case._, then select **Next**.

1. On the **Choose locations** page, select **Exchange mailboxes**. Under **Included** select **Choose users, groups, or teams**.

1. On the **Exchange mailboxes** flyout page on the right, in the **Search** field, search for _Lidia_, then select the checkbox to the left of  **Lidia Holloway**. Select **Done**.

1. Back on the **Choose locations** page, select **Next**.

1. On the **Query** page, ensure **Query builder** is selected, then select the trashcan in the **Keyword** box to remove this search criteria.

      ![Screenshot of Manage roles option](../Media/remove_keyword_search.png)

1. Select the dropdown for **+ Add condition** then select **Date**.

1. Leave the default date range in the **Date** fields, then select **Next**.

1. On the **Review your settings** page select **Submit**.

1. You should get a message that the hold **Succeeded**. On this page select **Done**.

You have successfully created an eDiscovery (Standard) hold.

## Task 3 - Create an eDiscovery (Standard) search

In Task 3 you will an eDiscovery (Standard) search within the "Wrongful Termination Case" previously created. This search aims to identify and collect all relevant electronic data related to the Contoso Ltd. wrongful termination lawsuit.

1. You should still be logged in with Joni's account. If not, open **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the left navigation pane, navigate to **eDiscovery**, then select **Standard**.

1. Select the **Wrongful Termination Case** created in the previous task, then select **Searches**.

1. On the **Searches** page of the Wrongful Termination Case page, select **+ New search**.

1. On the **Name and description** page of the **New search** wizard, in the **Name** field enter _Wrongful Termination Search_. In the **Description** field enter _This search is related to the Contoso Ltd. wrongful termination lawsuit and is designed to identify and collect all relevant electronic data related to the case._ Select **Next**.

1. On the **Locations** page, select **On** for **Exchange mailboxes**, **SharePoint sites**, and **Exchange public folders** then select **Next**.

1. On the **Define your search conditions** page select the radio button for **KQL editor**.

1. In the KQL editor box, enter:

    ```text
    To:Lidia OR From:Lidia OR Cc:Lidia OR Bcc:Lidia
    ```

1. Select **Next**.

1. On the **Review your search and create it** page select **Submit**.

1. On the **New search created** page, select **Done**.

By successfully creating the "Wrongful Termination Search" using the KQL editor and defining the search conditions, you have initiated a search process to identify and collect all relevant electronic data related to the Contoso Ltd. wrongful termination lawsuit.

## Task 4: Export search results

In this task you will export the search results obtained from the "Wrongful Termination Search."

1. You should still be logged in with Joni's account. If not, in **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the left navigation pane, navigate to **eDiscovery**, then select **Standard**.

1. Select the **Wrongful Termination Case** created in the previous task, then select **Searches**.

1. Under the **Searches** section, select the **Wrongful Termination Search** that was conducted in a previous task.

1. In the **Wrongful Termination Search** flyout page on the right, select the **Actions** drop down on the bottom of the page then select **Export results**.

1. On the **Export results** page under **Output options** select **All items, excluding one that have unrecognized format, are encrypted, or weren't indexed for other reasons**.

1. Under **Export Exchange content as** select **One PST file for each mailbox**.

1. Scroll down and select the check boxes for **Enable de-duplication for Exchange content** and **Include versions for SharePoint files**.

1. Review the estimation report at the bottom of the screen to get an idea of what types of items, the number of items, and the size of the items to be exported, then select **Export**.

1. A **compliance** pop up will appear letting you know **A job has been created**. Select **OK**.

1. Back on the **Searches** page select the **Exports** tab from the top navigation bar. Select the job named **Wrongful Termination Search_Export**

    >**Note**: If the status of the export is marked **Scheduling...** select **Refresh** until the **Export key** is available.

1. On the **Wrongful Termination Search_Export** flyout page under **Export key** select to **Copy to clipboard** to copy the export key.

1. At the top of the **Wrongful Termination Search_Export** page select **Download results** to download the results.

1. If you're prompted to install the **eDiscovery Export Tool**, select **Install**.

1. In the eDiscovery Export Tool, in the **Paste the export key that will be used to connect to the source:** field, paste in the **Export key** that was copied in a previous step.

1. Select **Browse** under **Select the location that will be used to store the downloaded files:**

1. In the **Browse For Folder** window select **Documents** then select **OK**.

1. Back in the **eDiscovery Export Tool** select **Start** to export the files.

1. Once you get a green check mark for **Processing has completed.** Your results have been downloaded. Select **Close** to close the window.

1. In the **eDiscovery Export Tool**, select the link for the **Export Location:** to open the locally exported files.

1. Explore the contents of the export:

    **Included in the export:**
    - **Export Summary:** An Excel document that contains a summary of the export, including the number of content sources searched, the estimated and downloaded sizes of the search results, and the estimated and downloaded number of items exported.
    - **Manifest:** A manifest file (in XML format) that contains information about each item included in the search results.
    - **Results:** An Excel document providing details about each indexed item in the search results. For emails, it includes message location, date, subject, sender, and recipients. For SharePoint and OneDrive for Business documents, it includes document URL, site collection URL, modification date, and document name.
    - **Skipped Items:** An Excel document that contains information about items that won't be downloaded, such as a folder or a document set.
    - **Trace.log:** Contains detailed logging information about the export process and can help uncover issues during export.
    - All search results and the export reports are included in a folder that has the same name as the Content search. The email messages that were exported are located in a folder named **Exchange**. Documents are located in a folder named **SharePoint**.

You have successfully exported the search results for the **Wrongful Termination Search**.

## Task 5: Export search report

In this task, you will review the search results obtained from the "Wrongful Termination Search" to identify any potential security or compliance issues related to the case.

1. You should still be logged in with Joni's account. If not, in **Microsoft Edge**, navigate to **`https://compliance.microsoft.com`** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the left navigation pane, navigate to **eDiscovery**, then select **Standard**.

1. Select the **Wrongful Termination Case** created in the previous task, then select **Searches**.

1. Under the **Searches** section, select the **Wrongful Termination Search** that was conducted in a previous task.

1. In the **Wrongful Termination Search** flyout page on the right, select the **Actions** drop down on the bottom of the page then select **Export report**.

1. On the **Export report** page under **Output options** select **All items, excluding one that have unrecognized format, are encrypted, or weren't indexed for other reasons**.

1. Select **Generate report**.

1. A **compliance** pop up will appear letting you know **A job has been created**. Select **OK**.

1. Back on the **Searches** page select the **Exports** tab from the top navigation bar. You should have a report named **Wrongful Termination Search_ReportsOnly**.

1. Select the **Wrongful Termination Search_ReportsOnly** report, and **Wrongful Termination Search_ReportsOnly** flyout page should appear on the right.

1. On the **Wrongful Termination Search_ReportsOnly** flyout page under **Export key** select to **Copy to clipboard** to copy the export key.

1. At the top of the **Wrongful Termination Search_ReportsOnly** page select **Download report** to download the report.

1. If you're prompted to install the **eDiscovery Export Tool**, select **Install**. If the tool is already installed, select **Open**.

1. In the eDiscovery Export Tool, in the **Paste the export key that will be used to connect to the source:** field, paste in the **Export key** that was copied in a previous step.

1. Select **Browse** under **Select the location that will be used to store the downloaded files:**

1. In the **Browse For Folder** window select **Documents** then select **OK**.

1. Back in the **eDiscovery Export Tool** select **Start** to download the report.

1. Once you get a green check mark for **Processing has completed.**, your report has been downloaded. Select **Close** to close the window.

1. In the **eDiscovery Export Tool**, select the link for the **Export Location:** to open the locally downloaded report.

1. Explore the contents of the report:

    **Included in the report:**
    - **Export Summary:** An Excel document that contains a summary of the export, including the number of content sources searched, the estimated and downloaded sizes of the search results, and the estimated and downloaded number of items exported.
    - **Manifest:** A manifest file (in XML format) that contains information about each item included in the search results.
    - **Results:** An Excel document providing details about each indexed item in the search results. For emails, it includes message location, date, subject, sender, and recipients. For SharePoint and OneDrive for Business documents, it includes document URL, site collection URL, modification date, and document name.
    - **Trace.log:** Contains detailed logging information about the export process and can help uncover issues during export.

1. Once you're finished reviewing the exported results, close the eDiscovery Export Tool and the file explorer windows then navigate back to Microsoft Edge.

You have successfully exported the search report for the **Wrongful Termination Search**. The report includes information such as an export summary, manifest, detailed item results, and a trace log. Review and analyze these findings to uncover insights relevant to the case. Once you have completed the review, you can close the eDiscovery Export Tool and file explorer windows.
