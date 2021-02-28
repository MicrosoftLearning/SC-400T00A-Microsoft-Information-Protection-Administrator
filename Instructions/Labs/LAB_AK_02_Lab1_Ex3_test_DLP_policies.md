# Exercise 3 - Test DLP Policies

You are Joni Sherman, the Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company offering driving instruction in the United States and you have configured DLP policies to make sure that sensitive customer information does not leave the organization. You decide to test your policies for correct functionality.

### Task 1 – Test a DLP policy

In this task, you will test the DLP policy that scans for credit card information to make sure that your users are informed about the block action and allowed to override it.

1. Log into the Client 1 VM (LON-CL1) as the **lon-cl1\admin** account.

2. In **Microsoft Edge**, navigate to **https://outlook.office.com** and log into Outlook as **Joni Sherman**.

3. In the top-left corner, select **New message** and select **Megan Bowen** as the recipient in the **To** field.

4. In the **Subject** field, type *Credit card information* and in the **Body** type *Credit Card: MASTERCARD 5239681227023651*.

5. Above the **To** field you should now see a mail tip that reads **Policy tip: Your email message conflicts with a policy in your organization.**

6. Select **Send** and review the resulting message. Megan should not receive this information and is therefore blocked.

You have successfully blocked an e-mail that includes credit card information.



# Proceed to Exercise 4