# Lab 18 - Defender for Cloud Apps Access and Session Policies

## Lab scenario

Microsoft Defender for Cloud Apps  allows us to create additional Conditional Access policies specific to the cloud apps that we are monitoring.  Creating these policies can be done from within the Control menu within the Microsoft Defender for Cloud Apps  portal.

## Lab objectives

After completing this lab, you will be able to complete the following exercises:

+ Exercise 1 - Create and test the Conditional Access App Contol policy
+ Exercise 2 - Setup alerts in Microsoft Defender for Cloud Apps

## Estimated time: 30 minutes

## Architecture Diagram

   ![](./media/arch18.png)

## Exercise 1 - Create and test the Conditional Access App Control policy
  
  In this lab, you will learn to create and test a Conditional Access App Control policy. 

### Task 1 - Confirm that PradeepG has unconditional access to FORMS

In this task, you will confirm that Pradeep Gupta has unconditional access to Microsoft Forms by logging in through an InPrivate browsing window and verifying that the application opens without any warning messages. You will also manage Pradeep's credentials in the Azure portal if necessary.

1. Open a Microsoft Edge browser, launch a new **InPrivate** browsing window, and browse to [https://forms.microsoft.com](https://forms.microsoft.com).

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/signin.png)

1. Select **Sign in** and log in as Pradeep Gupta.
    
   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | pradeep.gupta@`your domain name.com`|
   | Password| Enter the password for Pradeep Gupta|

4. To find the username for **Pradeep Gupta**, login to the Azure portal using the credentials given in the **Environment Details** page

5. In **Search resources, services and docs (1)** search and select for **Microsoft Entra ID (2)**.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/MicrosoftentraID.png)

6. Navigate to the **Users** section of the Microsoft Entra ID, and copy the mail id of Pradeep Gupta.

   ![image](./media/sc-300-lab18-2.png)

7. From the Microsoft Entra ID **Users** section, click on **Pradeep Gupta** user, and from the top navigation pane click on **Reset Password** and copy the temporary password and login and reset the password to **Pa55w.rd@123**

    ![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/pradeep.png)

   >**Note:** Copy the username and password of Pradeep in a notepad file because you will be needing it for further tasks.
    
8. Confirm that Microsoft Forms opens and that you do not get any warning messages.

   >**Note:** You will not have access to Microsoft Forms.

9. Close the InPrivate browsing window.

### Task 2 - Configure Microsoft Entra ID to work with Defender for Cloud Apps

In this task, you will configure Microsoft Entra ID to work with Defender for Cloud Apps by creating a Conditional Access policy to monitor Pradeep's usage of Microsoft Forms. You will also disable security defaults to enable the new policy and finalize the configuration.

1. Navigate to Azure Portal, in **Search resources, services and docs (1)** search and select for **Microsoft Entra ID (2)**.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/MicrosoftentraID.png)

2. From the left-hand navigation pane, under **Manage**, select **Security**.

3. From the left-hand navigation pane, under **Protect**, select **Conditional Access**.

4. Select **+ Create new policy**.

5. Enter a policy name, **Monitor Pradeep using Forms**.

6. Under **Users**, select **0 users and groups selected**, under **Include**, select **Select users and groups**, and select **Users and groups**. Choose **Pradeep Gupta** account for the lab tenant and select **Select**.

8. Under Target resources, select **No target resources selected**, under **Include**, select **All resources (formerly 'All cloud apps')**. 

9. Under **Access controls**, under **Session**, select **0 controls selected**.

10. Select the **Use Conditional Access App Control** box, select the drop-down and select **Monitor only (Preview)**, and select **Select**.

11. Under **Enable policy**, select **On**, you will receive an alert message to disable security defaults. Click on the provided hyperlink.
    
    ![](./media/sc-300-lab18-4.png)
    
12. On the Security Defaults setup page, select the option **Disabled (1)**. For the **Reason for disabling**, choose** _My organization is planning to use Conditional Access_ (2)** and click on **Save (3)**.

    ![](./media/sc-300-lab18-3.png)

13. Click on **Disable** when prompted.
    
14. Select **Create**.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

       <validation step="63811d93-2f19-414a-8080-7af5209c23db" />

### Task 3 - Log into Forms and validate that conditional access is monitoring

