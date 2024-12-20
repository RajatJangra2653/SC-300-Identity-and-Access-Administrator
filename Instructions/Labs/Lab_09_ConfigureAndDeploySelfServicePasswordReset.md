# Lab 09 - Configure and deploy self-service password reset

## Lab scenario
The company has decided to empower the employees and enable self-service password reset. You must configure this setting in your organization.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1 - Create a group to assign SSPR to it
- Task 2 - Enable SSPR for the group
- Task 3 - Register for SSPR with Alex
- Task 4 - Test SSPR
- Task 5 - What happens if you try a user not in SSPRTesters group?

## Estimated time: 15 minutes

## Architecture diagram

   ![](./media/arch-09.png)

# Exercise 1 - Create a group with SSPR enabled and add users to it

In this lab, you'll create a group with SSPR enabled and add users to it, configure SSPR for the group, and register Alex for SSPR. You'll then test the SSPR functionality and observe the behavior when attempting to use SSPR with a user who is not part of the SSPRTesters group.

### Task 1 - Create a group with SSPR enabled and add users to it

You want to roll out SSPR to a limited set of users first to make sure your SSPR configuration works as expected. Let's create a security group for the limited rollout and add a user to the group.

1. On Azure Portal page, in **Search resources, services and docs (G+/)** box at the top of the portal, enter **Microsoft Entra ID (1)**, and then select **Microsoft Entra ID (2)** under services.

    ![](./media/lab08-sc300-3.png)

1. On the **Microsoft Entra ID** blade, under **Manage** section, select **Groups**. 

    ![](./media/lab09-sc300-1.png)

1. On **Group | All groups** and select **+ New Group**.

    ![](./media/lab09-sc300-2.png)

1. Create a new group using the following information:

    | **Setting**| **Value**|
    | :--- | :--- |
    | Group type| Security|
    | Group name| SSPRTesters|
    | Group description| Testers of SSPR rollout|
    | Membership type| Assigned|
    | Members| Alex Wilber |
    | |  Allan Deyoung |
    | | Bianca Pisani |

    ![](./media/lab09-sc300-3.png)

3. Select **Create**.

    ![](./media/lab09-sc300-4.png)

   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Hit the Validate button for the corresponding task. You can proceed to the next task if you receive a success message.
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

   <validation step="e11d21a6-fbc6-42b0-8271-5413eb1ee9b4" />

### Task 2 - Enable SSPR for the group

1. Browse back to the Microsoft Entra ID page.

1. Under **Manage**, select **Password reset**.

   ![](./media/lab09-sc300-5.png)

1. On the Password reset page Properties page, under **Self service password reset enabled**, review the **Selected** button is selected if not follow the below steps.

   -  Under **Self service password reset enabled** select the **Selected (1)** button then click on **No groups selected (2)** under **Select group**.

      ![](./media/lab09-sc300-6.png)
      
   - On Default password reset policy select **SSPRTesters** then click on **Select** 

      ![](./media/lab09-sc300-7.png)

    - Under Selected group make sure SSPRTesters is selected and click on **Save**.

      ![](./media/lab09-sc300-8.png)
      
1. Under **Manage**, select and review the default values for the **Authentication methods**, **Registration**, **Notifications**, and **Customization** settings.

    >**Note** it is important to have **phone** selected as one of the authentication methods for the rest of this lab, but you can have other options as well.

### Taks 3 - Register for SSPR with Alex

Now that the SSPR configuration is complete, register a mobile phone number for the user you created.

1. Open an InPrivate browser session and then browse to [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).

    >**Note:** This is to ensure you well be prompted for user authentication.

1. Sign in as **alex.wilber@ `<<organization-domain-name>>.com`**, with the password = Enter the admin password of the tenant(Refer the **Environment Details** tab to retrieve the Alex's password).

    ![](./media/1.png)

    >**Note:** If prompted to update your password, enter a new password of your choice. Be sure to record the new password.

1. In the **More information required** dialog box, select **Next**.

1. On the Keep your account secure page, click on **I want to set up a different method** and from **Choose a different method** window, select **Phone** and click on **Confirm** and **Next**

     ![](./media/lab9-5.png)

    >**Note** - In this lab, you will use the **Phone** option. Enter your mobile phone details.

1. On the Keep your account secure page, ensure **Receive a code** is selected and enter your personal cell phone number into the phone number field and select **Next**.

1. When you receive the code on your mobile phone, enter the code in the text box and then select **Next**.

1. After your phone has been registered, select **Next** and then select **Done**.

1. Close the browser. You do not need to complete the sign in process.

### Task 4 - Test SSPR

Now let's test whether the user can reset their password.

1. Open an InPrivate browser session and then browse to [https://portal.azure.com](https://portal.azure.com).

    This is to ensure you well be prompted for user authentication.

1. Enter **alex.wilber@`<<organization-domain-name>>.com`**, and then select **Next**.

1. On the Enter password page, select **Forgot my password**.

   ![](./media/lab9-6.png)

1. On the Get back into your account page, complete the requested by entering captcha and then select **Next**.

   ![](./media/lab9-7.png)

1. In the **verification step 1** task, select **Text my mobile phone (1)**, **enter your phone number (2)** and then select **Text (3)**.

   ![](./media/lab9-8.png)

1. Enter your verification code and then select **Next**.

1. In the choose a new password step, enter and then confirm your new password. Recommend password **Pass@w.rd1234**
    ![](./media/lab9-9.png)

1. When complete, select **Finish**.

1. Now, browse to [https://portal.azure.com](https://portal.azure.com).

1. Sign in as **alex.wilber@`<<organization-domain-name>>.com`** with the new password you created.

10. Enter your verification code and then verify you can complete the sign in process.

    **Note**: If **Protect your account** window prompted please click on **Skip for now**

12. When finished, close your browser.

### Task 5 - What happens if you try a user not in SSPRTesters group?

1. As a test, open a new InPrivate browser window, and browse to [https://portal.azure.com](https://portal.azure.com).

1. Type the username **miriam.graham@`<<organization-domain-name>>.com`**, and then select **Next**.
   
1. On the Enter password page, select **Forgot my password**.

1. On the Get back into your account page, complete the requested information and then select **Next**.

1. You can see the error message which states, **You can't reset your own password because password reset isn’t turned on for your account.**

    ![](./media/lab9-11.png)

1. Close the InPrivate browser.

## Review
In this lab, you have completed:
- Added users to a group to assign SSPR
- Enabled SSPR for the group
- Registered for SSPR with Alex
- Tested SSPR
- What happens if you try a user not in the SSPRTesters group?

### You have successfully completed the lab
