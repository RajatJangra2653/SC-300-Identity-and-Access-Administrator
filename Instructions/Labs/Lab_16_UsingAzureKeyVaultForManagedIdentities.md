# Lab 16 - Using Azure Key Vault for Managed Identities

## Lab scenario

When you use managed identities for Azure resources, your code can get access tokens to authenticate to resources that support Microsoft Entra authentication.  However, not all Azure services support Microsoft Entra authentication. To use managed identities for Azure resources with those services, store the service credentials in Azure Key Vault, and use the managed identity to access Key Vault to retrieve the credentials.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1 - Create a Windows Virtual Machine
- Task 2 - Create a Key Vault
- Task 3 - Create a secret
- Task 4 - Grant access to Key Vault
- Task 5 - Access data with Key Vault secret with PowerShell

## Estimated time: 20 minutes

## Architecture Diagram

   ![](./media/arch16.png)

## Exercise 1 - Use Azure Key Vault to manage Virtual Machine identities

Use Azure Key Vault to securely manage and rotate secrets, keys, and certificates for Virtual Machine identities in Azure, enhancing security and access control.

### Task 1 - Create a Windows Virtual Machine

In this task, you will create a Windows 11 VM from the Azure Marketplace, configure essential settings like name and credentials, and enable managed identity before deploying the VM.

1. Select **+ Create a resource**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/lab16-1.png)

1. Type **Windows 11** in Search the Marketplace search bar.

1. Select **Windows 11** and click on the dropdown next to **Create**.

   ![](./media/sc-300-lab16-7.png)

1. From the dropdown, choose **Windows 11 Enterprise, version 22H2**. You will be redirected to **Create a virtual machine** tab.

   ![](./media/new-lab16-1.png)

1. In the **Create a Virtual Machine** page, modify the following by keeping the rest as default:

   - Resource Group: Select the existing resource group from the dropdown (1)
   - Virtual Machine Name: **VM-<inject key="DeploymentID" enableCopy="false"/> (2)**
   - Size: **See all sizes > B2s > Standard B2s (3)**
   - Username: **azureuser (4)**
   - Password: **Password@..!!(5)**
   - Confirm Password: **Password@..!! (6)**
   - Ensure the checkbox towards the end is checked which states that you have an eligible Windows 10/11 License.

        ![](./media/new-lab16-2.png)

        ![](./media/sc-300-lab16-2.png)

        ![](./media/sc-300-lab16-3.png)
   
1. You will have to create an administrator username and password for the VM on the basics tab.

1. On the **Management (1)** tab, check the box to **Enable system assigned managed identity (2)** and click on **Review + Create**.

   ![](./media/sc-300-lab16-4.png)

1. Select **Create**.

     >**Note**: Please wait till the deployment is successful.
   
     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

     <validation step="1935e96f-183f-447c-9218-a42a2312f43b" />

### Task 2 - Create a Key Vault

In this task, you will create an Azure Key Vault by configuring the required settings, including the name and access policy, then deploy it and retrieve the Key Vault URL for future tasks.

1. Select **+ Create a resource**.

    ![](./media/lab16-1.png)

1. In **Search services and marketplace**, type and search for **Key Vault**.

    ![](./media/lab16-4.png)

1. Select **Create > Key vault**.

    ![](./media/lab16-5.png)

1. Fill out all required information as shown below. Select **Next**.

    | Settings | Values |
    | -------- | ------ |
    | Resource group | **sc-300-rg-<inject key="DeploymentID" enableCopy="false"/>** |
    | Key vault name | **keyvault-<inject key="DeploymentID" enableCopy="false"/>** |
    | Region | **<inject key="Region" enableCopy="false"/>** |
    | Access Configuration | select the **Vault Access Policy** radio button. |

      ![](./media/sc-300-lab16-5.png)
   
1. Select **Review + create**.

1. Select **Create**.

1. Once deployment is completed click on **Go to resource**.

1. On **keyvault-<inject key="DeploymentID" enableCopy="false"/>** page copy the url and paste that URL in notepad you need this value in further tasks.

   ![](./media/lab16-6.png)
         
     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

     <validation step="242ccb00-a152-49ee-8d59-42c22a8c1860" />

### Task 3 - Create a secret

