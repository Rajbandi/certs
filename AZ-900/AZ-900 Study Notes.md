**Azure architecture and services**

1.  **Core components**


1.  **Geographies, Regions, DataCenters**

    1.  Microsoft has created boundaries called **geographies**. A geography boundary is oftentimes the border of a country. All the country data regulations are applied in geography.

    2.  Geographies help organizations comply with regulatory requirements by ensuring that data stays within certain physical boundaries.

    3.  An Azure Region is a specific geographic location within a geography that contains one or more data centers. Each region provides a range of Azure services and is designed to ensure high availability and resilience.

    4.  Region pairs are two Azure regions within the same geography that are strategically placed to provide disaster recovery and high availability. Each Azure region is paired with another region in the same geography, typically hundreds of miles apart. Ex: East US & West US, North Europe & West Europe

    5.  Region pairs help ensure data resiliency and availability in the event of a regional outage or disaster by providing automatic replication and failover between the paired regions.

    6.  Azure data centers are the physical facilities where the servers, storage, networking, and infrastructure necessary to run Azure services are housed within a region.

    7.  Data centers are the building blocks of Azure regions, providing the physical infrastructure needed to deliver cloud services

    8.  A data center houses thousands of servers and networking equipment. Multiple data centers make up an Azure region, and they are interconnected with high-speed networks.

    9.  Azure data centers feature robust security measures, including biometric scanning, 24/7 surveillance, and controlled access to protect the infrastructure.

    10. Data centers are part of a global network, interconnected with Microsoft's high-speed fiber-optic network, enabling seamless data transfer across the globe.

**Azure Government**

1.  Azure Government data centers are specialized Azure regions designed specifically to meet the stringent regulatory and compliance requirements of U.S. government agencies and their partners.

2.  These data centers provide cloud services that comply with government regulations, including FedRAMP, DoD, ITAR, and CJIS.

3.  Physically and logically isolated from the commercial Azure cloud

4.  Restricted to U.S. government and authorized users

5.  Hosting sensitive government data, defense projects

6.  Dedicated regions like US Gov Virginia, US Gov Texas

1.  **Availability Zones**

    1.  Azure Availability Zones are physically separate data centers within an Azure region.

    2.  Each zone is an independent location with its own power, cooling, and networking, designed to protect applications and data from data center failures

    3.  Availability Zones ensure high availability and resilience for applications and data by providing fault isolation within a region. They help protect against single points of failure by distributing resources across multiple zones within the same region

    4.  Each zone is located far enough from the others to minimize the risk of multiple zones being affected by a single disaster

    5.  Azure replicates data and resources across zones within a region, ensuring continuous availability and reducing the risk of data loss

    6.  **Virtual Machines**: You can deploy VMs across multiple Availability Zones to ensure that if one zone goes down, the others remain operational.

    7.  **Managed Disks**: Use zone-redundant disks to ensure high availability and data durability across zones.

    8.  **Load Balancers**: Distribute traffic across VMs in different zones for increased fault tolerance.

    9.  Availability zones aren’t available in all Azure regions, nor are they available for all Azure services in regions that support them

    10. There are at least **three availability zones** within each enabled region, and each availability zone has a water supply, cooling system, network, and power supply that is isolated from other zones.

    11. **Microsoft guarantees 99.99 percent uptime** for Azure virtual machines only if two or more VMs are deployed into two or more zones.

    12. There are two categories of services that support availability zones: **zonal services** and **zone-redundant services**.

    13. **Zonal services** are services such as virtual machines, managed disks used in a virtual machine, and public IP addresses used in virtual machines

    14. To achieve high availability, you must explicitly deploy **zonal services** into two or more zones.

    15. **Zone-redundant services** are services such as zone redundant storage and SQL databases.


2.  **Availability Sets**

    1.  Availability sets allow you to create two or more virtual machines in different physical server racks in an Azure datacenter

    2.  **Microsoft guarantees a 99.95 percen**t SLA with an availability sets.


