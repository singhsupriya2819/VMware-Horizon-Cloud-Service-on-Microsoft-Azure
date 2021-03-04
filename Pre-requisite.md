# Prerequisites

## Precreated Resources

### Resource Groups: There are two precreated resource groups i.e.:
  - **AD-RG**: 
  - **Horizon-Network-RG**:


### Virtual Networks: There are two precreated virtual network i.e:
  - **adVNET**: 
  - **HZN-Vnet**:


### Configuring VNet Peering

We use Microsoft Azure to configure bi-directional peering. One should configure VNet-to-VNet peering only if the following is true:

  - A new VNet that does not have an AD VM inside it
  - Not using Express Route for VNet peering
  - Not using VPN for express route peering


### Configuring the DNS Server

Now that the VNet is configured, next step is to configure the DNS, which is required during the Horizon Cloud Service pod deployment. Horizon Cloud Service uses the default Microsoft Azure-provided DNS for the deployment for outbound DNS resolution, but requires Active Directory to resolve the Active Directory domain controllers. The virtual network must support both internal and external name resolution.


### Creating a Service Principal Client Secret

