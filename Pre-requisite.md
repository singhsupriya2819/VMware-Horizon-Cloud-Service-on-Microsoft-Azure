# Prerequisites

The following lab requires few precreated resources which we have automated.

Following are the resources that are precreated.

### **Resource Groups**

There are two precreated resource groups i.e.:

  - **AD-RG**: Resource agroup to create adVnet virtual network.
  - **Horizon-Network-RG**: Resource group to create HZN-Vnet virtual network.


### **Virtual Networks**

There are two precreated virtual network i.e:

  - **adVNET**: Virtual network to deploy adVM.
  - **HZN-Vnet**: Virtual network for horizon resources.


### **Configuring VNet Peering**

We use Microsoft Azure to configure bi-directional peering. One should configure VNet-to-VNet peering only if the following is true:

  - A new VNet that does not have an AD VM inside it
  - Not using Express Route for VNet peering
  - Not using VPN for express route peering


### **Configuring the DNS Server**

Now that the VNet is configured, next step is to configure the DNS, which is required during the Horizon Cloud Service pod deployment. Horizon Cloud Service uses the default Microsoft Azure-provided DNS for the deployment for outbound DNS resolution, but requires Active Directory to resolve the Active Directory domain controllers. The virtual network must support both internal and external name resolution.


### **Service Principal with Contributor Role**

Horizon Cloud Service needs a service principal to access and use your Microsoft Azure subscription capacity. A service principal defines the policy and permissions for use of an application in a specific tenant, and is used to grant Horizon Cloud Service permission to access and modify your Microsoft Azure tenant. When you register a Microsoft Azure AD application, the service principal is also created. For more information, see [Create the Required Service Principal by Creating an Application Registration](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.getstarted15/GUID-DC011997-CE9E-4B38-9C4F-57104226218C.html).


### **Resource Providers**

We have automated the registration of resource providers that the pod requires i.e.:

  - Microsoft.Compute
  - microsoft.insights
  - Microsoft.Network
  - Microsoft.Storage
  - Microsoft.KeyVault
  - Microsoft.Authorization
  - Microsoft.Resources
  - Microsoft.ResourceHealth
  - Microsoft.DBforPostgreSQL
  - Microsoft.Sql


Click on the **Next** button from lower right corner of the guide to move on the next page.

