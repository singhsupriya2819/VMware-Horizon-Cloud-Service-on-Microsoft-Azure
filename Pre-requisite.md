# Prerequisites


This lab requires few prerequisites to be met to sucessfully complete the lab. We have preconfigured all the prerequisites for you, there is no action needed from your end.

Following are the resources that are precreated.

### **Resource Groups**

There are two precreated resource groups i.e.:

  - **AD-RG**: Resource agroup to create adVnet virtual network.
  - **Horizon-Network-RG**: Resource group to create HZN-Vnet virtual network.


### **Virtual Networks**

There are two precreated virtual network i.e:

  - **adVNET**: Virtual network to deploy adVM.
  - **HZN-Vnet**: Virtual network for horizon resources.


### **VNet Peering**

We use Microsoft Azure to configure bi-directional peering. One should configure VNet-to-VNet peering only if the following is true:

  - A new VNet that does not have an AD VM inside it
  - Not using Express Route for VNet peering
  - Not using VPN for express route peering


### **DNS Server**

We have preconfigured the DNS Server, which is required during the Horizon Cloud Service pod deployment. Horizon Cloud Service uses the default Microsoft Azure-provided DNS for the deployment for outbound DNS resolution, but requires Active Directory to resolve the Active Directory domain controllers. The virtual network will support both internal and external name resolution.


### **Service Principal with Contributor Role**

Horizon Cloud Service needs a service principal to access and use your Microsoft Azure subscription capacity. A service principal defines the policy and permissions for use of an application in a specific tenant, and is used to grant Horizon Cloud Service permission to access and modify your Microsoft Azure tenant. We have precreated a Service Principal in the lab tenent with Contributor role.

### **Resource Providers**

VMware Horizon Cloud Service require below Resource Providers to be registered in the Azure subscription which is preregistered while provisioning the environment.

  - Microsoft.Compute
  - Microsoft.Insights
  - Microsoft.Network
  - Microsoft.Storage
  - Microsoft.KeyVault
  - Microsoft.Authorization
  - Microsoft.Resources
  - Microsoft.ResourceHealth
  - Microsoft.DBforPostgreSQL
  - Microsoft.Sql


Click on the **Next** button from lower right corner of the guide to move on the next page.

