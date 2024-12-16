
# Lab 03: Assigning licenses using group membership

## Lab scenario

Your organization has decided to use security groups in Microsoft Entra ID to manage licenses. You need to configure a new security group and assign a license to that group and verify group member license's have been updated.

## Lab Objectives

After completing this lab, you will be able to complete the following exercises:

- Exercise 1 - Create a security group and add a user
- Exercise 2 - Create a Microsoft 365 group in Microsoft Entra ID
- Exercise 3 - Create a dynamic group with all users as members

## Architecture Diagram

![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/arch03.png)

## Estimated time: 25 minutes

## Exercise 1 - Create a security group and add a user

 In this exercise, you will create a security group to enhance access control and security measures and then include a user within the group to grant them specific permissions and restrictions as part of a broader security framework

### Task 1 - Check to see if user has access to Office 365
 
1. In the Azure portal, search for and  select **Microsoft Entra ID**.

1. In the left navigation menu, under **Manage**, select **Users**

1. From the Microsoft Entra ID **Users** section, click on **Delia Dennis** user, copy the **Username**  and from the top navigation tab click on **Reset Password** and copy the temporary password.

    ![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/azureaad.png)

1. Launch a new **InPrivate** browser window. Copy and paste this link in the browser window [https://www.office.com](https://www.office.com).

1. Select Sign in and connect as **Delia Dennis**, 

   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | delia.dennis@`your domain name.com`|
   | Current Password| Temporary Password you had copied in the previous step|
   | New Password| Pa55w.rd@123 |
   | Confirm Password| Pa55w.rd@123 |

    >**Note:** Enter the username and password that you had copied in the previous step.

1. You should connect to the Office.com website, but see a message indicating you don't have a license.

      ![Screen image the Office.com website with Delia Dennis logged in but no office applications are available, because no license is assigned.](./media/msoffice.png)
    
1. Close the browser window.

### Task 2 -  Create a security group in Microsoft Entra ID

1. In the search resources tab in the azure portal, type **Microsoft Entra ID** and navigate to it.

2. In the left navigation, under **Manage**, select **Groups**.

3. In the Groups page, on the menu, select **New group**.

4. Create a group using the following information:

   | **Setting**| **Value**|
   | :--- | :--- |
   | Group type| Security|
   | Group name| sg-SC300-O365|
   | Membership type| Assigned|
   | Owners| *Assign your own administrator account as the group owner*|

   ![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/odluser.png)

5. Select the **No members selected** text under Members.

6. Search for and select **Delia Dennis**  from the list of users.

7. Select the **Select** button.

8. Select the **Create** button.

9. When complete, verify the group named **sg-SC300-O365** is shown in the **All groups** list.

   >**Note:** Kindly click the **Refresh** button if you are not able to see the newly created group.
   
     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

     <validation step="6697b154-6e23-4071-b1b5-7bdbf56fc007" />

### Task 3 - Assign a license to a group

1. To assign the license please go to [http://admin.microsoft.com/](url)

2. In the Licenses page, select **Office 365 E3 (no Teams)**.
  
   ![Screen image displaying licenses selected and assigned to a group. The review license menu is also selected displaying multiple selection options.](./media/E1T3S2.png)

3. On License details page, select **Groups** then **+ Assign licenses**.

   ![Screen image displaying licenses selected and assigned to a group. The review license menu is also selected displaying multiple selection options.](./media/E1T3S3.png)
 

4. Enter a group name as **sg-SC300-O365**, select it and then click on **Assign**.

   ![Screen image displaying licenses selected and assigned to a group. The review license menu is also selected displaying multiple selection options.](./media/E1T3S4.png)

### Taks 4 - Confirm the Office 365 license

1. Launch a new InPrivate browser window.
2. Connect to [https://www.office.com](https://www.office.com).
3. Select Sign in and connect as Delia Dennis.

   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | delia.dennis@`your domain name.com`|
   | Password| **Pa55w.rd@123** |

   >**Note:** Enter the username that you had copied in Exercise 1 Task 1 step number 3.

4. You should connect to the Office.com website, and see no messages regarding license. All of the Office applications are available on the left.

   ![Screen image the Office.com website with Delia Dennis logged in with office applications available, because a license is assigned.](./media/licassign.png)
    
5. Close the browser window. 

## Exercise 2 - Create a Microsoft 365 group in Microsoft Entra ID

### Task 1 - Create the group

Part of your duties as an Microsoft Entra administrator is to create different types of groups. You need to create a new Microsoft 365 group for your organization's sales department.

1. From the Azure portal, navigate to **Microsoft Entra ID**

2. In the left navigation, under **Manage**, select **Groups**.

3. In the Groups page, on the menu, select **New group**.

4. Create a group using the following information:

   | **Setting**| **Value**|
   | :--- | :--- |
   | Group type| Microsoft 365|
   | Group name| Northwest Sales|
   | Membership type| Assigned|
   | Owners| *Assign your own administrator account as the group owner*(ODL user account)|
   | Members| **Alex Wilber** and **Bianca Pisani**|

   ![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/msgroup.png)

5. When complete, verify the group named **Northwest sales** is shown in the **All groups** list.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

     <validation step="cd72f203-b756-4b62-84fe-9e9abdcb5ea7" />

## Exercise 3 - Creating a dynamic group with all users as members

### Task 1 - Create the dynamic group

As your company grows, manually group management is too time consuming. Since standardizing the directory, you can now take advantage of dynamic groups. You must create a new dynamic group to ensure you're ready for dynamic group creation in production.

1. In the Microsoft Entra ID page, in the the left navigation pane under **Manage**, select **Groups**, and then select **New group**.

1. On the New Group page, under **Group type**, select **Security**.

1. In the **Group name** box, enter **SC300-myDynamicGroup**.

1. Select the **Membership type** menu and then select **Dynamic User**.

1. Select an **Owner** for the group(ODL user account).

1. Under **Dynamic user members**, select **Add dynamic query**.

1. On the right above the **Rule syntax** box, select **Edit**.

1. In the Edit rule syntax pane, enter the following expression in the **Rule syntax** box:

   ```powershell
   user.objectid -ne null
   ```

   **Warning** - the `user.objectid` is case sensitive.

   ![Screen image displaying the dynamic group membership rules page with rule syntax highlighted](./media/usersyn.png)

1. Click on **Ok**

1. Select **Save**. The new dynamic group will now include B2B guest users as well as member users.

1. On the New group page, select **Create** to create the group.

### Task 2 - Verify the members have been added

**Note** - The population of Dynamic group membership may take up to 15 minutes.

1. Select on the **Home** `Microsoft Entra ID`.

2. Launch **Microsoft Entra ID**.

3. In the **Manage** menu Select on **Groups**.

4. In the filter box type **SC300** and your newly created group will be listed.

5. Select on **SC300-myDynamicGroup** to open the group.

6. Notice that it shows that it contains **Direct members**.

7. Select on **Members** in the **Manage** menu.

8. Review the members.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

     <validation step="4ef44753-8afa-4cd5-afc5-7467551cf169" />

### Task 3 - Experiment with alternate rules (Optional)

1. Try making a group with only **Guest** users:

   - (user.objectid -ne null) and (user.userType -eq "Guest")
     

2. Try make a group with only **Members** of the Microsoft Entra users.

   - (user.objectid -ne null) and (user.userType -eq "Member")

### Review

In this lab you have completed the following tasks:
- Created a security group and add a user
- Created a Microsoft 365 group in Microsoft Entra ID
- Created a dynamic group with all users as members

## You have successfully completed the lab