In this task, you will log into Microsoft Forms as Pradeep Gupta in an InPrivate browsing window to validate that the conditional access policy is monitoring access.

1. Launch a new InPrivate browsing window and browse to [https://forms.microsoft.com](https://forms.microsoft.com).

2. Select **Sign in** and log in as Pradeep Gupta.

   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | pradeep.gupta@`your domain name.com`|
   | Password| Pa55w.rd@123|
    
   >**Note:** Copy the username for Pradeep from the notepad file as mentioned in the previous task.
   
3. Confirm that you get a new message as shown below:

   - Access to Microsoft Forms is monitored.
   
     ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/access.png)

4. Close the InPrivate browsing window.

   >**Note:** If the above message does not appear as expected, verify if the conditional access policy has been created. If it has, refresh the page and wait for a while for the message to appear.

## Exercise 2 - Setup alerts in Microsoft Defender for Cloud Apps

Registering your application establishes a trust relationship between your app and the Microsoft identity platform. The trust is unidirectional: Your app trusts the Microsoft identity platform—not the other way around.

### Task 1 - Access Microsoft Defender for Cloud Apps and create Conditional Access App Control

In this task, you will access Microsoft Defender for Cloud Apps to create a Conditional Access App Control policy, configuring it to monitor Microsoft Forms access and setting up alerts for email notifications.

1. Open a new tab and browse to the [https://security.microsoft.com](https://security.microsoft.com).

   >**Note:** If you get  **Your new endpoint protection home** page close it.

1. In the **Microsoft Defender** portal menu, from the left-hand navigation pane, under **Cloud apps** select **Policies** drop-down, and select **Policy management (1)**. Click on the **Enable Office 365 Cloud App Security (2)** to allow your subscription to use Office 365 Cloud App Security.

   ![image](./media/sc-300-lab18-1.png)

1. Select **+ Create policy**. Select **Access policy**.

   >**Note:** If you encounter a situation where no conditional access policy appears to be active even though one has been created, please try refreshing the page or logging out and back in.

1. Enter a name for the policy, **Monitor Microsoft Forms access**.

1. Leave the **Category** as **Access control**.

1. Under **Activities matching all of the following**, select the drop-down for **Intune compliant, Microsoft Entra Hybrid joined** and unselect **Microsoft Entra Hybrid joined**.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/new-lab18-1.png)

1. Select the drop-down for **Select apps**, select **Microsoft Forms**.

1. Leave **Actions** as **Test**.

1. Under **Alerts**, leave **Create an alert...** checked and select **Send alert as email**.

1. Enter and select **<inject key="AzureAdUserEmail"></inject>**.

1. Select **Create** to create the access policy.

### Task 2 - Log in as Pradeep to Forms to trigger activity

In this task, you will log in to Microsoft Forms as Pradeep Gupta to trigger activity, ensuring the account access is monitored.

1. Launch a new InPrivate browsing window and browse to [https://forms.microsoft.com](https://forms.microsoft.com).

1. Select **Sign in** and log in as Pradeep Gupta.

   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | pradeep.gupta@`your domain name.com`|
   | Password| Pa55w.rd@123|
    
   >**Note:** Copy the username for Pradeep from the notepad file as mentioned in the previous task.

1. Confirm that you get a new message as shown below:

   - Access to Microsoft Forms is monitored.

     ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/access.png)

1. Close the InPrivate browsing window.

### Task 3 - Review the Activity in Defender for Cloud Apps

In this task, you will review activity in Defender for Cloud Apps by accessing the activity log, filtering for Microsoft Forms, and checking sign-on records.

1. Return to the browser running Microsoft Defender.

2. Refresh the browser to ensure the most recent data is downloaded.

3. From the left-hand navigation pane, under **Cloud apps**, select **Activity log**.

4. Using the **App: filter** pick **Microsoft Forms** from the list.

5. Notice the sign-on records for Pradeep.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/msforms2.png)

   >**Note:** Please log out and log back in for the logs to appear. It may take 1-2 hours for the logs to generate, so it's possible they might not be visible within the duration of the lab session.

### Review

In this lab, you have completed the following exercises:
- Created and tested the Conditional Access App Control policy
- Setup alerts in Microsoft Defender for Cloud Apps

### You have successfully completed the lab
