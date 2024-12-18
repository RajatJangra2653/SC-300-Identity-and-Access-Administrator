# Lab 26: Configure Privileged Identity Management for Microsoft Entra ID roles

## Lab scenario

A Privileged role administrator can customize Privileged Identity Management (PIM) in their Azure Active Directory (Azure AD) organization, including changing the experience for a user who is activating an eligible role assignment. You must become familiar with configuring PIM.

   >**Note:** There have been on-going changes to requiring MFA in lab environments. When you switch between users to complete this lab, you may be prompted to set up MFA.

## Lab Objectives

After completing this lab, you will be able to:
- Exercise 1 - Configure Microsoft Entra ID role settings
- Exercise 2 - PIM with Microsoft Entra ID roles

## Architecture Diagram

![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/arch26.png)

## Estimated time: 45 minutes

## Exercise 1 - Configure Microsoft Entra ID role settings

In this exercise, you will learn how to customize role settings by configuring Microsoft Entra ID roles.

### Task 1 - Open role settings

In this task ,you will access and review the settings for the Compliance Administrator role in Azure AD Privileged Identity Management.

1. In the Azure portal, search for and  select **Microsoft Entra ID Privileged Identity Management.**

1. In the Privileged Identity Management page, in the left navigation, select **Microsoft Entra roles** under **Manage** option.

1. On the Quick start page, in the left navigation, select **Settings (1)** under **Manage** option.
  
1. Review the list of roles and then, in the **Search by role name (2)**, enter **compliance**.
   
   ![Screen image displaying the Azure AD roles page with the Settings menu highlighted](./media/set2.png)

1. In the results, select **Compliance Administrator**.

1. Review the role setting details information.

### Task 2 - Require approval to activate

In this task, you will configure the Compliance Administrator role to require approval for activation by enabling the approval setting, selecting the approvers, and saving the changes.

1. In the Role setting details page, on the top menu, select **Edit**.

    ![Screen image displaying the top portion of the Role setting details -Compliance Administrator page with Edit highlighted](./media/role12.png)

2. In the Edit role setting – Compliance Administrator page, select the **Require approval to activate** check box.

3. Select **Select approvers**.

4. In the Select a member pane, select your administrator account and then select **Select**.

    ![Screen image displaying the edit role settings page and select a member pane with the selected members highlighted](./media/admin123.png)

5. Once you have configured the role settings, select **Update** to save your changes.

## Exercise 2 - PIM with Microsoft Entra ID roles

### Task 1 - Assign a role

With Microsoft Entra ID, a Global administrator can make permanent Microsoft Entra ID admin role assignments. These role assignments can be created using the Azure portal or using PowerShell commands.

The Microsoft Entra ID Privileged Identity Management (PIM) service also allows Privileged role administrators to make permanent admin role assignments. Additionally, Privileged role administrators can make users eligible for Microsoft Entra ID admin roles. An eligible administrator can activate the role when they need it, and then their permissions expire once they're done.

Follow these steps to make a user eligible for an Azure AD admin role.

1. Search for and then select **Microsoft Entra ID Privileged Identity Management.**

2. In the Privileged Identity Management page, in the left navigation, select **Microsoft Entra roles.**

3. On the Quick start page, in the left navigation, under Manage select **Roles (1)**.

4. On the top menu, select **+ Add assignments (2)**

    ![Screen image displaying Azure AD roles with Add assignments menu highlighted](./media/aroll.png)

5. In the Add assignments page, on the **Membership** tab, review the settings.

6. Select the **Select role** menu and then select **Compliance Administrator**.

7. You can use the **Search role by name** filter to help locate a role.

8. Under **Select member(s),** select **No member selected**.

9. In the Select a member pane, select **Miriam Graham** and then select **Select**.

   ![Screen image displaying the select a member pane with a selected member highlighted](./media/miriam12345.png)

10. In the Add assignments page, select **Next >**.

11. On the **Settings** tab, under **Assignment type**, review the available options. For this task, use the default setting.

    - Eligible assignments require the member of the role to perform an action to use the role. Actions might include performing a multi-factor authentication (MFA) check, providing a business justification, or requesting approval from designated approvers.
    - Active assignments do not require the member to perform any action to use the role. Members assigned as active have the privileges always assigned to the role.

12. Review the remaining settings and then select **Assign**.

    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
    > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task.
    > - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
    > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

   <validation step="463fb3a1-c805-4bd6-96ca-3e48f02ec7b4" />

### Task 2 - Log in with Miriam

In this task, you will log in to the Azure Portal as Miriam Graham, reset her password if needed, and check that she has the Compliance Administrator role assigned.

1. Open a new InPrivate browser window.