3.  **Resource**

    1.  A resource in Azure is a manageable item that is available through the Azure platform.

    2.  Resources include services such as virtual machines (VMs), storage accounts, databases, web apps, and more.

    3.  Resources are the building blocks of your Azure environment.

    4.  Each resource has its own set of properties, settings, and configurations that can be managed individually through the Azure Portal, Azure CLI, PowerShell, or REST API

    5.  Types of Resources:

        -   **Compute**: Virtual Machines, App Services, Functions

        -   **Storage**: Blob Storage, Disk Storage, File Storage

        -   **Networking**: Virtual Networks, Load Balancers, VPN Gateways

        -   **Databases**: SQL Database, Cosmos DB, Azure Database for MySQL

        -   **Security**: Key Vault, Azure Firewall, Security Center

4.  **Resource Groups**

    1.  A resource group is a logical container that holds related Azure resources. It serves as an organizational unit that allows you to manage and group resources together.

    2.  Resource groups help you organize, manage, and deploy resources as a single entity. They simplify the management of resources by allowing you to apply common policies, access controls, and billing settings to all the resources within the group.

    3.  Resources in a resource group typically share a common lifecycle, allowing you to manage them collectively.

    4.  Monitor and manage costs by resource group, making it easier to track spending for specific projects or environments.

    5.  You can deploy, update, or delete all resources in a resource group together, using tools like Azure Resource Manager (ARM) templates.

    6.  Resources in a resource group can reside in different regions, but the resource group itself is located in a specific region to define where its metadata is stored.

    7.  You can apply role-based access control (RBAC) at the resource group level to manage permissions for all resources within the group.

    8.  If a lock is applied to a resource group, all resources within that group inherit the lock. However, locks at the resource level override resource group locks.

    9.  An Azure resource can only exist in one resource group

    10. Resources can be moved between resource groups and subscriptions, but some resources may not support this, and dependent resources must be moved together

    11. Deleting a resource group also deletes all resources within it; use locks to prevent accidental deletion.

    12. A resource group can contain up to 800 resources, and specific resources may have their own limits. Proper organization helps avoid reaching these limits.


5.  **Subscriptions**

    1.  An Azure subscription is a logical container used to provision and manage Azure resources, such as virtual machines, databases, and storage accounts.

    2.  It serves as the boundary for billing, resource organization, access control, and management within Azure.

    3.  Each subscription is associated with a globally unique identifier called a **subscription ID**. You can give each subscription a descriptive name to help you identify it, but Azure will always use the subscription ID to identify your subscription.

    4.  A subscription is the fundamental unit for billing in Azure. All resources within a subscription are billed together, and you receive a single invoice based on the usage of resources within that subscription.

    5.  You can track and manage costs at the subscription level, set budgets, and analyze spending using Azure Cost Management tools.

    6.  A subscription can contain multiple resource groups

    7.  The resources within a subscription can be deployed across multiple Azure regions, depending on the availability of services in those regions

    8.  Subscriptions allow you to manage access to resources using RBAC. You can assign users or groups specific roles at the subscription level, granting them permissions to manage resources within the subscription


    1.  **Types of Subscriptions:**

        -   **Pay-As-You-Go: You pay for the Azure services you use on a monthly basis, with no upfront commitment.**

        -   **Enterprise Agreement (EA): Suitable for large organizations, offering discounts based on committed usage and centralized billing.**

        -   **Azure Free Account: Offers limited free usage of certain Azure services for 12 months, along with some always-free services.**

        -   **MSDN, Visual Studio, and BizSpark Subscriptions: Offer Azure credits for developers and small businesses as part of Microsoft’s programs.**

    1.  Each subscription has limits on the number of resources. These limits can often be increased by requesting a quota increase. Microsoft support can increase limits in some scenarios if you have a good business justification. Some limits, however, cannot be increased.

6.  **Management Groups**

    1.  Organizational containers used to manage multiple subscriptions in a hierarchical structure, simplifying governance and compliance across large Azure environments

    2.  Management groups are arranged in a tree structure, allowing policies and access controls to be applied at different levels and inherited by child subscriptions.

    3.  Policies and RBAC can be applied at the management group level, ensuring consistent governance and security across all associated subscriptions.

    4.  Ideal for large organizations with complex structures, enabling efficient management and organization of Azure resources across multiple departments, regions, or projects.

    5.  By applying governance controls at the management group level, you ensure that all subscriptions under that group adhere to the same standards, reducing the risk of policy violations or inconsistent configurations.

    6.  Management groups simplify the process of auditing and reporting on compliance across the organization, as policies and controls are uniformly enforced.

    7.  You can create **nested management groups (up to six levels deep)** to reflect your organization's structure, such as departments, teams, or projects.

    8.  Permissions can be assigned at the management group level using RBAC. These permissions are inherited by all subscriptions, resource groups, and resources within the management group, streamlining access management across the organization.

    9.  You can assign Azure Policies and Azure Blueprints at the management group level, and these policies will automatically apply to all subscriptions and resources within that management group. This simplifies the enforcement of organizational standards across multiple subscriptions

    10. Management groups help ensure that all resources under them comply with corporate policies and regulatory requirements by applying consistent governance rules across all subscriptions.

    11.  limited to a total of 10,000 management groups

    12.  cannot have multiple parents for a single management group or subscription.

    13.  you can create multiple management groups, but even if you never create one, you still have one by default called the Tenant Root Group. This default management group is part of your Azure Active Directory tenant


