# Azure DevTest Lab Provisonning

### Quick start instructions

###### 1 - Installation Azure PowerShell using th link http://aka.ms/webpi-azps
###### 2 - Place all the files under the same folder. e.g. 'C:\PSScripts\'
###### 3 - Run Windows PowerShell as Administrator
###### 4 - In the Windows PowerShell console, go to the folder that stores all these files by running

	cd "<your folder path>"

   e.g.:

	PS C:\WINDOWS\system32>cd "C:\PSScripts"

###### 5 - Changes all necessary variables into 'azuredeploy.parameter.json' before execute script :

* **newLabName** : The name of the new lab instance to be created.
* **artifactRepoUri** : Set 'artifact repository' : the Git clone URI.
* **artifactRepoFolder** : Set 'artifact repository' : the target folder in the repo.
* **artifactRepoBranch** : Set 'artifact repository' : the target branch in the repo.
* **artifactRepoDisplayName** : Set 'artifact repository' : the display name of the repo.
* **artifactRepoSecurityToken** : Set 'artifact repository' : the personal access token of the repo. 

**TIPS** : On GitHub, you can generate a new one  > Avatar > Settings > Developer settings > Personal access token  
	
###### 6 - Then run the following commands:

	.\ProvisionSogetrelDevTestLab.ps1 -SubscriptionId "<Azure subscription ID where the lab will be created>" -ResourceGroupName "<name for the new resource group where the lab will be created>" -ResourceGroupLocation "<location for the resource group to be created. e.g. West US>"

   e.g.

	PS C:\PSScripts>.\ProvisionSogetrelDevTestLab.ps1 -SubscriptionId "6f2c9094-f241-4528-800d-bfde589f02cd" -ResourceGroupName "SOG-RG-WestEurope-DevTestLab" -ResourceGroupLocation "West Europe"

**TIPS** : To know your SubscriptionId launch the following command into PS cmd : Login-AzureRmAccount. You will see your SubscriptionId :)
	
===============================================================================

About the resources created in the Demo Lab:
The ARM template creates a demo lab with the following things:
* It sets up all the policies and a private artifact repo.
* It creates 3 custom VM images/templates.
* It creates 4 VMs, and 3 of them are created with the new custom VM images/templates.

To customize the lab/VM/template properties (e.g. the lab name), change the parameter values in the azuredeploy.parameters.json file. 