2. Connect to the Azure Portal (https://portal.azure.com).

3. If it opens with a user logged in, Select on their name in the upper-right corner and select **Sign in as a different account**.

4. Log in a Miriam.

   | Field | Value |
   | :--- | :--- |
   | Username | **miriam.graham@** `<<your domain.onmicrosoft.com>>` |
   | Password |  Enter the password for Miriam Graham |

   >**Note:** To find the username for Miriam Graham, login to the Azure portal and navigate to the Users section of the Microsoft Entra ID, and copy the user name.

   >**Note:** From the Microsoft Entra ID **Users** section, click on **Miriam Graham** user and from the top navigation pane, click on **Reset Password** and subsequently click on **Reset Password**  again and copy the temporary password and login to Azure portal and reset the password to **Pa55w.rd@123**

5. Close the **Welcome to Microsoft Azure dialog**.

6. From the **Search resource, services, and docs** bar look for **Microsoft Entra ID**, and open the page.

7. On the **Overview** page, look for the **My feed**.

8. Select **View Profile** under Miriam Graham's name; this with open Miriam's profile page.

   ![Screen image displaying the select a member pane with a selected member highlighted](./media/miriam.png)

9. From the left navigation pane,under Manage select **Assigned roles** then select **Eligible assignments**.

10. Notice that the **Compliance Administrator** role is now available to Miriam.

### Task 3 - Activate your Microsoft Entra ID roles

When you need to assume an Azure AD role, you can request activation by opening **My roles** in Privileged Identity Management.

1. From the **Search, resources, services, and docs** bar, look for Privileged.

2. Open the **Microsoft Entra ID Privileged Identity Management** page.

3. On the Privileged Identity Management page, in the left navigation menu, select **My roles (1)** under **Tasks**.

4. In the My roles page, review the list of **Eligible assignments (2)**.

5. In the Compliance Administrator role row, select **Activate (3)**.

    ![Screen image displaying My roles with eligible role assignments highlighted](./media/role567.png)

7. In the Activate – Compliance Administrator pane, select **Additional verification required** and then follow the instructions to provide additional security verification. You are required to authenticate only once per session.

    ![Screen image displaying a popup to activate the compliance administrator](./media/activate121.png)

    >**Verification** - Based on our current lab environment configuration, you will be required configure MFA and log in successfully.
    
     - If **Action required** pop-up window appears, click on **Next**.

     - On **Start by getting the app** page, click on **Next**.
      
     - In **Android**, go to the play store and Search for **Microsoft Authenticator** and Tap on **Install**.

         ![Install](./media/authapp.png)

         >**Note**: For **iOS**, Open app store and repeat the steps.

         >**Note**: Skip If already installed.
   
     - Open the app and click on **Scan a QR code**.

     - Scan the QR code visible on the screen and click on **Next**.

        ![QR code](./media/qrcode.png)
   
     - Enter the digit displayed on the Screen in the Authenticator app on mobile and tap on **Yes**.

     - Once the notification is approved, click on **Next**.

        ![Approved](./media/notification.png)

     - Click on **Done**.
  
     - If prompted to stay signed in, you can click **"No"**.

     - Tap on **Finish** in the Mobile Device.

       >**NOTE**: While logging in again , enter the digits displayed on the screen in the **Authenticator app** and click on Yes.

9. After you have completed the additional security verification, back in the Azure portal, in the **Activate – Compliance Administrator** pane, in the **Reason** box, enter the **This is my justification for activating this role**.

     >**Notes:** If required you will have to sigin in again as Miriam Graham with a SMS verification.
     
     >**Important Note** - The principal of least privilege, you should only activate the account for the amount of time you need it.  If the work needed to be done, only takes 1.5 hours, then set the duration to two hours.  Similarily, if you know that you won't be able to do the work until after 3 p.m., choose a Custom activation time.

10. Select **Activate**.

### Task 4 - Assign a role with restricted scope

For certain roles, the scope of the granted permissions can be restricted to a single admin unit, service principal, or application. This procedure is an example if assigning a role that has the scope of an administrative unit.

1. Now, go to the portal where you have logged in as the ODL user in the normal Microsoft Edge browser.
2. Browse to the Privileged Identity Management page, and in the left navigation menu, select Azure **Microsoft Entra roles** under **Manage** option.
3. Under Manage select **Roles**.
4. In the Roles page, on the top menu, select **+ Add assignments.**

5. In the Add assignments page, select the **Select role** menu and then select **User administrator.**

6. Select the **Scope type** menu and review the available options. For now, you will use the **Directory** scope type.

   >**Tip** - Go to [https://docs.microsoft.com/en-us/azure/active-directory/roles/admin-units-manage](https://docs.microsoft.com/en-us/azure/active-directory/roles/admin-units-manage) for more information about the administrative unit scope type.

7. As you did when assigning a role without a restricted scope, you would add members and complete the settings options. For now, select **Cancel**.

### Task 5 - Update or remove an existing role assignment

Follow these steps to update or remove an existing role assignment.

1. In the **Privileged Identity Management | Microsoft Entra roles** page, in the left navigation, select **Assignments**.

2. In **Assignments** list, for Compliance Administrator, review the options in the **Action** column.

    ![Screen image displaying the options listed in the action column of the Compliance Adminsitrator](./media/remove121.png)

3. Select **Update** and review the options available in the Membership settings pane. When complete, close the pane.

4. Select **Remove**.

5. In the **Remove** dialog box, review the information and then select **Yes**.

## Review
In this lab you have completed the following tasks:
- Configured Azure AD role settings
- Configured PIM with Azure AD roles

## You have successfully completed the lab
