# Lab 14 - Enable sign in and user risk policies

## Lab scenario

As an additional layer of security, you need to enable and configure your Azure AD organization's sign in and user risk policies.

## Lab Objectives

After completing this lab, you will be able to:
- Task 1 - Configure the policy
- Task 2 - Enable Sign-in risk policy

## Architecture Diagram

![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/arch14.png)

## Estimated time: 10 minutes

### Before the Hands-on lab

1. Sign in to the [https://portal.azure.com]( https://portal.azure.com) using credentials provided in the rnvironment (Global administrator account).

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
   - **Password:** <inject key="AzureAdUserPassword"></inject>

2. Open the portal menu and then search for and select **Microsoft Entra ID**.

3. On the **Microsoft Entra ID** page, in the left navigation under **Manage**, select **Users**.

4. Select <inject key="AzureAdUserEmail"></inject> 

5. From the **Users** page, in the left navigation under **Manage** select **Assigned Roles**.

   ![Screen image displaying the User risk policy page and highlighted browsing path](./media/assigned-roles.png)

6. Select **+ Add Assignments**. From the list of roles, choose **Conditional Access Administrator** and click on **Add**.
 
   ![Screen image displaying the User risk policy page and highlighted browsing path](./media/assign2.png)

### Exercise 1 - Enable User risk policy

#### Task 1 - Configure the policy

1. Sign in to the [https://entra.microsoft.com](https://entra.microsoft.com) using the credentials provided in the environment (Global administrator account).

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
   - **Password:** <inject key="AzureAdUserPassword"></inject>

2. In the left navigation menu, under **Identity (1)**, select **Protection (2)**, and under **Protection** select **Identity protection (3)**.

3. In the Identity protection, in the left navigation, select **User risk policy (4)**.

    ![Screen image displaying the User risk policy page and highlighted browsing path](./media/select-identity-protection.png)

4. Under **Assignments**, select **All users** and review the available options.

5. You can select from **All users** or **Select individuals and groups** if limiting your rollout.

6. Additionally, you can choose to exclude users from the policy.

7. Under **User risk**, select **Low and above**.

8. In the User risk pane, select **High** and then select **Done**.

9. Under **Controls** > **Access**, select **Block access**.

10. In the Access pane, review the available options.

    **Tip** - Microsoft's recommendation is to Allow access and Require password change.

11. Select the **Require password change** check box and then select **Done**.

12. Under **Policy enforcement**, toggle to  **Enabled** and then select **Save**.

    ![](./media/user-risk-policy.png)

#### Task 2 - Enable Sign-in risk policy

1. On the Identity protection page, in the left navigation, select **Sign-in risk policy**.

2. As with the User risk policy, the Sign-in risk policy can be assigned to users and groups and allows you to exclude users from the policy.

3. Under **Sign-in risk**, select **Low and above**.

4. In the Sign-in risk pane, select **High** and then select **Done**.

5. Under **Controls** > **Access**, select **Block access**.

6. Select the **Require multi-factor authentication** check box and then select **Done**.

7. Under **Policy enforcement**,  toggle to  **Enabled** and then select **Save**.

## Review

In this lab you have completed the following tasks:

- Configured the policy
- Enabled Sign-in risk policy

## You have successfully completed the lab