**Compute**

Any cloud service that consumes resources such as CPU and memory is categorized as a compute service.

1.  **Virtual Machines**

    1.  A virtual machine (VM) is a software-based computer that runs on a physical computer. The physical computer is considered the host, and it provides the underlying physical components such as disk space, memory, CPU power, and so on.

    2.  The host computer runs software called a hypervisor that can create and manage one or more VMs, and those VMs are commonly referred to as guests.

    3.  The operating system on a guest doesn’t have to be the same operating system that the host is running.

    4.  The host computer is managed by Microsoft, but you manage the VM because this is an IaaS offering in Azure.

    <!-- -->

    1.  You are charged for Azure VMs as long as they are running

    2.  If you reserve the IP address for your VM, your IP address will likely change the next time you start it.

    3.  still incur charges for managed disks and other resources like reserved public address if any used by VM even when stopped.

    4.  VM is susceptible to downtime due to three types of events: planned maintenance, unplanned maintenance, and unexpected downtime.

    5.  Planned maintenance refers to planned updates that Microsoft makes to the host computer. This includes things like operating system updates, driver updates, and so on.

    6.  If monitor detects that a component within the host computer might fail soon, Azure will flag the computer for unplanned maintenance. In an unplanned maintenance event, Azure will attempt to move your VM to a healthy host computer.

    7.  **Availability sets** protect you from maintenance events and downtime caused by hardware failures.

    8.  Azure creates some underlying entities in an availability set called update domains and fault domains.

    9.  you must deploy at least two VMs into your availability set.

    10. **Fault domains** are a logical representation of the physical rack in which a host computer is installed. By default, **Azure assigns two fault domains to an availability set** to protect from unplanned maintenance events and unexpected downtime.

    11. **Update domain**s are designed to protect you from a situation where the host computer is being rebooted.

    12. When you create an availability set, **Azure creates five update domains by default**.

    13. Azure will only reboot computers in one update domain at a time and it will wait **30 minutes** for computers to recover from the reboot before it moves on to the next update domain.

    14. Update domains protect you from planned maintenance events

    15. First disadvantage is While you can use an ARM template to deploy multiple virtual machines in one deployment, you still must configure those machines with the software and configuration necessary to support your application

    16. The second disadvantage is you’ll need to configure a load balancer that will handle the job of routing users of your website to the VMs that are running it.

    17. The third disadvantage is cost


1.  **Container Instances**

    1.  Container instances refer to an application that runs in a Docker container runtime.

    2.  You can run a containerized application on a virtual machine. , but you can also use a service like Azure Container Instances (ACI) to run a containerized application on a VM that isn’t directly allocated to you

    3.  A container is created using a zipped version of an application called an image, and it includes everything the application needs to run, including the user-mode portions of the operating system. That might include a database engine, a web server, and so on.

    4.  The image can be deployed to any environment that supports the use of containers. Once there, the image is used to start a container the application runs in.

    5.  Each container typically operates within an isolated environment. It has its own network, its own storage, and so on.

    6.  You can use containers in Azure by installing a container runtime such as Docker on a VM and configuring everything yourself.

    7.  an easier option is to use Azure Container Instances (ACI) or Azure Kubernetes Service (AKS)

    8.  ACI allows you to run containers using images, which are pre-configured packages of software. You can use your own custom images or choose from Microsoft's provided sample images to get started quickly

    9.  You only pay for the memory and CPU your container uses, making it a simple and cost-effective option for running lightweight apps.

    10.  ACI do run on virtual machines (VMs) in the background, but the key difference is that you don’t have to manage or even see these VMs. Azure takes care of all the infrastructure management for you, allowing you to focus solely on your containerized applications

    11.  Unlike traditional VMs, where you pay for the entire VM even when it's idle, ACI charges you only for the CPU and memory your container uses while it’s running. You don’t need to handle updates, scaling, or maintenance of the VM.

    12.  Container is a lightweight alternative to managing full VMs directly

    13.  You can’t change the DNS Name Label after the instance is created. You also can’t change the image your instance uses.

