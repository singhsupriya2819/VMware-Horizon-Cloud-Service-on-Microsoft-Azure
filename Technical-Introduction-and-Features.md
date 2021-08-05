# Technical Introduction and Features

## **About Horizon Cloud Service on Microsoft Azure**

The VMware Horizon Cloud Service delivers virtual desktops and applications using a cloud platform that is scalable across multiple deployment options. The overall environment consists of the VMware-hosted cloud service, your designated capacity, and the VMware software deployed into that capacity.

The Horizon Cloud Service provides a single cloud control plane from which you can choose multiple deployment options. At any time, you can dynamically switch options to adjust to use cases changes, employee moves, economic shifts, and so on. These options consist of Horizon pods using:
  - **Microsoft Azure capacity -** Public cloud infrastructure from Microsoft Azure, an Infrastructure-as-a-Service (IaaS) provider
  - **On-premises capacity -** Hyper-converged infrastructure from partners such as Dell EMC, Hitachi, and QTC
  - **VMware Cloud on AWS capacity -** Cloud-hosted capacity managed by VMware

The first option, Microsoft Azure, is the focus of this Hands-on Labs. You can connect your Microsoft Azure instance to your Horizon Cloud Service control plane for a comprehensive cloud-hosted solution for delivering virtualized Windows apps and desktops.

Setting up the environment involves deploying the required VMware software into your Microsoft Azure capacity. The deployed VMware software creates an appropriately configured entity called a Horizon Cloud Service pod, which pairs with the control plane. After the pod is deployed, you use the control plane to create RDSH farms and entitle remote desktops and applications to your end users, as well as to assign dedicated and floating Windows Enterprise 10 Multi-session desktops.

For more information, see the [Horizon Cloud Service on Microsoft Azure datasheet](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/images/products/horizon-cloud-virtual-desktops/vmware-horizon-cloud-azure-datsheet.pdf).


## **Packaging, Licensing, and Service Models**

Horizon Cloud Service delivers virtual desktops and apps using a cloud platform that is scalable across multiple deployment options. Horizon Cloud Service is available in two subscription options:

  - **Per named user:** For virtual environments with end users that require dedicated access to virtual machines (VMs) throughout the day
  - **Per concurrent connection:** For virtual environments with a high number of users who share machines throughout the day, such as students or shift workers

You can bring your own hyper-converged infrastructure (HCI) or Microsoft Azure infrastructure, or purchase cloud-hosted infrastructure from VMware. For more information, see [How to Buy](https://www.vmware.com/products/horizon-cloud-virtual-desktops.html#how-to-buy) and [Horizon Universal License](https://www.vmware.com/products/horizon.html).


## **Features and Benefits**

With the Horizon Cloud Service on Microsoft Azure offering, [Microsoft and VMware](https://www.vmware.com/partners/strategic-technology-partners/microsoft.html) work together to extend the desktop-as-a-service (DaaS) offering with new cross-cloud capabilities. Key features of Horizon Cloud Service on Microsoft Azure include:

  - **Support for VDI desktops:** For desktops that use the Microsoft Windows 10 operating system, you can entitle both VDI dedicated desktops and VDI floating desktops to your end users.
  - **Easy deployment:** Depending on the complexity of your configuration, it can take as little as 60 minutes to deploy the service to your own Microsoft Azure instance.
  - **Single management plane:** Even if you deploy multiple instances of Horizon Cloud Service to multiple Microsoft Azure regions, you still use the same cloud-based management UI to configure and manage your Horizon Cloud Service environments.
  - **Single infrastructure provider:** You can manage virtual applications from the cloud with your existing infrastructure provider.
  - **Simple upgrades:** VMware provides a simple blue-green upgrade method that allows you to rev to the next release in minutes.
  - **Power management:** Horizon Cloud Service has built-in features that automatically allocate and deallocate RD Session Hosts based on demand, which cuts costs because you pay for use only, not for idle time.
  - **Schedule-based power management options for VDI dedicated and floating desktops:** You can schedule powering off an assignment's VDI desktops for weekends, holidays, and non-working hours, which can optimize cost savings. You can also schedule a higher minimum desktop count to meet high-demand times. 
  - **Rolling maintenance and image update:** Horizon Cloud Service includes built-in orchestration to allow you to do rolling maintenance of your RD Session Hosts.
  - **RD Session Hosted applications:** Horizon Cloud Service supports RD Session Hosted applications and desktops with this initial release.
  - **Cloud monitoring:** You do not need a third party or additional tool to monitor or manage your Horizon Cloud Service on Microsoft Azure deployment. Our new cloud-based monitoring feature allows you to keep an eye on your deployment from a single UI.
  - **True multi-cloud deployments:** You can choose between cloud capacity managed by VMware, bring your own hyper-converged infrastructure, or bring your own public cloud capacity from Microsoft Azure.
  - **Dynamic Environment Manager (formerly known as User Environment Manager):** With this solution, you get personalization and dynamic policy configuration across any virtual, physical, and cloud-based Windows desktop environment, engineered to deliver workplace productivity while driving down the cost of day-to-day desktop support and operations.
  - **Workspace ONE:** This solution integrates with VMware Workspace ONE to provide your users with a single workspace to access all their applications.
  - **Leverage Microsoft Azure services and regions:** You can host virtual desktops and apps across more data centers and more locations by integrating with Azure, one of the fastest-growing IaaS providers with one of the largest number of global regions.
  - **Expanded geographic reach:** You can leverage any region from the many global Microsoft Azure data centers, and configure and deploy desktops in minutes.
  - **Low-cost hourly billing:** You benefit from consumption-based pricing for capacity, as well as no upfront costs or termination fees.


For more information, see [VMware Horizon Cloud Service](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/index.html) and under **VMware Horizon Cloud Service Release Notes**.


Click on the **Next** button from lower right corner of the guide to move on the next page.