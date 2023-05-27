---
lab:
    title: 'Exercise 3 - Create a case with eDiscovery (Standard)'
    module: 'Module 4 - Monitor and investigate data and activities by using Microsoft Purview'
---

# Lab 4 - Exercise 3 - Configure Records Management

Assuming the role of Joni Sherman, a Compliance Administrator for Contoso Ltd., you're confronted with a wrongful termination lawsuit from a former employee. Your task involves securing relevant electronic data related to the case by imposing a legal hold on all pertinent data sources. The legal hold, defined by specific date range, keywords, and content locations, ensures no data is lost or altered. Following the data preservation, you'll proceed to review and analyze the secured information to discern any evidence supporting or refuting the ex-employee's allegations, aiding Contoso Ltd.'s defense in this legal dispute.

## Task 1 - Create an eDiscovery (Standard) Case

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

1. In **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman** JoniS@WWLxZZZZZZ.onmicrosoft.com (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider).  Joni's password should be provided by your lab hosting provider.

1. Select the drop down for **eDiscovery** fro the left navigation pane, then select **Standard**.

1. On the **eDiscovery (Standard)** select **+ Create a case**.

1. From the **New case** flyout page, in the **Name** field enter **Wrongful Termination Case**.

1. In the **Description** field enter **This eDiscovery case is related to a wrongful termination lawsuit filed against Contoso Ltd. by a former employee.** then select **Save**.

1. Back on the **eDiscovery (Standard)** page, select **Settings**.

1. Under **Access & permissions** select **Select**.

1. On the **Access & permissions** flyout page, under **Manage members** select **+ Add**.

1. On the **Add members** flyout page type in *Diego* then press enter to find *Diego Siciliani*.

1. Select the checkbox next to Diego's name, then select **Add** at the bottom of the page.

1. Back on the **Access & permissions** page, select **Exit** to go back to the case settings page.

## Task 2 - Create an eDiscovery (Standard) hold

1. You should still be logged in with Joni's account. If not, open **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the left navigation pane, navigate to **eDiscovery**, then select **Standard**.

1. Select the **Wrongful Termination Case** created in the previous task, then select **Hold**.

1. On the **Hold** page of the Wrongful Termination Case, select **+ Create**.

1. From the **New Hold** flyout page on the right, under **Name your hold** in the **Name** field, enter *Wrongful Termination Hold*. In the **Description** field enter *This legal hold is related to the Contoso Ltd. wrongful termination lawsuit and is designed to preserve all relevant electronic data related to the case.*

1. Select **Next**.

1. On the **Choose locations** page, select **Exchange mailboxes**. Under **Included** select **Choose users, groups, or teams**.

1. On the **Exchange mailboxes** flyout page on the right, in the **Search** field enter *Lidia* then press enter. Select the checkbox for **Lidia Holloway** then select **Done**.

1. Back on the **Choose locations** page select **Next**.

1. On the **Query** page, ensure **Query builder** is selected, then select the trashcan in the **Keyword** box to remove this search criteria.

1. Select the dropdown for **+ Add condition** then select **Date**.

1. Leave the default date range in the **Date** fields, then select **Next**.

1. On the **Review your settings** page select **Submit**.

1. You should get a message that the hold **Succeeded**. On this page select **Done**.

## Task 3 - Create an eDiscovery (Standard) search

1. You should still be logged in with Joni's account. If not, open **Microsoft Edge**, navigate to **https://compliance.microsoft.com** and log into the Microsoft Purview portal as **Joni Sherman**.

1. In the left navigation pane, navigate to **eDiscovery**, then select **Standard**.

1. Select the **Wrongful Termination Case** created in the previous task, then select **Searches**.

1. On the **Searches** page of the Wrongful Termination Case page, select **+ New search**.

1. On the **Name and description** page of the **New search** wizard, in the **Name** field enter *Wrongful Termination Search*. In the **Description** field enter *This search is related to the Contoso Ltd. wrongful termination lawsuit and is designed to identify and collect all relevant electronic data related to the case.*

1. Select **Next**.

1. On the **Locations** page, select **On** for **Exchange mailboxes**, **SharePoint sites**, and **Exchange public folders** then select **Next**.

1. On the **Define your search conditions** page select the radial for **KQL editor**.

1. In the KQL editor box, enter `To:Lidia OR From:Lidia OR Cc:Lidia OR Bcc:Lidia` then select **Next**.

1. On the **Review your search and create it** page select **Submit**.

1. On the **New search created** page select **Done**.