In this task, you will create a secret in your Key Vault by specifying the name and value, then copy the secret name for use in future tasks.

1. Navigate to your newly created Key Vault.

1. From the left-hand navigation pane, under **Objects**, select **Secrets (1)** and click on **+ Generate/Import (2)**.

   ![](./media/lab16-7.png)
   
1. On the Create a secret page, follow the instruction:-

    | Settings | Values |
    | -------- | ------ |
    | Upload | **Manual** |
    | Name | **secret-<inject key="DeploymentID" enableCopy="false"/>** |
    | Secret value | **123456789** |
    | Enabled | **Yes** |

1. Select **Create** to create the secret.

1. Copy the secret name **secret-<inject key="DeploymentID" enableCopy="false"/>** , and paste it in the notepad you need this value in further tasks.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

     <validation step="b3569c98-64c4-4f7e-a19b-463cfc0b4d36" />

### Task 4 - Grant access to Key Vault

In this task, you will grant access to your Key Vault by creating an access policy, assigning secret management permissions, and selecting the appropriate VM as the principal.

1. On the **keyvault-<inject key="DeploymentID" enableCopy="false"/> | Secrets**, from the left-hand navigation pane, select **Access policies** and click on **+ Create**.
   
   ![](./media/lab16-8.png)

1. On the **Create an access policy**, under Configure from template, choose **Secret Management (1)** from the drop-down. Select **Next (2)**.
   
   ![](./media/lab16-(9).png)
   
1. On the **Principal** page, in the search field enter the name **VM-<inject key="DeploymentID" enableCopy="false"/> (1)**, and select it. Select **Next (2)**.

   ![](./media/lab16-10.png)
   
1. On the **Application (optional) page**, select **Next**.

1. On the **Review + Create** page, select **Create**.

### Task 5 - Access data with Key Vault secret with PowerShell

In this task, you will use PowerShell within your virtual machine to access the secret stored in Azure Key Vault by obtaining an access token and invoking a web request to retrieve the secret.

1. In **Search, resources, services and docs** search and select **Virtual machines**.

1. Select the virtual machine that you created in Task-1, that is **VM-<inject key="DeploymentID" enableCopy="false"/>**.

1. Select **Connect**, under the **Connect** tab, choose **Select**, and select **Download RDP file**.
   
    ![](./media/lab16-11.png)

1. Open the downloaded file, select **Connect**, and enter the VM credentials, that is username which is **azureuser**, and password which is **Password@..!!**, select **OK**. Select **Yes** on the certificate pop-up.
   
1. In the virtual machine, from the **Start menu** search and select **Windows PowerShell**.  

   ![](./media/sc-300-lab16-6.png)
   
1. In PowerShell, run the following command to invoke the web request on the tenant to get the token for the local host in the specific port for the VM.  

    ```
    $Response = Invoke-RestMethod -Uri 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fvault.azure.net' -Method GET -Headers @{Metadata="true"}
    ```

1. Next, run the following command to extract the access token from the response.  

    ```
    $KeyVaultToken = $Response.access_token
    ```

1. Use PowerShell’s Invoke-WebRequest command to retrieve the secret you created earlier in the Key Vault, passing the access token in the Authorization header.
   
   >**Note:** Replace **your-key-vault-URI** to the Key Vault URI that you copied in Task-2, and replace **secret-name** with the secret name that you copied in Task-3.

    ```
    Invoke-RestMethod -Uri <your-key-vault-URI>secrets/<secret-name>?api-version=2016-10-01 -Method GET -Headers @{Authorization="Bearer $KeyVaultToken"}
    ```

    >**Important-note:** It will look similar to this:- **Invoke-RestMethod -Uri https://keyvault-1131297.vault.azure.net//secrets/secret-1131297?api-version=2016-10-01 -Method GET -Headers @{Authorization="Bearer $KeyVaultToken"}**

1. You should receive a response that looks like the following: 
    
    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/results.png)

1. This secret can be used to authenticate services that require a name and password.

### Review
In this lab, you have completed:
- Created a Windows Virtual Machine
- Created a Key Vault
- Created a secret
- Granted access to Key Vault
- Accessed data with Key Vault secret with PowerShell

### You have successfully completed the lab