1.  Networking

2.  Storage

3.  Identity

4.  Access

5.  Security

6.  Network Security

7.  IoT

**Azure management and governance**

1.  **Cost Management**

1.  **Factors Affecting cost**

    1.  Azure services are billed according to meters associated with a resource

    2.  These meters track how much a specific metric has been used by the resource.

    3.  Microsoft’s costs for operating Azure services differ by region, even when those regions are within the same geographic boundary. Your pricing will differ based on which Azure region you use

    4.  Many Azure resources do not charge for network traffic within the same region, but they will charge for traffic across regions.

    5.  You’re not charged for network traffic into an Azure datacenter, but you are charged for network traffic out of a datacenter. Your first **100 GB of outbound data** is free

1.  **Reducing cost**


1.  Each Azure service has a **pricing page** that outlines estimates on pricing for that resource based on typical usage.

2.  Microsoft will offer you a reduced rate if you agree to pay in advance using an **Enterprise Agreement (EA)**. Longer-term agreements offer even more price breaks.

3.  A **Cloud Solution Providers (CSPs)** might also provide you with complete solutions that are more cost-effective than

4.  purchasing all the resources yourself

5.  If you use VMs month over month, you can save substantially by using **Azure Reservations**. By committing to resource usage in advance and taking advantage of reserved instances, you no longer must pay the fees associated with pay-as-you-go pricing

6.  Reserved capacity allows you to save by purchasing a **one-year or three-year contrac**t, and you are then billed monthly at a reduced amount

7.  You can save even more on VMs and Azure SQL Database by taking advantage of hybrid use benefit. When you use **Azure Hybrid Benefit**, you bring your own license for Windows Server or SQL Server to Azure.

8.  By using **Azure Spot VMs**, you can take advantage of this unused capacity for huge savings.


1.  **Pricing Calculators**

    1.  Microsoft offers calculators that can help you get a handle on estimating your costs as you move to the cloud

    2.  **The Azure pricing calculator** can help you get an estimate of expenses based on the products you intend to use, as well as where those products will be deployed, and so on. Use when you need to estimate costs for new Azure deployments or compare different configurations. Ideal for planning and budgeting cloud projects.

    3.  The **Total Cost of Ownership (TCO)** calculator can help you forecast your savings by moving from on-premises to the cloud. Use when evaluating the financial benefits of migrating from on-premises infrastructure to Azure. Helps build a business case for cloud adoption.

    4.  **Azure Spot Pricing Calculator**: Use when running non-critical workloads that can tolerate interruptions. Ideal for batch processing, development environments, and short-term tasks.

    5.  **Azure Reservations Calculator**: Use when considering purchasing Azure Reserved Instances for stable workloads. Helps maximize cost savings over pay-as-you-go pricing.

    6.  The pricing calculator is helpful for estimating your expenses for new applications in Azure, but if you have on-premises applications you want to migrate to Azure and you want an estimate of how much you can save in Azure, the TCO calculator is a better choice


1.  **Azure Cost Management and Billing**

    1.  Azure regions are broken out into four separate groups for billing purposes. These groups are called **billing zones**, or more commonly, **zones**. Microsoft’s costs for network traffic out of each zone differ, so your costs will differ

    2.  **Azure Cost Management and Billing** is a tool in Azure that makes it easy to analyze your costs at a granular level.

    3.  **Cost Management and Billing** allows you to **create a budget** for your Azure expenses, set **configurable alerts** so you’ll know if you are approaching a budgeted limit, and analyze your costs in detail

1.  Tags

    1.  Tags make tracking expenses in Azure easy. A tag consists of a name and a value.

    2.  To view all your tags, choose All Services from the main menu in the portal and then search for Tags in the list of services.

    3.  They will be visible on your Azure invoice, making them an ideal method of categorizing and reporting on costs.

    4.  You can apply a tag to most Azure resources, including resource groups. It’s important to understand that by adding a tag to a resource group, you are not adding that tag to the resources within the resource group.

