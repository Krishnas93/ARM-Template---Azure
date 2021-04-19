# ARMTemplates

# USING ARM TEMPLATE CREATING AKS , ACR AND STORAGEACCOUNT

### Step 1: Pre-Requistes

> Have an Azure account in azure cloud 
  you can follow the below link for creating a azure free subscription account
  https://azure.microsoft.com/en-in/free/

> Have installed Azure CLI in local system for connecting it to the central cloud 
  https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli
  
  Follow the above documentation for connecting to Azure CLI from local system



### Step 2: Create a ARM template files 

Create an ARM templates using VScode IDE or else use Azure Quickstart template files 

> Create an ARM template for the resource what you want 
> Here I have uploaded the Template files for AKS , ACR and Storage Account
> AKS template files 
  * templateaks.json
  * templateaks.parameters.json
> ACR template files
  * templateACR1.json
> Storage Account files
  *  templateStrAcc.parameters.json
  *  templateStrAcc.json
  
 # the above template files we can deploy in azure cloud In the ARM json files , have mentioned the resource group and about the particular resource configuration 
 
### Step 3: Login to AZURE CLI from our local system using the below commands 

````
az login 
````
If the azure cloud is not provided with Multi-Factor Authentication(MFA) it can login easily through the above command
But if Azure cloud account is associated with MFA, follow the below command

````
az login --tenant TENANT_ID

````
Tenant_ID will be present in Tenant properties in our Azure Cloud 

![image](https://user-images.githubusercontent.com/78354123/115270023-87f3df80-a159-11eb-97e0-e2885306a930.png)



### Step 4: Run the template files using the below command 
The below command for running the template of AKS Cluster and similar way we can deploy the json files for storage account

````
az deployment group create --resource-group <ResourceGroupName> --template-file templateaks.json --parameters templateaks.parameters.json
````
Give the above command in azure cloud CLI Bash or from our local system cmd using the azlogin command by connecting with the cloud cli

Once u deploy those two json files of AKS the specific resource will be created

![image](https://user-images.githubusercontent.com/78354123/115270983-7f4fd900-a15a-11eb-9e67-9ce38b33fc96.png)

In the above image you can see that cluster what we created through ARM template 


### Step 5 : Alternate way of uploading a ARM file in Azure cloud

> Search for Deploy a Custom Tempate 

Click it and click on the build your own template deploy 

![image](https://user-images.githubusercontent.com/78354123/115271651-2cc2ec80-a15b-11eb-9040-ce0d24873ed1.png)

In that upload file u can upload the json file of templateACR1.json which we created for ACR

Click on that save 

Select the paramters as below image and always give a unique ACR name and select your own resourcegroup and select that 

![image](https://user-images.githubusercontent.com/78354123/115272060-9a6f1880-a15b-11eb-8d29-5ea1a9cf7af7.png)

Then click Review + create and once validation of that file is done 

Click create 

Then the ACR resource wil be created 

### Step 6 : Resource Creation of AKS through Azure powershell

We can create AKS cluster through azure powershell by below commands  

Open Azure cloud CLI and select powershell in that ![image](https://user-images.githubusercontent.com/78354123/115272816-73651680-a15c-11eb-8059-60c672280239.png)


> Create a resource group  ( mention RG and location accordingly to your requirements )
````
New-AzResourceGroup -Name myResourceGroup -Location eastus
````
In the Powershell terminal once created you can see this :

````
ResourceGroupName : myResourceGroup
Location          : eastus
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup
````

Next command for aKs cluster creation ( give a unique cluster name )

````
New-AzAksCluster -ResourceGroupName myResourceGroup -Name myAKSCluster -NodeCount 1

````

or ( connect local system powershell to azure cloud )

````
Import-Module Az
````
connect to your azure cloud 
````
Connect-AzAccount 
````
Then once connected you can follow the above commands on creating the particular resources .

# REFERENCE DOCS 
https://docs.microsoft.com/en-in/azure/azure-resource-manager/templates/deploy-powershell
https://docs.microsoft.com/en-in/azure/azure-resource-manager/templates/quickstart-create-templates-use-visual-studio-code?tabs=CLI
https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough-powershell
https://docs.microsoft.com/en-us/azure/container-registry/container-registry-get-started-geo-replication-template
https://docs.microsoft.com/en-us/azure/container-registry/container-registry-get-started-powershell



````
