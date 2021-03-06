# Azure Stack Cloud Burst 
Learn how to create a cross-cloud solution to provide a manually triggered process for switching from an Azure Stack hosted web app, to an Azure hosted web app with auto-scaling via traffic manager, ensuring flexible and scalable cloud utility when under load.

For most businesses it may not be economically feasible to maintain the capacity required in their on-premises environment to handle spikes in demand for the app. The tenant can take use the elasticity of the public cloud with their on-premises solution.

![Cloud Burst Architecture](/img/cloudburst_architecture_1.jpg)

##  Considerations
### Scalability considerations
The key component of cross-cloud Scaling (or cloud burst) is the ability to deliver immediate, on-demand scaling between public and on-premises cloud infrastructure, proving consistent, reliable service as prescribed by the demand.
### Availability considerations
Ensure locally deployed apps are configured for high-availability through on-premises hardware configuration and software deployment.
### Manageability considerations. 
The cloud burst solution ensures seamless management and familiar interface between environments. PowerShell is recommended for cross-platform management.

# Prerequisites
There are some distinctions between single-node Azure Stack Development Kit (ASDK), and multi-node Azure Stack Integrated System:
 * ASDK utilizes a public IP address, while maintaining its own VM with a separate and defined private network.
 * Azure Stack Integrated System integrates with your datacenter and has an entire IP address range to delegate to the system during installation. This requires some specialized setup and configuration for the Azure stack isolated environment.
 
**Azure Stack**
  - Firewall and or router appliance needs to know how to route traffic to and from Azure Stack environment
  - An Azure Stack Environment.
    For information on how to deploy Azure Stack Development Kit see [ASDK-Install](https://docs.microsoft.com/azure/azure-stack/asdk/asdk-install)

  - Azure Stack environment has SQL and App Service RP deployed and configured.
      - [Deploy the Azure Stack SQL RP](https://docs.microsoft.com/azure/azure-stack/azure-stack-sql-resource-provider-deploy)
      - [Deploy the Azure Stack App Service RP](https://docs.microsoft.com/azure/azure-stack/azure-stack-app-service-deploy)

  - SQL Server 2016 image added to your Azure Stack Marketplace.
    For information on how to add Marketplace images from Azure Marketplace see [Adding-Images](https://docs.microsoft.com/azure/azure-stack/asdk/asdk-register)

  - Plans, Offers and Quotas Configured
    For information on how to configure Quotas, Offers and Plans see [Plan-Offer-Quota-Overview](https://docs.microsoft.com/azure/azure-stack/azure-stack-plan-offer-quota-overview)

  - A tenant subscribed to your Azure Stack Offer/Plan.
    For information on how to Subscribe to an offer see. [Subscribe-to-an-Offer](https://docs.microsoft.com/azure/azure-stack/azure-stack-subscribe-plan-provision-vm)
    
**Azure**
  - Azure Subscription
  > If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.

  - The Azure user needs to have a GitHub Account linked to email
  - The Azure user needs to have access to the GitHub Repository
    For information on how to add Collaborators see [Adding-Collaborators](https://help.github.com/articles/inviting-collaborators-to-a-personal-repository/)
  - You must approve a connection from Azure to GitHub before you begin the deployment. This can be accomplished by manually creating a
    WebApp from the Azure portal, clicking on the Deployments options and setting up the access to the GitHub repository.
    
##  Before you begin
Verify that you have met the following criteria before beginning your configuration:
  - Verify that you have an externally facing public IPv4 address for your VPN device. This IP address cannot run through network address translation (NAT).
  - Ensure all resources are deployed in the same region/location.

For more information about VPN Gateway settings in general, see [About VPN Gateway Settings](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings).

# Reference Architecture
This section details the reference architecture that can be used as a guidance to implement the offer.

## High Level Overview
![Cloud Burst Architecture](/img/cloudburst_architecture_1.jpg)

This architecture consists of the following components:
### Azure Resources
 * Azure App Service
 * Azure Virtual Network
   * Application Subnet
   * Gateway Subnet
 * Azure Local Network Gateway
 * Azure Virtual Network Gateway 
 * Azure Public IP Address
 * Azure Site-to-Site (S2S) VPN
 * Azure Traffic Manager
 
### Azure Stack Resources
 * Azure Stack App Service
 * Azure Stack Virtual Network
   * Application Subnet
   * Gateway Subnet
 * Azure Stack Local Network Gateway
 * Azure Stack Virtual Network Gateway 
 * Azure Stack Public IP Address
 * Azure Stack Site-to-Site (S2S) VPN
 
# Implementation

## Create Azure Stack Resources

## Create Azure Resources
Goto [Deployment/Azure](/Deployment/Azure/) and click on "Deploy to Azure" to deploy the required resources to your Azure Subscription.