1.  **Governance and compliance**


1.  Governance tools like Azure Policy and Azure Blueprints are essential to control costs, enforce organizational policies, ensure compliance, and maintain consistency across your Azure environment. They automate the enforcement of rules and ensure that resources are created and managed according to your organization's standards, reducing the risk of errors, overspending, and non-compliance.

2.  Compliance refers to companies moving to the cloud are often concerned about keeping information private and compliant with regulations. Azure provides robust tools, certifications, and continuous monitoring to ensure that your data is private, secure, and compliant with industry regulations and global standards.

**Azure Blueprints**

1.  is a service that can make the process of deploying to the cloud easier

2.  allow you to configure an environment just as you need it to be, along with all the policies and other governance aspects in place

3.  configuration can then be saved so it can be duplicated at any time in other deployments

4.  Items that you add to a blueprint are called artifacts. An artifact can be a resource group, an ARM template, a policy assignment, or a role assignment

5.  saved in a management group can then be used by any subscription within that management group’s hierarchy

6.  are actual Azure resources and not simply files designed to define a deployment, Azure maintains a connection between the blueprint and the resources that use the blueprint

7.  it’s important to understand that blueprints aren’t a replacement for ARM templates. In fact, most blueprints make extensive use of ARM templates as artifacts.

**Azure Policy**

1.  allows you to define rules that are applied when Azure resources are created and managed

2.  Azure will take care of enforcing this policy so that you remain in accordance with your corporate policies,

3.  makes it easy to impose a full suite of policies by combining them into a group called an initiative

4.  you can also define your own policies by creating a custom policy definition**. Custom policy** definitions are ARM templates that define the policy

**Resource Locks**

1.  Is a solution that prevent changes to a resource or prevent that resource from being deleted.

2.  apply to everyone with access to the resource, regardless of which RBAC role they are assigned,

3.  to create a lock, you must either be in the **Owner or the User Access Administrator role** in RBAC

4.  an administrator can create a custom role that grants the right to create a lock

5.  Locks can be applied at the resource level, **the resource group level, or at the subscription level**

6.  If a lock is applied to a resource group, all resources in that resource group inherit the lock

7.  if a lock is applied at the subscription level, all resources in the subscription inherit the lock.

8.  Locks are also inherited by newly created resources. If you apply a delete lock to a resource group and add a new resource to the resource group later, the new resource will automatically inherit the delete lock

9.  A **read-only lock** is the most restrictive lock. It prevents changing properties of the resource or deleting the resource.

10. A **delete lock** prevents the resource from being deleted, but properties can still be changed.

11. Locks only apply to operations that are handled by Azure Resource Manager (ARM), and some operations specific to a resource are handled internally by the resource instead of being handled by ARM

12. Not all resource types will tell you that a lock prevented an operation that was attempted in the portal. There are times when you will see only a generic error message

**Service Trust Portal**

1.  allows you to define rules that are applied when Azure resources are created and managed

2.  is also where you’ll find links to Compliance Manager (a compliance tool for enterprises), the Security & Compliance Center with tools to aid in securing resources and maintaining compliancy, and numerous other resources related to governance, compliance, security, and privacy

3.  Microsoft has made all its information and tools on trust, security, and compliance in one convenient web portal called the Service Trust Portal

1.  **Managing and deploying Azure resources**

**Azure Portal**

1.  is a web-based interface provided by Microsoft that allows users to manage and configure their Azure resources and services.

**Azure PowerShell**

1.  provides a powerful way to manage your Azure environment through powershell scripts and automation, enhancing efficiency and productivity.

2.  Allow scripts to Create, update, and delete Azure resources such as virtual machines, storage accounts, and more

3.  Allow Script repetitive tasks like deploying resources, managing services, and configuring settings

4.  Available on **Windows, macOS, and Linux**, making it versatile for different environments.

**Azure Command Line(CLI)**

1.  command-line tool for managing Azure resources,

2.  is cross-platform and works on Windows, Linux, and macOS if you use the 2.0 version or later.

3.  Uses **Bash-like syntax**

**Azure Cloud Shell**

1.  A browser-based command-line interface available directly within the Azure Portal,

