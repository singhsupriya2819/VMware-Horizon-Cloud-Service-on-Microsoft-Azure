# prerequisite

## About Setup


The prerequisite exercises help you prepare your environment for best use of Horizon Cloud Service on Microsoft Azure. The exercises are sequential and build upon one another, so make sure to complete each exercise in this section before going to the next.

In this section, you first verify that your environment meets the basic prerequisites. Next, you create a new virtual network (VNet), one of the prerequisite Microsoft Azure components.

You must provide your own Microsoft Azure IaaS capacity, and configure the Microsoft Azure prerequisites for the Horizon Cloud Service deployment. You then set up network ranges based on previously provided CIDR blocks, select Active Directory options, complete VNet bi-directional peering, DNS configuration, and so on. Subsequent sections describe how to deploy the Horizon Cloud Service pod on Microsoft Azure, and finally how to create a farm where your end users can access applications and shared desktops, and assign dedicated and floating desktops.

**Note:** You must verify that the subscription has the required capacity as listed in the [VMware Horizon Cloud Service on Microsoft Azure Requirements Checklist](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.getstarted15/GUID-5F69086E-E061-48F3-93D9-9705B8B5FD8A.html#GUID-5F69086E-E061-48F3-93D9-9705B8B5FD8A__SECTION_32A00526-5BD0-4233-B772-58B4B2C4EA29).


# Prerequisite 1: Reviewing the Workflow

Before you start, it is best practice to review the workflow and tasks involved. You can use the navigation tool on the left to jump to each section as outlined below:

1. Verify that your environment meets the prerequisites listed in [VMware Horizon Cloud Service on Microsoft Azure Requirements Checklist](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.getstarted15/GUID-5F69086E-E061-48F3-93D9-9705B8B5FD8A.html).

2. See **Deploying a Horizon Cloud Service Pod**
  - Prepare the Microsoft Azure for pod deployment.
  - Deploy the pod.

3. See **Creating an Image**
  - Register Active Directory domain.
  - Configure a golden image.
  - Install applications in the golden image.
  - Convert the golden image into an assignable image.

4. See **Deploying a Farm**
  - Create an RDSH farm to provide session desktops to assign to users.
  - Create another RDSH farm to provide remote desktops to assign to users.
  - Create a CNAME record in your DNS server.

5. See **Assigning VDI Desktops**
  - Assign a dedicated desktop.
  - Assign a floating desktop.

6. See **Explore Horizon Cloud Service Monitoring and Analytics**
  - Explore the reports and analytics functionality.

7. See **Explore VMware Dynamic Environment Manager**
  - Explore the integration with Dynamic Environment Manager and capabilities.

After you finish reviewing the workflow, verify that your environment meets all prerequisites, and then proceed to the next exercise to configure the VNet.


## Prerequisite 2: Creating the VNet

You can deploy a Horizon Cloud Service pod to an existing virtual network (VNet), or create a new VNet. But before you create a VNet, verify that your environment meets the prerequisites listed in [VMware Horizon Cloud Service on Microsoft Azure Requirements Checklist](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.getstarted15/GUID-5F69086E-E061-48F3-93D9-9705B8B5FD8A.html). For more information, see [Getting Started with VMware Horizon Cloud Service on Microsoft Azure](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.admin15/GUID-A4FA2F8E-6AF5-4F4A-9437-01107591337F.html).

This exercise describes how to create a new VNet where Active Directory services are available. Microsoft Azure automatically creates the necessary subnets in the VNet using CIDR blocks that you provide. Horizon Cloud Service automates machine creation and domain join operations, and requires access to a VNet with AD services. A set of resource groups in your Microsoft Azure capacity is also automatically created. Resource groups organize the assets that the environment needs, such as virtual subnets and VMs for the Unified Access Gateway, RDS-enabled server images, RDSH farms, and so on.

### Task 1: Log in to Microsoft Azure

   ![ws name.](media/pr1.png)
   
1. Log in to your existing Microsoft Azure deployment.

2. Make sure to use a subscription that provides IaaS capacity.


### Task 2: Add a New Virtual Network

   ![ws name.](media/pr2.png)
   
1. In the navigation bar on the left, select **Virtual Networks**.

2. Click **Add** to create a VNet.


### Task 3: Provide Data for New VNet

   ![ws name.](media/pr3.png)
   
1. In the Create Virtual Network pane, provide the following information:
  - **Name:** Enter a name to distinguish this VNet from others.
  - **Address space:** Accept the default, or enter an address range.
  - **Subscription:** Select from the drop-down menu.
  - **Resource group:** Select an existing resource group, or create a new one when the virtual network is created.
  - **The value should not be empty:** Create a new resource group or use an existing one.
  - **Location:** From the drop-down menu, select the region where you plan to deploy the Horizon Cloud Service pod.
  - **Subnet Name:** Accept the default. Horizon Cloud Service automates the creation of the necessary subnets using the CIDR blocks previously provided.
  - **Address range:** Accept the default.
  - **Service endpoints:** Accept the default.

2. In the lower right corner, click **Create**.

3. Wait until the creation process is complete, and the VNet is created.

### Task 4: Creating the VNET

   ![ws name.](media/pr4.png)
   
After creating the VNET, you must update it to add a Service Endpoint. To do this:

1. Navigate to the VNET you created, and in the left pane under Settings, click **Service Endpoints**.

2. Click **Add**.

3. From the pane on the right, select **Microsoft.Sql** to add it.

### Task 5: Add a service endpoint

   ![ws name.](media/pr5.png)
   
1. Under **Settings**, select **Service endpoints**.

2. In the middle pane, click **Add**.

3. In the **Add a service endpoints** pane on the right, under **Service**, select **Microsoft.Sql**.

**Note:** The SQL component is required for regular backups of the pod configuration, and the HA feature too.

For more information, see VMware Horizon Cloud Service Deployment Guide, in the search field select **Book**, and search the guide for **Configure the Required Virtual Network in Microsoft Azure**.

After creating the VNET, proceed to the next section to configure bi-directional VNET peering.


## Prerequisite 3: Configuring VNet Peering (Optional)

In this exercise, you use Microsoft Azure to configure bi-directional peering. You should configure VNet-to-VNet peering only if the following is true:

  - You created a new VNet that does not have an AD VM inside it
  - You are not using Express Route for VNet peering
  - You are not using VPN for express route peering

In this tutorial, it is assumed that another VNet is in the same region as the AD/DNS server, to which you are peering for access to those services.


### Task 1: Peering Connects the Horizon Cloud Service VNet on Microsoft Active Directory

   ![ws name.](media/pr6.png)
   
1. Select the Virtual Networks pane and select a network.

2. Click **Peering**.

3. On the right-most pane, verify that the peer is not yet connected.


### Task 2: Add Peering Details

   ![ws name.](media/pr7.png)
   
1. In the **Add peering** pane under **Peer details**, provide the required information:
  - **Name:** Enter a name to distinguish this action from others.
  - **Virtual network deployment model:** Select the **Resource manager** option.
  - **Subscription:** Select your subscription.
  - **Virtual network:** Click **Choose a virtual network**, and select your VNet.

2. Under **Configuration**, provide the following required information: enabled
  - **Allow virtual network access:** Enabled.
  - **Configure forwarded traffic settings:** Enabled.
  - **Configure gateway transit settings:** Check to allow gateway transit.

3. Click **OK**.


### Task 3: VNet Peering Is Connected

   ![ws name.](media/pr8.png)
   
1. Return to the third pane if you are not already there.

2. Verify that VNet peering is now connected.


### Task 4: VNet Peering Overview Details

   ![ws name.](media/pr9.png)
   
1. In the second pane, click **Overview**.

2. Review the additional details now displayed in the third pane.

For more information, see the [Getting Started with VMware Horizon Cloud Service on Microsoft Azure](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.getstarted15/GUID-6E460805-C323-4200-9A45-45E7BFB31730.html) guide.

After you finish configuring the VNet, proceed to the next exercise to configure the DNS server.


## Prerequisite 4: Configuring the DNS Server

Now that the VNet is configured, your next step is to configure the DNS, which is required during the Horizon Cloud Service pod deployment. Horizon Cloud Service uses the default Microsoft Azure-provided DNS for the deployment for outbound DNS resolution, but requires Active Directory to resolve the Active Directory domain controllers. You must set the virtual network to support both internal and external name resolution.


### Task 1: Microsoft Azure DNS Supports Name Resolution

   ![ws name.](media/pr10.png)
   
1. In the navigation bar on the left, click **Virtual networks**.

2. Select the virtual network you want to use for your pod.

3. Click **DNS servers** to display the DNS server settings.


### Task 2: Configure DNS Before Deploying the Horizon Cloud Service Pod

   ![ws name.](media/pr11.png)
   
1. In the upper right, select the **Custom** option.

2. Add the address of the DNS server to use for name resolution.

For more information, see [Getting Started with VMware Horizon Cloud Service on Microsoft Azure](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/hzncloudmsazure.getstarted15/GUID-6E460805-C323-4200-9A45-45E7BFB31730.html).

After you finish configuring the DNS server, proceed to the next exercise to create a client secret for the service principal.


## Prerequisite 5: Creating a Service Principal Client Secret

