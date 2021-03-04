# VMware Horizon Cloud Service on Microsoft Azure 2.0

## Introduction

**Note:** This Quick-Start Tutorial was updated with content relevant for the March 2020 release of Horizon Cloud on Microsoft Azure. For more details about this release, see [Horizon Cloud on Microsoft Azure Support for Windows Virtual Desktop is Here](https://blogs.vmware.com/euc/2020/03/windows-virtual-desktop-support.html) and [VMware Horizon Cloud Service Release Notes - v3 - March 2020](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/rn/horizon-cloud-service-relnotes-30.html).

This Quick-Start Tutorial introduces you to VMware Horizon® Cloud Service™ on Microsoft Azure. This solution combines the management functionality of the Horizon Cloud Service control plane with the cost-saving capacities of Microsoft Azure. You can take advantage of the Horizon Cloud Service to manage your desktops and remote applications. This includes managing VDI and RDS-hosted applications on Microsoft Azure infrastructure, as well as the flexibility to choose the deployment option that best meets the needs of your organization or use cases.

This Quick-Start Tutorial is relevant for VMware Horizon Cloud Services on Microsoft Azure 2.0, and describes the process of deploying Horizon Cloud Service components into your Microsoft Azure capacity. This process creates an entity called the Horizon Cloud Service pod (previously referred to as a node), which pairs with the control plane. You then use the control plane to create RDSH and session farms, and to manage and deliver virtual RDS-enabled Windows Servers and remote applications to your end users. You can also leverage the automation to perform basic VDI agent updates to floating and dedicated desktops.


## Purpose

This Quick-Start Tutorial introduces you to Horizon Cloud Service on Microsoft Azure, and helps you to evaluate this product through a series of practical exercises. The Overview section describes the benefits, features, architecture, and components, and component interoperability. The subsequent sections provide exercises to help you deploy the Horizon Cloud Service pod into your Microsoft Azure capacity, and then to explore and evaluate this product and its core capabilities and key features.

**Important:** This Tutorial is for evaluation purposes, based on minimum required resources for a basic deployment, and does not explore all possible features. The resulting environment should not be used as a template for deploying a production environment. To deploy a production environment, see the [Horizon Cloud Service documentation](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/index.html).


## Audience

This guide is intended for security architects, engineers, and administrators who want to familiarize themselves with, or are in the process of implementing, a Horizon Cloud Service on Microsoft Azure infrastructure.

It is assumed that you have familiarity with Windows data center technologies such as Microsoft Azure and Active Directory, and knowledge of VMware Horizon 7 and VMware Unified Access Gateway. You should also be familiar with virtualization technology, cloud computing, network routing, and firewall security architecture. Knowledge of compatibility is also useful when using VMware Horizon Cloud Service on Microsoft Azure (see [VMware Product Interoperability Matrices](https://interopmatrix.vmware.com/#/Interoperability)).

Note: Not all sections of this guide are necessarily applicable to your particular deployment. Optional sections are marked as such. If you have questions about the specifics of your order, see [Getting Started with Horizon Cloud](https://www.vmware.com/products/horizon-cloud-virtual-desktops/getting-started.html), or reach out to your VMware sales representative.