2.  Comes pre-configured with Azure CLI, Azure PowerShell, and popular development tools like Git, making it easy to manage and automate Azure resources

3.  Accessible from any device with a web browser, offering the flexibility to manage Azure resources from anywhere without needing to install local tools.

4.  Provides 5 GB of free persistent storage, allowing you to save scripts and files across sessions.

**Azure Arc**

1.  extends management and governance features of Azure to resources outside of Azure.

2.  using one of two different methods: Azure Arc-enabled servers or Azure Arc–enabled Kubernetes

3.   

Azure Arc-enabled servers

1.  Azure Arc-enabled servers can be Windows servers or Linux servers.

2.  Azure Arc-enabled servers allow you to extend Azure management features to your physical servers and virtual machines running outside of Azure.

3.  To use Azure Arc-enabled servers, you will need to install the Azure Connected Machine agent to the machine. This agent collects information about the server or VM and makes it available to Azure. It also installs some extensions from Azure onto your VMs that are used for VM management.

Azure Arc–enabled Kubernetes

1.  extends Azure management and governance features to your Kubernetes clusters running on-premises or in other cloud providers.

2.  works via the installation of an agent that you install. Once you’ve created your Kubernetes cluster outside of Azure, you can use the Azure CLI or PowerShell to begin the registration of your cluster with Azure Arc

3.  uses a feature of the Git source control system called GitOps to deploy and manage Arc-enabled Kubernetes clusters.

4.  Azure application services allow you to run apps on several Azure services on Arc-enabled Kubernetes, including Azure App Service, Azure Functions, Azure Logic Apps, Azure Event Grid, and Azure API Management.

5.  Arc-enabled data services make it possible to run Azure SQL Managed Instance or PostgreSQL Hyperscale services on your Kubernetes clusters outside of Azure

**Azure Resource Manager (ARM) and ARM Templates**

1.  ARM is a service that runs in Azure, and it’s responsible for all interactions with Azure services.

2.  ARM uses JSON templates in a declarative syntax. Each resource is accompanied by properties such as the name of the resource and properties that are specific to that resource

3.  ARM authenticates you to ensure you have the right access to create that resource, and then it talks to a resource provider for the service you’re creating.

4.  All management tools for Azure use ARM on the back end. That includes the Azure portal, Azure PowerShell, and the Azure CLI.

5.  Management tools interact with ARM using the ARM application programming interface (API).

1.  **Monitoring**

**Azure Monitor**

1.  is a monitoring platform that includes powerful tools like Application Insights and Log Analytics to help monitor web apps and VMs.

2.  Collects, analyzes, and acts on telemetry from cloud and on-premises environments.

3.  Key features: Alerts, metrics, log analytics

4.  alerts make it easy to react appropriately to metrics

 **Azure Advisor**

1.  A personalized cloud consultant that offer advice about high availability, security, performance, and cost.

2.  provides analysis and recommendations for cost, security, reliability, operational excellence, and performance of your Azure resources.

3.  **Cost**: Advises on ways to reduce your Azure spending, such as resizing or shutting down underutilized resources.

4.  **Security**: Suggests improvements to enhance the security of your Azure resources, like enabling encryption or addressing potential vulnerabilities.

5.  **Performance**: Recommends actions to improve the performance of your applications, such as upgrading to higher-performance resources or optimizing configurations.

6.  **Reliability**: Offers guidance on improving the availability and resilience of your resources, like setting up redundancy or configuring backup solutions.

7.  **Operational**: Suggests best practices for managing and monitoring your Azure environment, including setting up alerts or automating tasks.

**Azure Service Health**

1.  shows you all current and historic incidents in Azure that impacted your resources.

2.  **Service Issues**: Notifications about outages.

3.  **Planned Maintenance**: Alerts about upcoming maintenance.

4.  **Health History**: Records of past incidents.

**Azure Advisor vs. Azure Monitor vs. Azure Service Health**

-   **Azure Advisor**:

    -   Provides best practice recommendations for cost, security, performance, and reliability.

    -   Uses data from Azure Monitor for performance recommendations.

-   **Azure Monitor**:

    -   Monitors performance and availability of applications and resources.

    -   Collects metrics, logs, and alerts.

-   **Azure Service Health**:

    -   Reports on Azure service issues, outages, and maintenance that affect your resources.

    -   Focuses on the health of the Azure platform itself rather than individual resources.

